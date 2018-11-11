# Como cambiar la password de root en Linux

*Sabiendola*

1-Abre la Terminal

2-Teclea sudo su

3-Introduce tu clave actual

4-Teclea "passwd root" y escribe tu nueva clave

5-Pulsa enter y cierra la terminal

*Sin saberla*

**1-nos dirigimos a la linea Linux16 y cambiamos el conjunto de palabras “rghb quiet” por**

rd.break enforcing= 0

**2-Ahora pulsamos Ctrl+X para que continue el proceso de carga. Si el sistema está encriptado nos pedirá ahora la contraseña de LUKS. -Con esto hemos hecho que el sistema de Fedora se cargue en modo de emergencia, ahora hemos de montar el disco duro con el siguiente comando:**

mount -o remount, rw / sysroot

**3-Y ejecutamos el comando chroot para acceder al sistema. Escribiendo lo siguiente:**

chroot / sysroot

**4-Y ahora ya podemos ejecutar el comando passwd para cambiar la contraseña de root. Tras ejecutar el comando se nos pedirá escribir la contraseña de root nueva dos veces. Ahora escribimos dos veces Exit para reiniciar el sistema. Tras ello iniciamos la sesión como root y restauramos los cambios del grub escribiendo esto:**

restorecon -v /etc/shadow

**Y para finalizar**

setenforce 1
