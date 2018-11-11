# **Fdisk**

-Es un comando muy importante para poder gestionar las particiones y espacio en disco incluso sin interfaz gráfica.

-Para revisar todas las particiones existentes en nuestro sistema escribimos el comando “-l”, que hará que se muestren ordenadas por el nombre del dispositivo.

-Para borrar una partición primero debemos seleccionar la que deseamos eliminar y una vez lo tengamos todo seleccionado pulsamos la letra ''D'' que significa Delete en inglés. Después se nos pedirá que introduzcamos el número que se le ha dado a la partición que nos interesa. Y para finalizar hacemos click en la letra ''W'' para guardar todo lo que hemos hecho.

-Para crear una nueva partición deberemos acceder al menú obviamente y después pulsar la letra ''N'' de New para poder crear la partición y acto seguido nos pedirá qué tipo de partición deseamos crear, extendida o primaria. Y para finalizar deberemos escoger el tamaño de la partición que vamos a crear.

-Para crear un partición de swap se requiere crear antes una partición de disco con el comando fdisk.

**Este es el comando para saber si tenemos alguna partición swap en nuestro sistema:**

cat /proc/swaps

**A continuación para crear una partición swap de 120 megas tendremos que crear un archivo con ese tamaño:**

sudo dd if=/dev/zero of=/mnt/120MiB.swap bs=1024 count=524288

**Damos permisos de leer y escribir solamente a root:**

sudo chmod 600 /mnt/120MiB.swap

**A continuación formateamos el archivo como swap:**

sudo mkswap /mnt/120MiB.swap

**Después tendremos que agregar la partición al sistema operativo:**

sudo swapon /mnt/120MiB.swap

**Y ahora ya se podrá observar con el siguiente comando que hemos creado la partición swap:**

cat /proc/swaps o cat /proc/meminfo.

**Finalmente para hacer los cambios permanentes:+*

sudo vim /etc/fstab

**Al final del archivo agregamos esta línea y guardamos todos los cambios:**

/mnt/120MiB.swap none swap sw 0 0

**Reiniciando el sistema operativo veremos que ya contamos con la nueva memoria swap.**
