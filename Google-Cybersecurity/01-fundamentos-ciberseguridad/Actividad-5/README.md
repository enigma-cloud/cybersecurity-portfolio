# Incident Report Analysis: NIST CSF

Activity on incident analysis using the NIST Cybersecurity Framework (CSF).

## Description

Analysis of a network incident using the NIST Cybersecurity Framework (CSF). The organization suffered a Distributed Denial of Service (DDoS) attack that compromised the internal network for two hours.

## Scenario

A media company providing web design, graphic design, and social media marketing services experienced a DDoS attack. The network services suddenly stopped responding due to an avalanche of incoming ICMP packets. The incident management team responded by blocking incoming ICMP packets, taking all non-critical network services offline, and restoring critical network services.

An investigation revealed that a malicious actor sent a flood of ICMP pings to the company's network through an unconfigured firewall. This vulnerability allowed the attacker to saturate the company's network with a DDoS attack.

## Type of attack

**Distributed Denial of Service (DDoS) — ICMP Flood**

- An avalanche of incoming ICMP packets saturated the network.
- Normal internal network traffic could not access any network resources.
- The vulnerability was caused by an unconfigured firewall.

## NIST CSF analysis

### Identify
- Conduct regular audits of internal networks, systems, devices, and access privileges to identify security gaps.

### Protect
- Apply policies, procedures, training, and tools to mitigate cybersecurity threats.
- Configure firewall rules to limit incoming ICMP packet rates.

### Detect
- Monitor network traffic for suspicious activity, such as incoming ICMP packets from untrusted IP addresses.
- Implement network monitoring software to detect anomalous traffic patterns.

### Respond
- Contain, neutralize, and analyze security incidents.
- Block incoming ICMP packets and isolate affected systems.

### Recover
- Restore normal operation of affected systems and recover data and assets.
- Improve recovery processes to better manage future incidents.

## Security measures implemented

- New firewall rule to limit the rate of incoming ICMP packets.
- Source IP address verification on the firewall to check for spoofed addresses.
- Network monitoring software to detect anomalous traffic patterns.
- IDS/IPS system to filter ICMP traffic based on suspicious characteristics.

## Tools

- NIST Cybersecurity Framework (CSF)
- Firewall configuration
- Network monitoring software
- IDS/IPS system

## Contents

- Incident report analysis (NIST CSF application)

---

# Análisis de Informe de Incidentes: NIST CSF

Actividad sobre análisis de incidentes utilizando el Marco de Ciberseguridad (CSF) del NIST.

## Descripción

Análisis de un incidente de red utilizando el Marco de Ciberseguridad (CSF) del NIST. La organización sufrió un ataque de Denegación de Servicio Distribuida (DDoS) que comprometió la red interna durante dos horas.

## Escenario

Una empresa multimedia que ofrece servicios de diseño web, diseño gráfico y soluciones de marketing en redes sociales experimentó un ataque DDoS. Los servicios de red dejaron de responder repentinamente debido a una avalancha de paquetes ICMP entrantes. El equipo de gestión de incidentes respondió bloqueando los paquetes ICMP entrantes, deteniendo los servicios de red no críticos y restableciendo los servicios críticos.

Una investigación reveló que un actor malicioso envió una avalancha de pings ICMP a la red de la empresa a través de un firewall no configurado. Esta vulnerabilidad permitió al atacante saturar la red con un ataque DDoS.

## Tipo de ataque

**Denegación de Servicio Distribuida (DDoS) — Inundación ICMP**

- Una avalancha de paquetes ICMP entrantes saturó la red.
- El tráfico normal de la red interna no pudo acceder a ningún recurso.
- La vulnerabilidad fue causada por un firewall no configurado.

## Análisis con el marco NIST CSF

### Identificar
- Realizar auditorías periódicas de redes internas, sistemas, dispositivos y privilegios de acceso para identificar brechas de seguridad.

### Proteger
- Aplicar políticas, procedimientos, capacitación y herramientas para mitigar amenazas de ciberseguridad.
- Configurar reglas de firewall para limitar la tasa de paquetes ICMP entrantes.

### Detectar
- Monitorear el tráfico de red para detectar actividad sospechosa, como paquetes ICMP entrantes de direcciones IP no confiables.
- Implementar software de monitoreo de red para detectar patrones de tráfico anómalos.

### Responder
- Contener, neutralizar y analizar incidentes de seguridad.
- Bloquear paquetes ICMP entrantes y aislar los sistemas afectados.

### Recuperar
- Restaurar el funcionamiento normal de los sistemas afectados y recuperar datos y activos.
- Mejorar los procesos de recuperación para gestionar mejor futuros incidentes.

## Medidas de seguridad implementadas

- Nueva regla de firewall para limitar la tasa de paquetes ICMP entrantes.
- Verificación de la dirección IP de origen en el firewall para detectar direcciones falsas.
- Software de monitoreo de red para detectar patrones de tráfico anómalos.
- Sistema IDS/IPS para filtrar el tráfico ICMP según características sospechosas.

## Herramientas

- Marco de Ciberseguridad (CSF) del NIST
- Configuración de firewall
- Software de monitoreo de red
- Sistema IDS/IPS

## Contenido

- Análisis del informe de incidentes (aplicación del CSF del NIST)
