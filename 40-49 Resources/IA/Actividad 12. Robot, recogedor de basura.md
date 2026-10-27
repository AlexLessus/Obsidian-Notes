Alexis De Jesus Perez Carmona

Para probarlo es necesario instalar pygame
``` 
pip install pygame
```

Las dos versiones están en el mismo Código, para cambiarla hay que presionar la tecla `M`
![[Pasted image 20261006230858.png]]
![[Pasted image 20261006230747.png]]

![[Pasted image 20261006230800.png]]


![[Pasted image 20261006230819.png]]
``` python
import pygame
import math
import random
import sys
from enum import Enum

# --- CONFIGURACIONES GLOBALES ---
FPS = 60
WIDTH, HEIGHT = 1000, 700
SIM_WIDTH = 750  # Área de simulación (deja 250px para el HUD)
SIM_HEIGHT = 700

# Paleta de Colores
BG_COLOR = (30, 30, 40)
HUD_COLOR = (45, 45, 55)
ROBOT_COLOR = (255, 200, 0)
DEPOT_COLOR = (50, 150, 255)
STATION_COLOR = (50, 200, 50)
DOOR_COLOR = (200, 50, 200)
TEXT_COLOR = (220, 220, 220)

# --- 1. DEFINICIÓN DE LA MÁQUINA DE ESTADOS (FSM) ---
class FSMState(Enum):
    BUSQUEDA = 1        # Estado 1: Buscar objetos en la habitación
    NUEVA_BUSQUEDA = 2  # Estado 2: Evaluar si hay más objetos tras depositar
    IR_A_BATERIA = 3    # Estado 3: Navegar a la estación de carga por baja batería
    RECARGAR = 4        # Estado 4: Recuperando energía
    MUERTO = 5          # Estado 5: Batería a 0, inoperativo
    ALEATORIO = 6       # Estado 6: Vagar (Modo 1) o Ir a Puerta (Modo 2)

# --- 2. CLASES DEL ENTORNO (OOP) ---

class Basura:
    def __init__(self, x, y):
        self.x = x
        self.y = y
        self.peso = round(random.uniform(1.0, 5.0), 1)
        self.radio = int(5 + self.peso * 2) # Más peso = más grande
        
        # Color varía de gris claro (ligero) a marrón oscuro (pesado)
        c_val = int(200 - (self.peso * 30))
        self.color = (c_val, c_val - 20, c_val - 40)
        
    def draw(self, surface):
        pygame.draw.circle(surface, self.color, (int(self.x), int(self.y)), self.radio)
        pygame.draw.circle(surface, (0, 0, 0), (int(self.x), int(self.y)), self.radio, 1)

class EstacionRecarga:
    def __init__(self):
        self.rect = pygame.Rect(20, 20, 60, 60)
        self.centro = (self.rect.centerx, self.rect.centery)
        
    def draw(self, surface):
        pygame.draw.rect(surface, STATION_COLOR, self.rect)
        pygame.draw.rect(surface, (255, 255, 255), self.rect, 2)
        # Ícono de rayo simplificado
        pygame.draw.polygon(surface, (255, 255, 0), [(45, 30), (35, 50), (55, 50), (45, 70)])

class DepositoBasura:
    def __init__(self):
        self.rect = pygame.Rect(SIM_WIDTH - 80, 20, 60, 60)
        self.centro = (self.rect.centerx, self.rect.centery)
        
    def draw(self, surface):
        pygame.draw.rect(surface, DEPOT_COLOR, self.rect)
        pygame.draw.rect(surface, (255, 255, 255), self.rect, 2)

class Puerta:
    def __init__(self):
        # Puerta al sur, en medio de la habitación
        self.rect = pygame.Rect(SIM_WIDTH // 2 - 40, SIM_HEIGHT - 30, 80, 30)
        self.centro = (self.rect.centerx, self.rect.centery)
        
    def draw(self, surface):
        pygame.draw.rect(surface, DOOR_COLOR, self.rect)

class Habitacion:
    def __init__(self):
        self.numero = 1
        self.basuras = []
        self.estacion = EstacionRecarga()
        self.deposito = DepositoBasura()
        self.puerta = Puerta()
        self.generar_basura()
        self.basura_total_recogida = 0

    def generar_basura(self):
        self.basuras.clear()
        cantidad = random.randint(10, 15)
        for _ in range(cantidad):
            # Evitar que aparezcan sobre las bases
            x = random.randint(100, SIM_WIDTH - 100)
            y = random.randint(100, SIM_HEIGHT - 100)
            self.basuras.append(Basura(x, y))

    def draw(self, surface):
        self.estacion.draw(surface)
        self.deposito.draw(surface)
        self.puerta.draw(surface)
        for b in self.basuras:
            b.draw(surface)

# --- 3. EL AGENTE AUTÓNOMO (ROBOT) ---

class Robot:
    def __init__(self, habitacion):
        self.x = SIM_WIDTH // 2
        self.y = SIM_HEIGHT // 2
        self.radio = 15
        self.velocidad = 3.0
        
        # Energía
        self.bateria_max = 1000.0
        self.bateria = self.bateria_max
        self.umbral_critico = 350.0
        
        # Entorno y Estado FSM
        self.habitacion = habitacion
        self.estado = FSMState.BUSQUEDA
        self.modo = 1  # 1: Original, 2: Extendido
        
        # Memoria de Trabajo (Variables Locales)
        self.rango_vision = 150.0
        self.carga_actual = None      # Objeto Basura que lleva cargando
        self.target_pos = None        # (x, y) Hacia dónde se dirige actualmente
        self.target_basura = None     # Referencia a la basura objetivo
        
    def cambiar_estado(self, nuevo_estado):
        """Gestiona la transición de la FSM de manera centralizada"""
        self.estado = nuevo_estado
        self.target_pos = None # Resetear el objetivo al cambiar de estado

    def actualizar(self):
        """Ciclo principal de actualización de IA basado en la tabla de transiciones"""
        
        # TRANSICIONES GLOBALES: Agotamiento de batería
        if self.bateria <= 0 and self.estado != FSMState.MUERTO:
            self.bateria = 0
            self.cambiar_estado(FSMState.MUERTO)
            return
            
        # EJECUCIÓN DE ESTADOS
        if self.estado == FSMState.BUSQUEDA:
            # Transición: 1 -> 3 (Batería crítica)
            if self.bateria < self.umbral_critico:
                self.cambiar_estado(FSMState.IR_A_BATERIA)
            else:
                self.comportamiento_busqueda()
                
        elif self.estado == FSMState.NUEVA_BUSQUEDA:
            # Transición instantánea: Evaluación
            if len(self.habitacion.basuras) > 0:
                self.cambiar_estado(FSMState.BUSQUEDA)  # 2 -> 1
            else:
                self.cambiar_estado(FSMState.ALEATORIO) # 2 -> 6
                
        elif self.estado == FSMState.IR_A_BATERIA:
            self.mover_hacia(self.habitacion.estacion.centro)
            # Transición: 3 -> 4 (Llegó a batería)
            if self.llegado(self.habitacion.estacion.centro):
                self.cambiar_estado(FSMState.RECARGAR)
                
        elif self.estado == FSMState.RECARGAR:
            # Comportamiento: Recuperar energía
            self.bateria += 5.0
            if self.bateria >= self.bateria_max:
                self.bateria = self.bateria_max
                # Transición: 4 -> 1 (Batería completa)
                self.cambiar_estado(FSMState.BUSQUEDA)
                
        elif self.estado == FSMState.ALEATORIO:
            if self.modo == 1:
                # MODO 1: Vagabundear hasta morir
                self.comportamiento_vagar()
            else:
                # MODO 2: Ir a puerta para cambiar habitación
                self.mover_hacia(self.habitacion.puerta.centro)
                if self.llegado(self.habitacion.puerta.centro):
                    self.cambiar_habitacion()
                    
        elif self.estado == FSMState.MUERTO:
            pass # No hace nada, terminal.

    # --- COMPORTAMIENTOS ESPECÍFICOS DE LOS ESTADOS ---

    def comportamiento_busqueda(self):
        """Lógica del Estado 1: Explorar, Detectar, Recoger, Depositar"""
        if self.carga_actual is None:
            # Fase A: Buscar objetos
            if self.target_basura is None or self.target_basura not in self.habitacion.basuras:
                # Escanear el área visual
                visibles = [b for b in self.habitacion.basuras if self.distancia_a(b.x, b.y) < self.rango_vision]
                if visibles:
                    # Seleccionar la basura más cercana
                    self.target_basura = min(visibles, key=lambda b: self.distancia_a(b.x, b.y))
                    self.target_pos = (self.target_basura.x, self.target_basura.y)
                else:
                    self.comportamiento_vagar() # Vagar si no ve nada
            else:
                # Acercarse a la basura vista
                self.mover_hacia(self.target_pos)
                if self.llegado(self.target_pos):
                    # Recoger objeto (Costo base + Factor peso)
                    costo_recogida = 5.0 + (self.target_basura.peso * 2.0)
                    self.bateria -= costo_recogida
                    self.carga_actual = self.target_basura
                    self.habitacion.basuras.remove(self.target_basura)
                    self.target_basura = None
                    self.target_pos = self.habitacion.deposito.centro
        else:
            # Fase B: Llevar al depósito
            self.mover_hacia(self.habitacion.deposito.centro)
            if self.llegado(self.habitacion.deposito.centro):
                # Depositar
                self.bateria -= 5.0  # Coste de dejar
                self.carga_actual = None
                self.habitacion.basura_total_recogida += 1
                # Transición: 1 -> 2 (Llegó a objeto y procesado)
                self.cambiar_estado(FSMState.NUEVA_BUSQUEDA)

    def comportamiento_vagar(self):
        """Movimiento aleatorio simulando exploración (sin objetivo fijo)"""
        if self.target_pos is None or self.llegado(self.target_pos):
            self.target_pos = (random.randint(50, SIM_WIDTH-50), random.randint(50, SIM_HEIGHT-50))
        self.mover_hacia(self.target_pos)

    def cambiar_habitacion(self):
        """Transición de habitación (Solo V2)"""
        coste_puerta = 100.0
        self.bateria -= coste_puerta
        if self.bateria > 0:
            self.habitacion.numero += 1
            self.habitacion.generar_basura()
            # Iniciar en la parte superior tras cruzar
            self.x, self.y = SIM_WIDTH // 2, 50 
            self.cambiar_estado(FSMState.BUSQUEDA)

    # --- MATEMÁTICAS VECTORIALES Y FÍSICAS ---

    def mover_hacia(self, pos):
        """Interpolación vectorial hacia objetivo y cálculo cinemático de coste de energía"""
        tx, ty = pos
        dx, dy = tx - self.x, ty - self.y
        dist = math.hypot(dx, dy)
        
        if dist > 0:
            # Normalizar vector
            nx, ny = dx / dist, dy / dist
            mov_x = nx * min(self.velocidad, dist)
            mov_y = ny * min(self.velocidad, dist)
            self.x += mov_x
            self.y += mov_y
            
            # Cálculo estricto de consumo energético por tick
            coste_movimiento = 0.5 # Costo base por frame en movimiento
            if self.carga_actual:
                coste_movimiento += (self.carga_actual.peso * 0.15) # Penalización de carga
                
            self.bateria -= coste_movimiento

    def llegado(self, pos):
        """Verifica colisión circular simple con el objetivo"""
        return self.distancia_a(pos[0], pos[1]) < self.radio

    def distancia_a(self, ox, oy):
        return math.hypot(ox - self.x, oy - self.y)

    # --- RENDERIZADO ---

    def draw(self, surface):
        # Dibujar rango de visión si está buscando
        if self.estado == FSMState.BUSQUEDA and not self.carga_actual:
            pygame.draw.circle(surface, (50, 50, 50), (int(self.x), int(self.y)), self.rango_vision, 1)

        # Color cambia si está muerto
        color = (100, 100, 100) if self.estado == FSMState.MUERTO else ROBOT_COLOR
        pygame.draw.circle(surface, color, (int(self.x), int(self.y)), self.radio)
        pygame.draw.circle(surface, (255, 255, 255), (int(self.x), int(self.y)), self.radio, 2)
        
        # Indicador de carga
        if self.carga_actual:
            pygame.draw.circle(surface, self.carga_actual.color, (int(self.x), int(self.y)), self.radio - 5)

        # Renderizar texto de estado FSM encima del robot
        font = pygame.font.SysFont(None, 20)
        lbl = font.render(f"S:{self.estado.value}", True, (255, 255, 255))
        surface.blit(lbl, (self.x - 10, self.y - 30))

# --- 4. MOTOR PRINCIPAL Y HUD ---

def main():
    pygame.init()
    screen = pygame.display.set_mode((WIDTH, HEIGHT))
    pygame.display.set_caption("Simulación FSM: Robot Autónomo")
    clock = pygame.time.Clock()
    font = pygame.font.SysFont(None, 26)
    small_font = pygame.font.SysFont(None, 22)

    habitacion = Habitacion()
    robot = Robot(habitacion)

    running = True
    while running:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_m:
                    # Intercambiar Modos al vuelo
                    robot.modo = 2 if robot.modo == 1 else 1

        # Lógica FSM
        robot.actualizar()

        # Renderizado del Entorno
        screen.fill(BG_COLOR)
        
        # Dibujar área de simulación (separador)
        pygame.draw.line(screen, (100, 100, 100), (SIM_WIDTH, 0), (SIM_WIDTH, HEIGHT), 2)

        habitacion.draw(screen)
        robot.draw(screen)

        # --- HUD LATERAL ---
        hud_x = SIM_WIDTH + 15
        
        tit = font.render("PANEL DE CONTROL", True, TEXT_COLOR)
        screen.blit(tit, (hud_x, 20))
        
        # Modo
        modo_txt = "Modo 1: Vagabundo" if robot.modo == 1 else "Modo 2: Explora Habitaciones"
        mod_lbl = small_font.render(modo_txt, True, (0, 255, 255))
        screen.blit(mod_lbl, (hud_x, 60))
        instrucc = small_font.render("(Presiona 'M' para alternar)", True, (150, 150, 150))
        screen.blit(instrucc, (hud_x, 80))

        # Estado FSM
        fsm_str = f"FSM: {robot.estado.name} ({robot.estado.value})"
        st_color = (255, 100, 100) if robot.estado == FSMState.MUERTO else (100, 255, 100)
        st_lbl = font.render(fsm_str, True, st_color)
        screen.blit(st_lbl, (hud_x, 130))

        # Batería
        bat_lbl = font.render(f"Batería: {int(robot.bateria)} / 1000", True, TEXT_COLOR)
        screen.blit(bat_lbl, (hud_x, 180))
        
        # Barra de progreso de batería
        bar_w = 200
        bar_h = 20
        bat_pct = max(0, robot.bateria / robot.bateria_max)
        bar_color = (0, 255, 0) if robot.bateria >= 350 else (255, 0, 0)
        pygame.draw.rect(screen, (50, 50, 50), (hud_x, 210, bar_w, bar_h))
        pygame.draw.rect(screen, bar_color, (hud_x, 210, int(bar_w * bat_pct), bar_h))

        # Estadísticas
        bas_lbl = font.render(f"Basura restante: {len(habitacion.basuras)}", True, TEXT_COLOR)
        screen.blit(bas_lbl, (hud_x, 260))
        
        rec_lbl = font.render(f"Total Recogido: {habitacion.basura_total_recogida}", True, TEXT_COLOR)
        screen.blit(rec_lbl, (hud_x, 290))
        
        if robot.modo == 2:
            hab_lbl = font.render(f"Habitación: #{habitacion.numero}", True, (255, 200, 200))
            screen.blit(hab_lbl, (hud_x, 340))

        pygame.display.flip()
        clock.tick(FPS)

    pygame.quit()
    sys.exit()

if __name__ == "__main__":
    main()
```