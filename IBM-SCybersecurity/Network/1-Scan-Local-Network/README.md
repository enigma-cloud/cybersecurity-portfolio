
## Overview

This report documents a **host discovery and port scan** performed on a home network using **Nmap**, followed by a **context analysis** to determine whether the findings represent real risk. The goal was not to list open ports, but to answer the question that matters: *is this finding exploitable, and from where?*

---

## Environment

| Item | Value |
| --- | --- |
| Analyst host | `soc-lab` (Kali Linux, VM) |
| Target network | `192.168.101.0/24` |
| Gateway / ONU | `192.168.101.1` |
| Scan tool | Nmap 7.98 |
| Date | 2026-11-11 |

---

## Commands executed

### 1. Host discovery (ping sweep)

```bash
sudo nmap -sn 192.168.101.1/24
```

**Result:** 256 IP addresses scanned, **4 hosts up**, completed in 6.11 seconds.

| Host | MAC vendor |
| --- | --- |
| `192.168.101.1` (gateway / ONU) | Shenzhen C-Data Technology |
| `192.168.101.5` | Huawei Technologies |
| `192.168.101.x` | CyberTAN Technology |
| `soc-lab.local` | — (analyst host) |

### 2. Port scan (SYN, fast)

```bash
sudo nmap -sS -F 192.168.101.1/24
```

**Result:** 256 IP addresses scanned, **3 hosts up**, completed in 26.60 seconds.

| Host | Open ports | Service |
| --- | --- | --- |
| `192.168.101.1` (ONU) | **80/tcp**, **443/tcp** | http, https |
| `192.168.101.5` | **5357/tcp** | wsddapi (Web Services Dynamic Discovery) |
| `soc-lab.local` | none | 100 filtered ports (ignored states) |

---

## Findings

### Finding 1 — Port 80 (HTTP) open on the ONU management panel

- **Host:** `192.168.101.1`
- **Port:** 80/tcp (HTTP)
- **Service:** ONU Web Management panel
- **Exposure:** Local network only
- **Risk: Low**

The ONU (fibre termination unit) exposes its administrative web panel over unencrypted HTTP. The panel is reachable by any device on the local network.

### Finding 2 — Management panel does not enforce HTTPS

- **Host:** `192.168.101.1`
- **Evidence:** URL remains on `http://192.168.101.1/index.html`; the browser flags the connection as **"Not secure"**. No redirect to `https://` occurs.
- **Exposure:** Local network only
- **Risk: Medium**

Administrative credentials are submitted over an unencrypted channel. An attacker already present on the local network could capture them in cleartext with a packet analyser such as Wireshark.

### Finding 3 — Port 5357 (WSD) open on a secondary host

- **Host:** `192.168.101.5`
- **Port:** 5357/tcp (wsddapi)
- **Exposure:** Local network only
- **Risk: Low**

Web Services Dynamic Discovery is a Windows feature used for automatic discovery of devices and printers on a network. It is expected on a home network and carries no direct exposure.

---

## Verification

A finding is not a vulnerability until its exposure is established. Both an internal and an external test were performed.

### Internal test

Accessing the public IP from inside the network failed (the ONU does not support hairpin NAT). **This test is not conclusive** — it cannot distinguish between a closed port and a router that simply does not loop traffic back.

### External test

A trusted contact on a **different network** opened `http://<public-IP>` in a browser.

**Result:** `ERR_TIMED_OUT` — the host took too long to respond.

| Observation | Meaning |
| --- | --- |
| Timeout, not connection refused | The firewall **drops** packets silently rather than rejecting them |
| No response from outside | Port 80 is **not reachable from the internet** |

**Conclusion:** the ONU management panel is **not exposed to the internet**. The drop-instead-of-reject behaviour is good practice: it does not confirm to a remote attacker that a service exists.

---

## Limitations

- The external test was performed from a single external network; results may vary by ISP routing.
- The ONU firmware is supplied by the ISP and may not expose an option to enable HTTPS. If unavailable, this cannot be remediated from the client side.
- Port scan used the fast (`-F`) profile, covering the 100 most common ports only. A full 65535-port scan was not performed.

---

## Risk summary

| Finding | Port | Exposure | Risk |
| --- | --- | --- | --- |
| ONU management panel over HTTP | 80 | Local only | Low |
| No HTTPS enforcement on panel | 80 | Local only | Medium |
| WSD service | 5357 | Local only | Low |

---

## Remediation applied

- Administrative password on the ONU changed from the factory default.
- Wi-Fi (WPA) key changed from the factory default.

Both actions were performed from the local management panel at `http://192.168.101.1`.

---

## Recommendations

1. Enable HTTPS on the management panel if the firmware supports it.
2. Keep the administrative password changed from the factory default.
3. Keep the Wi-Fi key strong and rotate it if unknown devices appear.
4. Disable remote management if the option exists and is not in use.
5. Re-run the external verification after any firmware or configuration change.

---

## Key takeaways

- **An open port is a finding, not a vulnerability.** The same open port is low risk on a local network and high risk on the internet.
- **Context determines severity.** The deciding question is not *"is it open?"* but *"who can reach it?"*
- **Internal tests are not conclusive.** Testing from inside your own network can produce false positives and false negatives.
- **A silent drop is better than a rejection.** It reveals less to a remote attacker.
- **Document limitations honestly.** Saying what you did *not* verify is part of the analysis, not a weakness in it.

---

## Tools and references

- Nmap 7.98 — host discovery and port scanning
- Wireshark — referenced as the tool an on-network attacker would use to capture cleartext credentials
- MITRE ATT&CK — T1040 (Network Sniffing) applies to the cleartext credential exposure scenario

---
---

# Escaneo de Red — Red Local

**Diana Esmeralda Cárdenas Duarte** · Noviembre 2026

---

## Descripción general

Este informe documenta un **descubrimiento de hosts y escaneo de puertos** realizado en una red doméstica con **Nmap**, seguido de un **análisis de contexto** para determinar si los hallazgos representan riesgo real. El objetivo no fue listar puertos abiertos, sino responder la pregunta que importa: *¿este hallazgo es explotable, y desde dónde?*

---

## Entorno

| Elemento | Valor |
| --- | --- |
| Host analista | `soc-lab` (Kali Linux, VM) |
| Red objetivo | `192.168.101.0/24` |
| Gateway / ONU | `192.168.101.1` |
| Herramienta | Nmap 7.98 |
| Fecha | 2026-11-11 |

---

## Comandos ejecutados

### 1. Descubrimiento de hosts (ping sweep)

```bash
sudo nmap -sn 192.168.101.1/24
```

**Resultado:** 256 direcciones IP escaneadas, **4 hosts activos**, en 6.11 segundos.

| Host | Fabricante MAC |
| --- | --- |
| `192.168.101.1` (gateway / ONU) | Shenzhen C-Data Technology |
| `192.168.101.5` | Huawei Technologies |
| `192.168.101.x` | CyberTAN Technology |
| `soc-lab.local` | — (host analista) |

### 2. Escaneo de puertos (SYN, rápido)

```bash
sudo nmap -sS -F 192.168.101.1/24
```

**Resultado:** 256 direcciones IP escaneadas, **3 hosts activos**, en 26.60 segundos.

| Host | Puertos abiertos | Servicio |
| --- | --- | --- |
| `192.168.101.1` (ONU) | **80/tcp**, **443/tcp** | http, https |
| `192.168.101.5` | **5357/tcp** | wsddapi (Web Services Dynamic Discovery) |
| `soc-lab.local` | ninguno | 100 puertos filtrados |

---

## Hallazgos

### Hallazgo 1 — Puerto 80 (HTTP) abierto en el panel de la ONU

- **Host:** `192.168.101.1`
- **Puerto:** 80/tcp (HTTP)
- **Servicio:** Panel de administración de la ONU
- **Exposición:** Solo red local
- **Riesgo: Bajo**

La ONU (equipo de terminación de fibra) expone su panel de administración por HTTP sin cifrar. El panel es alcanzable por cualquier dispositivo de la red local.

### Hallazgo 2 — El panel no fuerza HTTPS

- **Host:** `192.168.101.1`
- **Evidencia:** La URL permanece en `http://192.168.101.1/index.html`; el navegador marca la conexión como **"No seguro"**. No hay redirección a `https://`.
- **Exposición:** Solo red local
- **Riesgo: Medio**

Las credenciales de administración se envían por un canal sin cifrar. Un atacante ya presente en la red local podría capturarlas en texto claro con un analizador de tráfico como Wireshark.

### Hallazgo 3 — Puerto 5357 (WSD) abierto en un host secundario

- **Host:** `192.168.101.5`
- **Puerto:** 5357/tcp (wsddapi)
- **Exposición:** Solo red local
- **Riesgo: Bajo**

Web Services Dynamic Discovery es una función de Windows para el descubrimiento automático de dispositivos e impresoras en la red. Es esperable en una red doméstica y no representa exposición directa.

---

## Verificación

Un hallazgo no es una vulnerabilidad hasta que se establece su exposición. Se realizaron dos pruebas: interna y externa.

### Prueba interna

El acceso a la IP pública desde dentro de la red falló (la ONU no soporta hairpin NAT). **Esta prueba no es concluyente** — no permite distinguir entre un puerto cerrado y un router que simplemente no devuelve el tráfico.

### Prueba externa

Un contacto de confianza en una **red distinta** abrió `http://<IP-pública>` en el navegador.

**Resultado:** `ERR_TIMED_OUT` — el host tardó demasiado en responder.

| Observación | Significado |
| --- | --- |
| Timeout, no conexión rechazada | El firewall **descarta** paquetes en silencio en lugar de rechazarlos |
| Sin respuesta desde fuera | El puerto 80 **no es alcanzable desde internet** |

**Conclusión:** el panel de administración de la ONU **no está expuesto a internet**. El comportamiento de descarte silencioso es buena práctica: no le confirma a un atacante remoto que el servicio existe.

---

## Limitaciones

- La prueba externa se realizó desde una sola red externa; los resultados pueden variar según el enrutamiento del ISP.
- El firmware de la ONU lo provee el ISP y puede no exponer una opción para habilitar HTTPS. Si no está disponible, no puede remediarse desde el lado del cliente.
- El escaneo usó el perfil rápido (`-F`), que cubre solo los 100 puertos más comunes. No se realizó un escaneo completo de 65535 puertos.

---

## Resumen de riesgo

| Hallazgo | Puerto | Exposición | Riesgo |
| --- | --- | --- | --- |
| Panel de la ONU por HTTP | 80 | Solo local | Bajo |
| Sin forzar HTTPS en el panel | 80 | Solo local | Medio |
| Servicio WSD | 5357 | Solo local | Bajo |

---

## Remediación aplicada

- Contraseña de administrador de la ONU cambiada respecto a la de fábrica.
- Clave del Wi-Fi (WPA) cambiada respecto a la de fábrica.

Ambas acciones se realizaron desde el panel local en `http://192.168.101.1`.

---

## Recomendaciones

1. Habilitar HTTPS en el panel de administración si el firmware lo soporta.
2. Mantener la contraseña de administrador cambiada respecto a la de fábrica.
3. Mantener una clave Wi-Fi fuerte y rotarla si aparecen dispositivos desconocidos.
4. Deshabilitar la administración remota si la opción existe y no se usa.
5. Repetir la verificación externa tras cualquier cambio de firmware o configuración.

---

## Conclusiones clave

- **Un puerto abierto es un hallazgo, no una vulnerabilidad.** El mismo puerto es riesgo bajo en red local y riesgo alto en internet.
- **El contexto determina la severidad.** La pregunta decisiva no es *"¿está abierto?"* sino *"¿quién puede alcanzarlo?"*
- **Las pruebas internas no son concluyentes.** Probar desde tu propia red puede dar falsos positivos y falsos negativos.
- **Un descarte silencioso es mejor que un rechazo.** Revela menos a un atacante remoto.
- **Documentar las limitaciones con honestidad.** Decir lo que *no* verificaste es parte del análisis, no una debilidad de él.

---

## Herramientas y referencias

- Nmap 7.98 — descubrimiento de hosts y escaneo de puertos
- Wireshark — referenciado como la herramienta que usaría un atacante en la red para capturar credenciales en texto claro
- MITRE ATT&CK — T1040 (Network Sniffing) aplica al escenario de exposición de credenciales en texto claro
