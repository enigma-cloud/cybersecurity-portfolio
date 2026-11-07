# TryHackMe — SIEM Alert Triage

### Overview
Practical lab from the **TryHackMe SIEM** room focused on **alert triage** inside a SOC environment. Four security alerts were investigated, analyzed, and classified as either **True Positive** or **False Positive**, following the standard SOC L1 triage workflow.

### Objectives
- Understand how SIEM alerts are generated and what each alert property means.
- Apply a structured triage workflow: prioritize → assign → investigate → verdict → close.
- Differentiate between True Positive and False Positive based on context and evidence.
- Document findings with clear analyst reasoning.

### Triage Workflow Applied
1. Prioritize alerts by severity.
2. Assign the alert to myself.
3. Move the alert to **In Progress**.
4. Read the alert name, description, and key indicators (host, IP, user, file).
5. Investigate the activity using the available context.
6. Determine the final verdict.
7. Add an analyst comment and move the alert to **Closed**.

### Alerts Investigated

#### 1. Brute Force Attack from External — Medium — True Positive
- **Assignee:** J.Adams (L2)
- **Verdict:** True Positive
- **Reasoning:** Repeated failed authentication attempts from an external source, consistent with a brute-force pattern.

#### 2. Unusual VPN Login Location — Medium — False Positive
- **Assignee:** T.Ross (L1)
- **Verdict:** False Positive
- **Reasoning:** Login from an unusual location, later confirmed as legitimate user activity (travel/remote work).

#### 3. Potential Data Exfiltration — Critical — False Positive
- **Destination:** `*.zoom.us`
- **Source IP:** `192.168.45.66`
- **Source Network:** `UK04/MEETINGROOM`
- **Sent Data:** 5.8 GB
- **Received Data:** 5.2 GB
- **Verdict:** False Positive
- **Reasoning:** The rule triggers on volume (5+ GB sent to a single destination in a day). However, the destination is a legitimate video-conferencing platform, the source network is a meeting room, and the traffic is symmetric (5.8 GB sent / 5.2 GB received), which is consistent with a long video call rather than data exfiltration. Exfiltration typically shows asymmetric traffic (large outbound, minimal inbound).

#### 4. Download from GitHub Repository — Low — False Positive
- **Accessed URL:** `https://github.com/facebook/react`
- **Source User:** G.Chandler
- **Source Host:** LPT-IT-063
- **Source Network:** VPN/DEVELOPERS
- **Verdict:** False Positive
- **Reasoning:** The rule triggers on any download from GitHub, since the platform hosts both legitimate projects and malicious scripts. In this case, the download came from the official React repository by an IT/developer user on the developers' VPN segment — fully consistent with the user's role.

#### 5. Double-Extension File Creation — High — True Positive
- **Host:** LPT-HR-009
- **Process Name:** `chrome.exe`
- **Process User:** S.Conway
- **Target File:** `C:\Users\S.Conway\Downloads\cats2025.mp4.exe`
- **File MotW:** `https://freecatvideoshd.monster/cats2025.mp4.exe`
- **File MD5:** `14d8486f3f63875ef93cfd240c5dc10b`
- **Verdict:** True Positive
- **Reasoning:** Double-extension file (`.mp4.exe`) used to disguise an executable as a video file. Windows hides known extensions by default, so the user sees "cats2025.mp4" while actually executing a binary. The origin domain (`freecatvideoshd.monster`) shows a typical malware-distribution pattern (cheap TLD, "free"/"hd" bait words). The download was performed through `chrome.exe`, consistent with a phishing vector. The affected host belongs to HR, a high-value target. Recommended action: escalate to L2 for binary analysis and domain blocking.

### Key Takeaways
- **Severity ≠ maliciousness.** A Critical alert means "this deserves investigation", not "this is an attack".
- **Context decides the verdict.** The same event can be a True Positive or False Positive depending on who, where, and what.
- **Symmetric vs. asymmetric traffic** is a strong indicator: video calls are symmetric, exfiltration is asymmetric.
- **Ambiguous rules exist.** Some rules detect a *condition* (any GitHub download, any large transfer), not malicious behavior. The analyst provides the context.
- **No benign explanation = True Positive.** If you have to force the benign explanation, it probably isn't benign.

### Tools & Concepts
- SIEM alert triage
- Alert properties: Time, Name, Severity, Status, Verdict, Assignee
- Indicators of Compromise (IoC): domain, file hash, file path
- MITRE ATT&CK mapping (see below)

### MITRE ATT&CK Mapping
| Alert | Technique |
|---|---|
| Brute Force Attack from External | T1110 — Brute Force |
| Unusual VPN Login Location | T1078 — Valid Accounts |
| Potential Data Exfiltration | T1041 — Exfiltration Over C2 Channel |
| Download from GitHub Repository | T1105 — Ingress Tool Transfer |
| Double-Extension File Creation | T1204.002 — User Execution: Malicious File |


### Descripción general
Laboratorio práctico de la sala **TryHackMe SIEM** centrado en el **triaje de alertas** dentro de un entorno SOC. Se investigaron, analizaron y clasificaron cuatro alertas de seguridad como **Verdadero Positivo** o **Falso Positivo**, siguiendo el flujo estándar de triaje de un analista SOC L1.

### Objetivos
- Comprender cómo se generan las alertas del SIEM y qué significa cada propiedad de la alerta.
- Aplicar un flujo de triaje estructurado: priorizar → asignar → investigar → veredicto → cerrar.
- Diferenciar entre Verdadero Positivo y Falso Positivo con base en el contexto y la evidencia.
- Documentar los hallazgos con un razonamiento de analista claro.

### Flujo de triaje aplicado
1. Priorizar las alertas por severidad.
2. Asignarme la alerta.
3. Mover la alerta a **In Progress**.
4. Leer el nombre, la descripción y los indicadores clave (host, IP, usuario, archivo).
5. Investigar la actividad usando el contexto disponible.
6. Determinar el veredicto final.
7. Agregar un comentario de analista y mover la alerta a **Closed**.

### Alertas investigadas

#### 1. Brute Force Attack from External — Medium — Verdadero Positivo
- **Asignado a:** J.Adams (L2)
- **Veredicto:** Verdadero Positivo
- **Razonamiento:** Intentos repetidos de autenticación fallida desde una fuente externa, consistente con un patrón de fuerza bruta.

#### 2. Unusual VPN Login Location — Medium — Falso Positivo
- **Asignado a:** T.Ross (L1)
- **Veredicto:** Falso Positivo
- **Razonamiento:** Inicio de sesión desde una ubicación inusual, confirmado posteriormente como actividad legítima del usuario (viaje/trabajo remoto).

#### 3. Potential Data Exfiltration — Critical — Falso Positivo
- **Destino:** `*.zoom.us`
- **IP origen:** `192.168.45.66`
- **Red origen:** `UK04/MEETINGROOM`
- **Datos enviados:** 5.8 GB
- **Datos recibidos:** 5.2 GB
- **Veredicto:** Falso Positivo
- **Razonamiento:** La regla se dispara por volumen (5+ GB enviados a un solo destino en un día). Sin embargo, el destino es una plataforma legítima de videoconferencia, la red de origen es una sala de reuniones y el tráfico es simétrico (5.8 GB enviados / 5.2 GB recibidos), lo cual es consistente con una videollamada larga y no con exfiltración de datos. La exfiltración suele mostrar tráfico asimétrico (mucho saliente, poco entrante).

#### 4. Download from GitHub Repository — Low — Falso Positivo
- **URL accedida:** `https://github.com/facebook/react`
- **Usuario origen:** G.Chandler
- **Host origen:** LPT-IT-063
- **Red origen:** VPN/DEVELOPERS
- **Veredicto:** Falso Positivo
- **Razonamiento:** La regla se dispara ante cualquier descarga desde GitHub, ya que la plataforma aloja tanto proyectos legítimos como scripts maliciosos. En este caso, la descarga provino del repositorio oficial de React por un usuario de IT/desarrollo en el segmento VPN de desarrolladores — totalmente consistente con su rol.

#### 5. Double-Extension File Creation — High — Verdadero Positivo
- **Host:** LPT-HR-009
- **Nombre del proceso:** `chrome.exe`
- **Usuario del proceso:** S.Conway
- **Archivo objetivo:** `C:\Users\S.Conway\Downloads\cats2025.mp4.exe`
- **File MotW:** `https://freecatvideoshd.monster/cats2025.mp4.exe`
- **MD5 del archivo:** `14d8486f3f63875ef93cfd240c5dc10b`
- **Veredicto:** Verdadero Positivo
- **Razonamiento:** Archivo con doble extensión (`.mp4.exe`) usado para disfrazar un ejecutable como archivo de video. Windows oculta las extensiones conocidas por defecto, así que el usuario ve "cats2025.mp4" mientras en realidad ejecuta un binario. El dominio de origen (`freecatvideoshd.monster`) muestra un patrón típico de distribución de malware (TLD barato, palabras gancho "free"/"hd"). La descarga se realizó mediante `chrome.exe`, consistente con un vector de phishing. El host afectado pertenece a RRHH, un objetivo de alto valor. Acción recomendada: escalar a L2 para análisis del binario y bloqueo del dominio.

### Conclusiones clave
- **Severidad ≠ malicia.** Una alerta Crítica significa "esto merece investigación", no "esto es un ataque".
- **El contexto decide el veredicto.** El mismo evento puede ser Verdadero o Falso Positivo según quién, dónde y qué.
- **Tráfico simétrico vs. asimétrico** es un indicador fuerte: las videollamadas son simétricas, la exfiltración es asimétrica.
- **Existen reglas ambiguas.** Algunas reglas detectan una *condición* (cualquier descarga de GitHub, cualquier transferencia grande), no comportamiento malicioso. El analista aporta el contexto.
- **Sin explicación benigna = Verdadero Positivo.** Si tienes que forzar la explicación benigna, probablemente no lo es.

### Herramientas y conceptos
- Triaje de alertas en SIEM
- Propiedades de alerta: Time, Name, Severity, Status, Verdict, Assignee
- Indicadores de Compromiso (IoC): dominio, hash de archivo, ruta de archivo
- Mapeo a MITRE ATT&CK (ver abajo)

