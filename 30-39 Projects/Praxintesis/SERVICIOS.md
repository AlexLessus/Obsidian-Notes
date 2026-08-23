# Guía de Acceso a Servicios

Este documento detalla los servicios desplegados en el stack y cómo acceder a cada uno de ellos.

## Resumen de Accesos

| Servicio | URL / Punto de Acceso | Descripción |
| :--- | :--- | :--- |
| **n8n** | [https://n8n.praxintesis.dev](https://n8n.praxintesis.dev) | Plataforma principal de automatización de flujos de trabajo. |
| **Evolution API** | [https://api.praxintesis.dev](https://api.praxintesis.dev) | API de mensajería (WhatsApp) para integraciones. |
| **Ollama** | `http://ollama:11434` (interno) | Motor de modelos de lenguaje (LLM) para uso interno por n8n. |
| **Traefik** | Puertos 80/443 | Proxy inverso y gestión de certificados SSL. |

---

## Detalles de los Servicios

### 1. n8n
Es la herramienta central de automatización. 
- **Acceso:** Protegido por SSL a través de Traefik.
- **Configuración:** Utiliza el volumen `n8n_data` para persistir flujos y credenciales.

### 2. Evolution API
API diseñada para facilitar la integración con WhatsApp.
- **Documentación API:** Generalmente disponible en `${SERVER_URL}/docs`.
- **Seguridad:** Requiere la `API_KEY` definida en el archivo `.env` para la mayoría de las operaciones.
- **Dependencias:** Utiliza PostgreSQL (`evolution_db`) para datos y Redis (`evolution_redis`) para caché.

### 3. Ollama
Permite ejecutar modelos de IA localmente.
- **Uso:** En n8n, se configura apuntando al host `ollama` y al puerto `11434`.
- **Modelos:** Los modelos descargados se guardan en el volumen `ollama_data`.

### 4. Traefik
Gestiona el tráfico entrante y renueva automáticamente los certificados SSL de Let's Encrypt.
- **Email de SSL:** tu-praxintesis@gmail.com
- **Resolución ACME:** HTTP Challenge.

## Consideraciones de Red
Todos los servicios están conectados a la red interna de Docker `n8n-network`. Esto permite que se comuniquen entre sí utilizando sus nombres de servicio como hostnames (ej. `http://evolution_api:8080` o `http://ollama:11434`).
