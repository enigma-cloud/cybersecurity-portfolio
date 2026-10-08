## Descripción

Análisis de un incidente de seguridad en el sitio web de una agencia de viajes. El servidor web recibió un gran volumen de solicitudes TCP SYN desde una dirección IP desconocida, lo que provocó que el servicio se saturara y dejara de responder (error de tiempo de espera de conexión).

## Tipo de ataque identificado

**Denegación de Servicio (DoS) — Ataque SYN Flood**

- El atacante envía una gran cantidad de solicitudes TCP SYN sin completar el proceso de conexión (handshake).
- El servidor queda desbordado manteniendo conexiones a medio abrir, agotando sus recursos.
- El sitio web deja de responder a los usuarios legítimos, generando errores de tiempo de espera.

## Impacto en la organización

- El sitio web de ventas quedó inaccesible para los empleados.
- Interrupción del servicio y pérdida de productividad.
- Daño potencial a la reputación de la empresa con los clientes.

## Medidas de mitigación

- Bloqueo temporal de la dirección IP del atacante en el firewall.
- Configuración de límites de conexiones SYN (SYN cookies) para proteger el servidor.
- Monitoreo continuo del tráfico de red para detectar patrones anómalos.

## Herramientas

- Detector de paquetes (Wireshark)
- Registro TCP/HTTP de Wireshark

## Contenido

- Informe sobre incidentes de ciberseguridad (análisis del ataque)
