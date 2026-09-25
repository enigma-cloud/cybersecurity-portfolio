# DNS and ICMP Traffic Analysis

## Overview
A cybersecurity incident report analyzing DNS and ICMP network traffic captured with `tcpdump`. This was my first hands-on activity in the Google Cybersecurity Professional Certificate.

## Scenario
A consulting company's clients could not access `www.yummyrecipesforme.com` and received a "destination port unreachable" error. As a security analyst, I analyzed a network traffic capture to identify which protocol and service were affected.

## What I Did
- Analyzed a DNS and ICMP traffic log captured with `tcpdump`.
- Identified that the computer sent DNS queries over **UDP to port 53** to resolve the website's IP address.
- Instead of a DNS response, the host received **ICMP "udp port 53 unreachable"** messages.
- Concluded that the DNS service was unreachable, preventing domain name resolution and access to the website.

## Tools Used
- `tcpdump` (network traffic analysis)
- DNS and ICMP traffic log

## Key Takeaway
The incident involved **UDP port 53 (DNS)** being unreachable. The root cause was a problem with the DNS service or communication to it, which prevented the domain from resolving. The recommended next step was to verify the DNS service was running and that port 53 could receive and respond to requests.

## Skills Demonstrated
- Network traffic analysis
- Understanding of TCP/IP protocols (DNS, UDP, ICMP)
- Incident analysis and reporting

---

# Análisis de Tráfico DNS e ICMP

## Resumen
Informe de incidente de ciberseguridad que analiza el tráfico de red DNS e ICMP capturado con `tcpdump`. Fue mi primera actividad práctica en el Certificado de Ciberseguridad de Google.

## Escenario
Los clientes de una empresa de consultoría no podían acceder a `www.yummyrecipesforme.com` y recibían un error de "puerto de destino inalcanzable". Como analista de seguridad, analicé una captura de tráfico de red para identificar qué protocolo y servicio estaban afectados.

## Qué hice
- Analicé un registro de tráfico DNS e ICMP capturado con `tcpdump`.
- Identifiqué que la computadora enviaba consultas DNS sobre **UDP al puerto 53** para resolver la dirección IP del sitio web.
- En lugar de una respuesta DNS, el host recibió mensajes **ICMP "puerto udp 53 inalcanzable"**.
- Concluí que el servicio DNS estaba inalcanzable, impidiendo la resolución del dominio y el acceso al sitio web.

## Herramientas utilizadas
- `tcpdump` (análisis de tráfico de red)
- Registro de tráfico DNS e ICMP

## Conclusión clave
El incidente involucró el **puerto UDP 53 (DNS)** inalcanzable. La causa raíz fue un problema con el servicio DNS o la comunicación hacia él, lo que impidió resolver el dominio. El siguiente paso recomendado fue verificar que el servicio DNS estuviera funcionando y que el puerto 53 pudiera recibir y responder solicitudes.

## Habilidades demostradas
- Análisis de tráfico de red
- Comprensión de protocolos TCP/IP (DNS, UDP, ICMP)
- Análisis de incidentes y elaboración de informes
