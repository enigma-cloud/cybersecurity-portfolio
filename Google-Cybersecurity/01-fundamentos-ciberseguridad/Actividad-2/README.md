## Description

Analysis of a security incident on a travel agency's website. The web server received a large volume of TCP SYN requests from an unknown IP address, which caused the service to become saturated and stop responding (connection timeout error).

## Scenario

A security analyst receives an automated alert about a problem with the company's web server. When trying to visit the website, a connection timeout error appears. A packet sniffer reveals a large number of TCP SYN requests coming from an unknown IP address, overwhelming the server and preventing legitimate users from accessing the site.

## Type of attack identified

**Denial of Service (DoS) — SYN Flood Attack**

- The attacker sends a large number of TCP SYN requests without completing the connection process (handshake).
- The server becomes overwhelmed keeping half-open connections, exhausting its resources.
- The website stops responding to legitimate users, generating timeout errors.

## Key questions addressed

- Difference between Denial of Service (DoS) and Distributed Denial of Service (DDoS).
- Why the website took too long to load and reported a connection timeout error.
- Identification of attack patterns in the Wireshark TCP/HTTP log.

## Impact on the organization

- The sales website became inaccessible to employees.
- Service interruption and loss of productivity.
- Potential damage to the company's reputation with customers.

## Mitigation measures

- Temporary blocking of the attacker's IP address on the firewall.
- Configuration of SYN connection limits (SYN cookies) to protect the server.
- Continuous network traffic monitoring to detect anomalous patterns.

## Tools

- Packet sniffer (Wireshark)
- Wireshark TCP/HTTP log

## Contents

- Cybersecurity incident report (attack analysis)

---


## Descripción

Análisis de un incidente de seguridad en el sitio web de una agencia de viajes. El servidor web recibió un gran volumen de solicitudes TCP SYN desde una dirección IP desconocida, lo que provocó que el servicio se saturara y dejara de responder (error de tiempo de espera de conexión).

## Escenario

Un analista de seguridad recibe una alerta automatizada sobre un problema en el servidor web de la empresa. Al intentar visitar el sitio web, aparece un error de tiempo de espera de conexión. Un detector de paquetes revela un gran número de solicitudes TCP SYN provenientes de una dirección IP desconocida, saturando el servidor e impidiendo que los usuarios legítimos accedan al sitio.

## Tipo de ataque identificado

**Denegación de Servicio (DoS) — Ataque SYN Flood**

- El atacante envía una gran cantidad de solicitudes TCP SYN sin completar el proceso de conexión (handshake).
- El servidor queda desbordado manteniendo conexiones a medio abrir, agotando sus recursos.
- El sitio web deja de responder a los usuarios legítimos, generando errores de tiempo de espera.

## Preguntas clave abordadas

- Diferencia entre Denegación de Servicio (DoS) y Denegación de Servicio Distribuida (DDoS).
- Por qué el sitio web tardaba tanto en cargar e informaba un error de tiempo de espera de conexión.
- Identificación de patrones de ataque en el registro TCP/HTTP de Wireshark.

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
