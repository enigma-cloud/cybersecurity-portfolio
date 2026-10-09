# Web Attack Investigation: yummyrecipesforme.com

Activity on network protocols and incident investigation.

## Description

Investigation of a security incident on the yummyrecipesforme.com website. A disgruntled baker used a brute force attack to access the admin panel, modified the site's source code, and embedded malicious JavaScript that redirected visitors to a fake website (greatrecipesforme.com) where the company's recipes were published for free.

## Scenario

A security analyst investigates a security event using the tcpdump network protocol analyzer. The logs show the following process:

1. The browser requests a DNS resolution for yummyrecipesforme.com.
2. The DNS server responds with the correct IP address.
3. The browser initiates an HTTP request for the web page.
4. The browser starts downloading the malware.
5. The browser requests another DNS resolution for greatrecipesforme.com.
6. The DNS server responds with the new IP address.
7. The browser initiates an HTTP request to the new IP address.

## Network protocols identified

- **DNS (Domain Name System)**: used to resolve the website URL to an IP address (port 53).
- **HTTP (Hypertext Transfer Protocol)**: used to establish the connection between the user and the website (port 80).
- **TCP (Transmission Control Protocol)**: transport layer protocol that establishes and maintains the connection.

## Type of attack

**Brute Force Attack**

- The attacker repeatedly tried known default passwords for the admin account until successful.
- After gaining access, the attacker modified the source code and embedded malicious JavaScript.
- The malicious file redirected visitors to a fake version of the website.

## Impact on the organization

- The company's recipes were published for free on the fake website.
- Customer devices were infected with malware.
- Damage to the company's reputation and loss of revenue.

## Recommended solution

- **Enforce strong passwords**: eliminate the use of default passwords for admin accounts.
- **Implement two-factor authentication (2FA)**: adds an extra layer of security.
- **Limit login attempts**: prevents repeated password guessing.
- **Monitor login attempts**: detects suspicious activity early.

## Tools

- tcpdump (network protocol analyzer)
- DNS and HTTP traffic log

## Contents

- Security incident report (incident documentation and recommendations)

---

# Investigación de Ataque Web: yummyrecipesforme.com

Actividad sobre protocolos de red e investigación de incidentes.

## Descripción

Investigación de un incidente de seguridad en el sitio web yummyrecipesforme.com. Un panadero descontento utilizó un ataque de fuerza bruta para acceder al panel de administración, modificó el código fuente del sitio e incrustó JavaScript malicioso que redirigía a los visitantes a un sitio web falso (greatrecipesforme.com) donde las recetas de la empresa se publicaban de forma gratuita.

## Escenario

Un analista de seguridad investiga un evento de seguridad utilizando el analizador de protocolos de red tcpdump. Los registros muestran el siguiente proceso:

1. El navegador solicita una resolución DNS para yummyrecipesforme.com.
2. El servidor DNS responde con la dirección IP correcta.
3. El navegador inicia una solicitud HTTP para la página web.
4. El navegador inicia la descarga del malware.
5. El navegador solicita otra resolución DNS para greatrecipesforme.com.
6. El servidor DNS responde con la nueva dirección IP.
7. El navegador inicia una solicitud HTTP a la nueva dirección IP.

## Protocolos de red identificados

- **DNS (Sistema de Nombres de Dominio)**: utilizado para resolver la URL del sitio web a una dirección IP (puerto 53).
- **HTTP (Protocolo de Transferencia de Hipertexto)**: utilizado para establecer la conexión entre el usuario y el sitio web (puerto 80).
- **TCP (Protocolo de Control de Transmisión)**: protocolo de la capa de transporte que establece y mantiene la conexión.

## Tipo de ataque

**Ataque de Fuerza Bruta**

- El atacante probó repetidamente contraseñas predeterminadas conocidas para la cuenta de administrador hasta acertar.
- Tras obtener acceso, modificó el código fuente e incrustó JavaScript malicioso.
- El archivo malicioso redirigía a los visitantes a una versión falsa del sitio web.

## Impacto en la organización

- Las recetas de la empresa se publicaron gratuitamente en el sitio web falso.
- Los dispositivos de los clientes fueron infectados con malware.
- Daño a la reputación de la empresa y pérdida de ingresos.

## Solución recomendada

- **Exigir contraseñas seguras**: eliminar el uso de contraseñas predeterminadas en las cuentas de administrador.
- **Implementar autenticación de dos factores (2FA)**: agrega una capa adicional de seguridad.
- **Limitar los intentos de inicio de sesión**: evita la adivinación repetida de contraseñas.
- **Monitorear los intentos de inicio de sesión**: detecta actividad sospechosa a tiempo.

## Herramientas

- tcpdump (analizador de protocolos de red)
- Registro de tráfico DNS y HTTP

## Contenido

- Informe sobre incidentes de seguridad (documentación del incidente y recomendaciones)
