# Prueba del comando auth.log

## Umbral de detección Para distinguir los fallos de autenticación aislados de la actividad sospechosa, se definió un umbral: - **Señal:** Intentos de autenticación fallidos - **Fuente:** /var/log/auth.log - **Umbral:** ≥ 5 intentos fallidos en 2 minutos Este umbral ayuda a reducir los falsos positivos causados por errores del usuario y al mismo tiempo permite la detección temprana de posibles intentos de fuerza bruta o mal uso.

## sudo ls -lh /var/log/aut.log
- Muestra que el archivo exista y que esté activo.

## sudo tail -n 50 /var/log/auth.log
- Muestra los 50 registros recientes.
![Resultado del comando con intentos de acceso a Linux](Images/intentos_fallidos.png)

## sudo grep -i "failed password" /var/log/auth.log
- Buscar intentos fallidos de login por contraseña incorrecta.
![Resultado del comando con intentos de acceso a Linux](Images/failedpassword.png)

## sudo grep -i "invalid user" /var/log/auth.log
- Busca intentos de login por usuarios inexistentes. En este caso solo se encuentra la búsqueda realizada por mí al contener el "sshd", para evitarlo se realiza el uso de otro comando, "sudo grep -i "sshd" /var/log/auth.log | grep -v "sudo:"

##sudo grep "X.X.X.X" /var/log/auth.log
- Filtra eventos de una IP única.
