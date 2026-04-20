Tags [[Redes]]
### **Métricas clave de desempeño de red**
Las siguientes métricas son fundamentales para analizar el comportamiento real de una red.

### **3.4.1.1 Latencia**
Es el **tiempo que tarda un paquete de datos en viajar desde el origen hasta el destino**. Suele medirse en: milisegundos (ms). Latencias altas generan retrasos perceptibles, especialmente en aplicaciones en tiempo real.

### **3.4.1.2 Jitter**
Es la **variación del retardo entre paquetes consecutivos**. Un jitter elevado provoca cortes, distorsión de audio o video entrecortado. Por ejemplo: **Voz robótica o congelamiento de imagen** en videollamadas.

### **3.4.1.3 Throughput**
Es la **cantidad real de datos que se transmiten correctamente por unidad de tiempo**, que suele medirse en: Mbps, Gbps. No es lo mismo que ancho de banda; el throughput es el **rendimiento efectivo**. Por ejemplo: **Velocidad real de descarga**.

### **3.4.1.4 Pérdida de paquetes**
Es el **porcentaje de paquetes que no llegan a su destino**. Una alta pérdida afecta gravemente aplicaciones sensibles al tiempo.

**Tabla resumen de métricas de desempeño**

|**Métrica**|**Qué mide**|**Herramientas comunes**|
|---|---|---|
|**Latencia**|Retardo de transmisión|ping, traceroute|
|**Jitter**|Variación del retardo|Wireshark, VoIP tools|
|**Throughput**|Rendimiento real|iperf, SNMP|
|**Pérdida de paquetes**|Paquetes no entregados|ping, Wireshark|

Una sola métrica no describe el desempeño completo de la red; **todas deben analizarse en conjunto**.

**Relación entre métricas y aplicaciones**

| **Aplicación**                | **Métrica crítica**       |
| ----------------------------- | ------------------------- |
| **Videollamadas**             | Latencia, jitter, pérdida |
| **Streaming**                 | Throughput, pérdida       |
| **Navegación web**            | Latencia                  |
| **Transferencia de archivos** | Throughput                |