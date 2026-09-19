# Documento de Especificación de Proyecto de Software (SRS) y Plan de Arquitectura MVP

## Plataforma B2B de Economía Circular y Logística Inversa para el Corredor Agroindustrial del Sur de Jalisco

**Versión:** 1.0 (MVP)
**Fecha:** Septiembre 2026
**Ubicación de Operaciones:** Ciudad Guzmán, Jalisco, México.
**Audiencia:** Equipo de Ingeniería, Inversionistas Semilla, Dirección de Operaciones (Empacadoras y Recicladoras).

## 1. RESUMEN EJECUTIVO Y MODELO DE NEGOCIO MVP
### 1.1 Propuesta de Valor
La plataforma resuelve la ineficiencia logística y de cumplimiento normativo en la gestión de residuos agroindustriales del Sur de Jalisco. Mediante un modelo B2B, monetiza los subproductos de las empacadoras conectándolas con recicladores en el Bajío/ZMG, utilizando fletes de retorno (back-hauling) a costo marginal y automatizando la emisión de manifiestos exigidos por SEMADET, garantizando la trazabilidad y la liquidación financiera en esquema _escrow_.
### 1.2 Definición de Actores del Sistema
- **Generadores (Lado de Oferta):** Empacadoras agroindustriales piloto (aguacate y berries) ubicadas en el corredor Ciudad Guzmán - Zapotiltic - Tuxpan.
- **Transportistas (Logística):** Operadores de carga con registro SEMADET vigente, que viajan vacíos en sus rutas de retorno hacia la Zona Metropolitana de Guadalajara (ZMG) o el puerto de Manzanillo.
- **Compradores/Recicladores (Lado de Demanda):** 2-3 centros de acopio y transformación autorizados en ZMG/Bajío.

### 1.3 Catálogo Estricto de Materiales (MVP)
Para estandarizar el cubicaje y mitigar riesgos de rechazo comercial, el MVP soporta exclusivamente: 
1. **Cartón Corrugado (OCC):** Embalaje de desecho. _Criterio de rechazo:_ Humedad > 12%, contaminación por materia orgánica (fruta aplastada).    
2. **Tarimas de Madera:** Rotas o de un solo uso. _Criterio de rechazo:_ Contaminación por agroquímicos o plagas activas.    
3. **Plásticos HDPE y LDPE:** Cajas cosecheras mermadas, plásticos de acolchado e invernadero. _Criterio de rechazo:_ Tierra excesiva (>5% en peso), sin pre-lavado en LDPE.

## 2. ESPECIFICACIÓN DE REQUERIMIENTOS FUNCIONALES (FR) Y CASOS DE USO

| **ID**    | **Módulo**    | **Requerimiento / Caso de Uso**                                                                                                    | **Criterio de Aceptación**                                                                                                                             |
| --------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **FR-01** | Generador     | **Publicación de Lote:** El generador publica un lote indicando tipo de material, cubicaje/peso estimado y fotos de evidencia.     | El sistema valida campos obligatorios y analiza metadata de fotos (fecha/hora) para evitar fraudes. Estado cambia a `OPEN_BID`.                        |
| **FR-02** | Transportista | **Matchmaking de Retornos:** El sistema filtra y notifica a transportistas geolocalizados cerca de Cd. Guzmán con rutas hacia ZMG. | El transportista visualiza lotes compatibles con su capacidad de carga volumétrica y acepta el viaje (`RIDE_ACCEPTED`).                                |
| **FR-03** | Compliance    | **El "Hook" SEMADET:** Validación de transportista y generación de Manifiesto Electrónico.                                         | El sistema impide cargar si el transportista no tiene RFC y número de registro SEMADET activo. Auto-genera layout PDF oficial del manifiesto de carga. |
| **FR-04** | Transaccional | **Bloqueo en Escrow:** Al acordar la compra, el Comprador deposita los fondos, los cuales quedan retenidos.                        | La pasarela confirma el cobro; el sistema cambia el estado del lote a `FUNDS_SECURED`.                                                                 |
| **FR-05** | Transaccional | **Liquidación:** Liberación de fondos tras confirmación de peso en báscula de destino y firma digital.                             | El receptor sube ticket de báscula. El pago se divide automáticamente (Transportista + Generador - Comisión) y se ejecuta el payout.                   |

## 3. REQUERIMIENTOS NO FUNCIONALES (NFR) Y SEGURIDAD

- **NFR-01 (Arquitectura):** El sistema operará bajo un patrón de [[Monolito Modular]]. Prohibida la fragmentación temprana en microservicios debido a la baja transaccionalidad inicial esperada (estimado: 50-100 viajes/semana en MVP). Prioridad: Mantenibilidad y bajo costo de nube.
- **NFR-02 (Disponibilidad y Concurrencia):** [[SLA]] del 99.9% para la base de datos core. Tolerancia a latencia en submódulos de conciliación de pagos y scraping de SEMADET (operaciones asíncronas
- **NFR-03 (Seguridad y RBAC):** Control de acceso estricto. Roles: `ADMIN`, `GENERATOR`, `BUYER`, `CARRIER`. JWT con expiración corta (15 min) y refresh tokens.
- **NFR-04 (Almacenamiento Legal):** Buckets S3 (AWS/GCP) con encriptación en reposo (AES-256) y políticas de retención inmutables (WORM) por 5 años para documentos fiscales (CFDI 4.0), tickets de báscula y Manifiestos SEMADET (cumplimiento Código Fiscal de la Federación y Ley de Residuos de Jalisco).
## 4. ARQUITECTURA DE SOFTWARE Y STACK TECNOLÓGICO

### 4.1 Justificación del Stack Tecnológico
Para minimizar el "time-to-market" (8 semanas) y maximizar la predictibilidad, se usará un stack maduro, tipado y basado en un monolito modular:
- **Backend:** Node.js con **NestJS** (TypeScript). Provee inyección de dependencias y modularidad nativa.
- **Frontend:** **React.js** (Next.js) con TailwindCSS. PWA (Progressive Web App) requerida para que los transportistas y operarios de montacargas/báscula suban fotos sin instalar apps nativas.
- **Base de Datos:** **PostgreSQL** (Relacional). Indispensable para asegurar la integridad transaccional (ACID) de operaciones financieras (Escrow) y manejo espacial básico (PostGIS para radios de carga Cd. Guzmán-ZMG).
- **Almacenamiento:** Amazon S3 o [Cloudflare R2](https://www.cloudflare.com/products/r2/) (menor costo de egress) para imágenes y PDFs.
- **Infraestructura:** Despliegue en PaaS (Render, Heroku o AWS AppRunner) para anular costos de DevOps durante el MVP.
### 4.2 Esquema Preliminar de Base de Datos (Entidad-Relación)

- `Users`: id, company_id, role, email, password_hash, status.    
- `Companies`: id, type (GENERATOR, BUYER, CARRIER), legal_name, rfc, semadet_registry_id, address, geo_location.
- `Listings`: id, generator_id, material_type, estimated_weight, estimated_volume, pickup_date, status (OPEN, PENDING_TRANSIT, IN_TRANSIT, DELIVERED, CLOSED).
- `Bids_Orders`: id, listing_id, buyer_id, agreed_price_per_ton, status.
- `Shipments`: id, listing_id, carrier_id, driver_name, truck_plates, current_status, final_weight_ticket_url.
- `Manifests`: id, shipment_id, semadet_folio, document_url, issued_at, signed_by_generator, signed_by_receiver.
- `Escrow_Transactions`: id, order_id, stripe_pi_id, total_amount, carrier_fee, platform_fee, status (HELD, RELEASED, REFUNDED).

### 4.3 Diseño de API RESTful (Endpoints Principales)

``` 
POST   /api/v1/listings           # Generador publica material.
GET    /api/v1/listings/geo       # Transportista consulta cargas en Cd. Guzmán/Zapotiltic.
POST   /api/v1/orders             # Comprador crea orden e inicia Escrow.
POST   /api/v1/shipments/accept   # Transportista hace claim del viaje.
POST   /api/v1/manifests/generate # El "Hook". Crea el layout PDF oficial y lo firma.
PUT    /api/v1/shipments/deliver  # Báscula ZMG confirma peso final. Dispara webhook de pagos.
```

## 5. DIAGRAMAS DE FLUJO Y SECUENCIA (End-to-End)
El siguiente diagrama detalla la orquestación entre los actores físicos y los subsistemas digitales (Pagos y Gobierno).
Fragmento de código

```
sequenceDiagram
    autonumber
    participant G as Generador (Empacadora)
    participant P as Plataforma B2B
    participant C as Comprador (Reciclador)
    participant F as Pasarela (Stripe/STP)
    participant T as Transportista
    participant S as SEMADET_Sys
    
    G->>P: Publica lote (OCC, 5 Tons)
    P-->>C: Notificación de material disponible
    C->>P: Acepta lote y emite orden de compra
    P->>F: Intención de pago (Hold / Escrow)
    F-->>P: Fondos bloqueados (FUNDS_SECURED)
    P->>T: Matchmaking: Alerta a transportistas en retorno
    T->>P: Acepta flete
    P->>S: Valida registro SEMADET del transportista
    S-->>P: Registro Válido
    P->>P: Auto-genera Manifiesto Electrónico (PDF)
    P-->>G: Manifiesto listo para despacho
    G->>T: Carga camión y firma salida
    T->>C: Tránsito hacia ZMG / Entrega en planta
    C->>P: Confirma recepción, sube ticket de báscula (Ej: 4.8 Tons)
    P->>P: Recálculo de montos finales (Ajuste por peso real)
    P->>F: Instrucción de Payout (Split Payment)
    F-->>P: Fondos transferidos (G, T, y Fee Plataforma)
    P->>P: Cierra Manifiesto (Firma destino)
    P-->>G: CFDI y Manifiesto Final en Bóveda Legal
```

## 6. ESTRATEGIA DE INTEGRACIÓN Y BARRERAS TÉCNICAS

### 6.1 Contingencia Compliance: Integración SEMADET Jalisco
**El Problema:** Actualmente, la ventanilla estatal de SEMADET y los sistemas de Manifiestos de la Ley de Gestión Integral de los Residuos del Estado no cuentan con una API pública abierta para interoperabilidad B2B pura.

**Solución Arquitectónica (Estrategia Semi-automatizada):
1. **Generación Determinística de Layouts:** El sistema utilizará librerías de generación de PDFs (ej. `PDFKit` o renderizado HTML-to-PDF) para recrear _exactamente_ el formato de manifiesto exigido por la norma estatal.
2. **RPA / Scraping Asistido (Fase 2):** Se implementará un worker asíncrono utilizando `Puppeteer` o `Playwright` (headless browser) que tome los datos estructurados de nuestra DB e inicie sesión en el portal estatal con las credenciales delegadas del generador, llenando el formulario web oficial. Si hay un Captcha o cambio de layout gubernamental, el sistema recurrirá a un _fallback_ manual donde el Generador simplemente imprime y firma el PDF autogenerado por la plataforma.

### 6.2 Arquitectura del Flujo de Pagos (Escrow y Fiscalidad MX)
**El Problema:** La plataforma maneja dinero de terceros, lo que requiere estricto control de prevención de lavado de dinero (PLD) y cumplimiento del SAT (Retenciones de IVA para autotransporte).
**Solución Técnica:
- Se descarta la retención manual en cuentas bancarias convencionales para evitar que la plataforma acumule ingresos no propios.
- **Integración:** Uso de **Stripe Connect Custom Accounts** o una API SPEI directa vía **STP (Sistema de Transferencias y Pagos)** mediante cuentas concentradoras y sub-cuentas virtuales (CLABEs dinámicas).
- **Flujo Fiscal:** El Comprador fondea una cuenta virtual. Al entregarse la mercancía, la plataforma calcula el pago del flete (aplicando por ley el -4% de retención de IVA al transportista, conforme a normatividad mexicana) y el remanente por el material al Generador. La plataforma factura únicamente su comisión transaccional (SaaS fee / Brokerage fee).

## 7. ROADMAP DE IMPLEMENTACIÓN DEL MVP (Plan de 10 Semanas)
Este esquema se basa en sprints de 2 semanas, orientados a un equipo pequeño y altamente productivo (1 Backend, 1 Frontend, 1 Tech Lead/PM).
- **Sprint 1: Infraestructura y Data Core (Semanas 1-2)
    - Setup de AWS/GCP, repositorios, CI/CD.
    - Implementación de modelos de base de datos (PostgreSQL).
    - Auth, RBAC (Generador, Transportista, Comprador).
- **Sprint 2: El Mercado - "Offer & Discovery" (Semanas 3-4)
    - Endpoints y UI del Generador para publicación de Lotes.
    - Lógica de validación de materiales (Catálogo estricto).
    - UI del Comprador para explorar lotes y lanzar ofertas.
- **Sprint 3: Logística y Matchmaking (Semanas 5-6)
    - Módulo de transportistas (PWA móvil para conductores).
    - Lógica de Matchmaking basada en geo-cercas (Polígonos limitados a Cd. Guzmán / ZMG).
    - Aceptación de viajes y cambio de estados logísticos (`IN_TRANSIT`).
- **Sprint 4: Escrow Financiero y Compliance SEMADET (Semanas 7-8)
    - Integración de pasarela de pagos (Bloqueo y liberación).
    - Desarrollo de motor de generación de Manifiestos PDF (El "Hook").
    - Cálculos matemáticos de liquidación tras confirmación de báscula.
- **Sprint 5: Pruebas de Campo y "Go-Live" Piloto (Semanas 9-10)
    - Despliegue a producción.
    - _Shadowing_ de operaciones: 2 transacciones piloto en físico con 1 empacadora de aguacate en Cd. Guzmán y 1 reciclador en ZMG.
    - Corrección de fricciones UI/UX con choferes de montacargas y transportistas en los patios de carga.