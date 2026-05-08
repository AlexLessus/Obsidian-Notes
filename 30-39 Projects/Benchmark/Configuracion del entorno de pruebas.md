## Requerimientos de Software y Herramientas

### Sistema Operativo y Controladores
- **SO:** Linux (Recomendado Ubuntu 22.04 LTS o superior) para un control más preciso de los procesos. Si usas Windows, utiliza **WSL2** con soporte para GPU.
- **Driver NVIDIA:** Versión estable más reciente (535+ recomendado).    
- **CUDA Toolkit:** Versión 12.x instalada para asegurar la compatibilidad con Ollama y `pynvml`.

### Entorno de Ejecución (Ollama)
- **Instalación:** Ejecuta `curl -fsSL [https://ollama.com/install.sh](https://ollama.com/install.sh) | sh`.    
- **Servicio:** Debes saber cómo detener e iniciar el servicio manualmente para limpiar la memoria entre pruebas:    
    - `sudo systemctl stop ollama`        
    - `ollama serve` (en una terminal dedicada para ver logs en tiempo real).

### Entorno Python
``` bash
# Crear entorno virtual en tu carpeta del proyecto  
mkdir ~/benchmark-praxintesis && cd ~/benchmark-praxintesis  
python3 -m venv .venv  
source .venv/bin/activate  
  
# Instalar librerías  
pip install psutil pynvml pandas matplotlib requests

# Para métricas de energía (RAPL — exclusivo de Linux):
sudo apt install linux-tools-common linux-tools-generic -y  

# Verificar acceso a RAPL  
ls /sys/class/powercap/intel-rapl/
```

**Librerías críticas (Instalar vía pip):**
- `requests`: Para interactuar con la API de Ollama (puerto 11434).    
- `psutil`: Monitoreo de CPU y RAM del sistema.    
- `pynvml`: Monitoreo directo de la NVIDIA GTX 1050 (VRAM y temperatura).    
- `pandas`: Para la estructuración y exportación de resultados a CSV.    
- `tqdm`: Para barras de progreso en el benchmark.



### Herramientas de monitoreo
``` bash
# Temperatura de CPU y GPU  
sudo apt install lm-sensors -y  
sudo sensors-detect --auto  
sensors # Verificar que aparece la GPU y el CPU  
  
# Monitor visual en tiempo real (opcional pero útil)  
sudo apt install nvtop htop -y  
nvtop # GPU en tiempo real  
htop # CPU/RAM en tiempo real
```

