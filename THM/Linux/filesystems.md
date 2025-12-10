# Sistema de Archivos en Linux – Enfoque de Seguridad

## /var/log
Carpeta principal para logs del sistema.

Archivos clave:
- **auth.log** → autenticaciones, fallas, SSH (muy útil para investigación)
- **syslog** → eventos del sistema
- **kern.log** → mensajes del kernel

## /etc
Archivos de configuración crítica.

- **/etc/passwd** → usuarios
- **/etc/shadow** → hashes de contraseñas
- **/etc/ssh/sshd_config** → seguridad SSH (hardening)

## /home
Directorio de usuarios.  
En un incidente, aquí se busca persistencia, scripts desconocidos o exfiltración.
