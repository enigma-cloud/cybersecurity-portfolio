# Windows Defender Antivirus — Real-Time Protection Lab

### Overview
Hands-on lab from the IBM Cybersecurity Fundamentals program covering Windows
Defender Antivirus configuration on Windows. The lab explores real-time
protection, threat definition updates, quick and custom scans, scheduled
full scans, and malware test-file detection using the EICAR standard.

**Tools:** Windows Security · Windows Defender Antivirus · Task Scheduler · EICAR test file
**Source:** IBM Skills Network — Hands-on Lab: Windows Defender Antivirus

### Objectives
- Review virus and threat protection in Windows Security.
- Update threat definitions.
- Run a quick scan and a custom scan.
- Schedule a weekly full scan with Task Scheduler.
- Simulate a malware download with the EICAR test file and verify quarantine.

### Steps

#### 1. Review virus and threat protection
Opened Windows Security and navigated to Virus & threat protection. Reviewed the
four sections: Current threats, Virus & threat protection settings, Virus & threat
protection updates, and Ransomware protection.


#### 2. Update threat definitions
Ran a manual check for updates under Virus & threat protection updates. Confirmed
the timestamp of the latest definition update changed after the check completed.

#### 3. Run a quick scan
Started a quick scan from the Current threats section. Waited for completion and
reviewed the results in Protection history.

#### 4. Run a custom scan
Ran a custom scan targeting a specific folder only, then verified the scan scope
and results.

#### 5. Enable real-time protection
Opened Manage settings and confirmed Real-time protection was enabled, giving
continuous monitoring of the system.

#### 6. Schedule a weekly full scan
Created a task in Task Scheduler named "Weekly Full Scan". Configured the trigger
as Weekly, set the action to run the Defender scan, and adjusted conditions to
avoid running on battery power.

#### 7. Configure notifications
Enabled notifications for recent activity and scan results, threats found with no
immediate action needed, and blocked files or activity.

#### 8. Test detection with the EICAR file
Downloaded the EICAR anti-malware test file from eicar.org. Windows Defender
detected it in real time during download, blocked it, and placed it in quarantine
without requiring a manual scan.

#### 9. Review the quarantine report
Opened Protection history to review the detected threat, the action taken, and the
recommended options for handling it.


### Key Takeaways
- Real-time protection catches threats as they are written to disk, before any
  manual scan is needed.
- Threat definitions must be current before trusting a scan result.
- Scheduled scans automate routine coverage; Task Scheduler conditions prevent
  scans from running on battery.
- The EICAR file is a safe, standardized way to validate antivirus response
  without using real malware.

---


### Descripción general
Laboratorio práctico del programa IBM Cybersecurity Fundamentals sobre la
configuración de Windows Defender Antivirus en Windows. Se exploran la protección
en tiempo real, la actualización de definiciones de amenazas, los análisis rápido
y personalizado, la programación de análisis completos y la detección de un archivo
de prueba de malware con el estándar EICAR.

**Herramientas:** Seguridad de Windows · Windows Defender Antivirus · Programador de tareas · Archivo de prueba EICAR
**Fuente:** IBM Skills Network — Laboratorio práctico: Antivirus de Windows Defender

### Objetivos
- Revisar la protección contra virus y amenazas en Seguridad de Windows.
- Actualizar las definiciones de amenazas.
- Ejecutar un análisis rápido y un análisis personalizado.
- Programar un análisis completo semanal con el Programador de tareas.
- Simular la descarga de malware con el archivo de prueba EICAR y verificar la cuarentena.

### Pasos

#### 1. Revisar la protección contra virus y amenazas
Abrí Seguridad de Windows y navegué a Protección contra virus y amenazas. Revisé
las cuatro secciones: Amenazas actuales, Configuración de protección contra virus y
amenazas, Actualizaciones de protección contra virus y amenazas, y Protección
contra ransomware.


#### 2. Actualizar las definiciones de amenazas
Ejecuté una búsqueda manual de actualizaciones en Actualizaciones de protección
contra virus y amenazas. Confirmé que la fecha y hora de la última actualización
cambiaron al terminar el proceso.

#### 3. Ejecutar un análisis rápido
Inicié un análisis rápido desde la sección Amenazas actuales. Esperé a que
finalizara y revisé los resultados en el Historial de protección.

#### 4. Ejecutar un análisis personalizado
Ejecuté un análisis personalizado dirigido solo a una carpeta específica y luego
verifiqué el alcance y los resultados del análisis.

#### 5. Habilitar la protección en tiempo real
Abrí Administrar configuraciones y confirmé que la Protección en tiempo real estaba
activada, lo que da monitoreo continuo del sistema.

#### 6. Programar un análisis completo semanal
Creé una tarea en el Programador de tareas llamada "Análisis completo semanal".
Configuré el desencadenador como Semanal, establecí la acción para ejecutar el
análisis de Defender y ajusté las condiciones para evitar ejecutarlo con batería.

#### 7. Configurar las notificaciones
Activé las notificaciones para actividad reciente y resultados de escaneo, amenazas
encontradas sin acción inmediata necesaria, y archivos o actividades bloqueadas.

#### 8. Probar la detección con el archivo EICAR
Descargué el archivo de prueba antimalware EICAR desde eicar.org. Windows Defender
lo detectó en tiempo real durante la descarga, lo bloqueó y lo puso en cuarentena
sin necesidad de un análisis manual.

#### 9. Revisar el informe de cuarentena
Abrí el Historial de protección para revisar la amenaza detectada, la acción tomada
y las opciones recomendadas para manejarla.

Pantallazo:

### Conclusiones clave
- La protección en tiempo real detecta amenazas mientras se escriben en disco,
  antes de cualquier análisis manual.
- Las definiciones de amenazas deben estar actualizadas antes de confiar en el
  resultado de un análisis.
- Los análisis programados automatizan la cobertura rutinaria; las condiciones del
  Programador de tareas evitan que se ejecuten con batería.
- El archivo EICAR es una forma segura y estandarizada de validar la respuesta del
  antivirus sin usar malware real.

---



