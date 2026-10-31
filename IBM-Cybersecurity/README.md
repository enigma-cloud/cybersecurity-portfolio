
## English

### Objective
Learn to configure and verify strong password policies in Windows using the
Local Group Policy Editor, and understand why they are a key preventive control
in operating system security.

### Tools and environment
- OS: Windows (local machine / lab)
- Local Group Policy Editor (gpedit)
- Kaspersky Password Checker (to evaluate password strength)

### Steps performed
1. Evaluated password strength with Kaspersky Password Checker, seeing how
   length and character variety affect cracking time (short passwords like
   "fido1973" break in seconds, while a 12-character passphrase takes much
   longer).
2. Opened the Local Group Policy Editor (gpedit).
3. Configured the following password policies, following Microsoft
   recommendations:
   - Enforce password history: 24
   - Maximum password age: 60 days
   - Minimum password age: 1 day
   - Minimum password length: 12 characters
4. Verified the changes in the security settings panel.

### Results
- Policies were configured according to Microsoft recommendations.
- A user trying to use a weak password will be rejected by the system.

### Lessons learned
- Password policies apply to Windows login, not to web services like Gmail.
- They are a preventive control (hardening): the administrator sets the rules
  so users cannot choose weak passwords.
- In a SOC, the analyst verifies that these policies are active on the machines.

---

# Laboratorio: Políticas de contraseña seguras en Windows

## Español

### Objetivo
Aprender a configurar y verificar políticas de contraseña seguras en Windows
usando el Editor de directivas de grupo local, y comprender por qué son un
control preventivo clave en la seguridad de un sistema operativo.

### Herramientas y entorno
- Sistema operativo: Windows (máquina local / laboratorio)
- Editor de directivas de grupo local (gpedit)
- Kaspersky Password Checker (para evaluar la fortaleza de contraseñas)

### Pasos realizados
1. Evalué la fortaleza de contraseñas con Kaspersky Password Checker,
   comprobando cómo la longitud y la variedad de caracteres afectan el tiempo
   de descifrado (por ejemplo, contraseñas cortas como "fido1973" se rompen
   en segundos, mientras que una de 12 caracteres basada en una frase tarda
   mucho más).
2. Accedí al Editor de directivas de grupo local (gpedit).
3. Configuré las siguientes políticas de contraseña, según las
   recomendaciones de Microsoft:
   - Exigir historial de contraseñas: 24
   - Vigencia máxima de la contraseña: 60 días
   - Vigencia mínima de la contraseña: 1 día
   - Longitud mínima de la contraseña: 12 caracteres
4. Verifiqué los cambios en el panel de configuración de seguridad.

### Resultados
- Las políticas quedaron configuradas según las recomendaciones de Microsoft.
- Un usuario que intente usar una contraseña débil será rechazado por el sistema.

### Aprendizajes
- Las políticas de contraseña se aplican al inicio de sesión de Windows, no a
  servicios web como Gmail.
- Son un control preventivo (hardening): el administrador configura las reglas
  para que los usuarios no elijan contraseñas débiles.
- En un SOC, el analista verifica que estas políticas estén activas en los equipos.


