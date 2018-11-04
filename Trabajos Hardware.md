**MBR:**

El MBR de normal se utiliza para arrancar sistemas operativos con Bootstrap pero también se puede utilizar para almacenar una tabla de particiones.

*Mbr contiene:*

**Tabla de Particiones** -ocupa 64 bytes. Como su nombre indica, es donde se registran las particiones.

**Gestor de Arranque** -ocupa 446 bytes. Gracias a esto se puede arrancar el SO (código máquina)

**Signature** -ocupa 2 bytes. Es la firma de la unidad arrancable



**¿Qué hemos hecho?**

-Lo primero que hicimos fue abrir el ordenador destornillando los tornillos que aguantan la tapa del lado contrario a la CPU. A continuación vimos lo que es compatible con la placa base y el profe nos explicó por encima donde estaba colocada cada componente.

-Jonatan nos enseñó el material que ibamos a utilizar para comprobar si había algun fallo en la fuente de alimentación. Utilizamos el tester y nos explicó como teníamos que hacerlo funcionar, enchufando el cable negro en el agujero negro y el rojo en el agujero rojo (normalmente) mas cercano al negro, siempre evitando las ''A''. Una vez comprobado si la fuente de alimentación tenia algun problema, vimos que funcionaba pero que estaba un poco echa polvo. La señal de que un componente todavía funciona es que el tester hace un pitido intermitente y nos marca un número (3,3 vd aprox).

-Jonatan también nos ha enseñado un ''truquillo'' por si nos falta el material y es que con un pin o un hilo de hierro podemos doblarlo y conectarlo en el lugar adecuado para que nos haga la misma funcion y poder comprobar si todo está bien, aunque el proceso será mas lento.

-Se nos ha enseñado a cambiar la pasta termica de la CPU y se recomienda usar un plastico duro para quitarla ya que la pasta con el tiempo se queda petrificada, después añadiriamos la nueva pasta.

-También comprobamos el botón de encendido para ver si funcionaba bien, en caso de que no funcione bien lo que se tendría que hacer es cambiar los cables con el botón del reset y así podríamos hacerlo funcionar.




**Reglas-MBR**

**¿Qué reglas existen?**

1- Solo 1 de las primarias puede ser extended.

2- Dentro de las extended (si existiera) puede haber N lógicas.

3- Una primaria debe ser activa. (obligatorio)

Información adicional Linux no necesita de estas reglas, ya que dichas reglas son para Windows.

Windows necesita una partición primaria y activa para arrancar mientras que Linux no.




**32-bits-vs-64-bits**
Empezaremos diciendo que las *CPU* de **32 bits** son mas antiguas que las de **64 bits**, pero no por ello se les ha dejado de dar soporte, ya que a dia de hoy todavía hay gente que les sigue dando uso. Por lo tanto los desarrolladores de software y los *Sistemas Operativos* siguen dándole el soporte necesario.

Diferencias

-La principal diferencia es la memória *RAM*. Una *CPU* de **32 bits** no puede gestionar la misma capacidad de *RAM* que una *CPU* de **64 bits**. Independientemente de la *RAM* que tenga tu ordenador, la *CPU* de **32 bits** solo puede aprovechar un máximo de 4GB mientras que la de **64 bits** puede aprovechar unos 16 Exabytes (Cifra a la que ningúna RAM ni Sistema Operativo es capaz de llegar hoy en día).

-Otra de las diferencias que pueden tener es el número de aplicaciones en funcionamiento, dándote problemas una de **32 bits** con mas de 4 aplicaciones en funcionamiento simultáneo ya que eso pediría más *RAM*. (También puede depender de que aplicaciones utilices debido al consumo de cada una.) Otro añadido sería que las *CPU* de **32 bits** solo pueden asignar 2GB a cada aplicación mientras que con las *CPU* de **64 bits** pueden llegar a los 8TB.

-Y la última diferencia y no por ello menos importante sería que una *CPU* de **64 bits** es capaz de utilizar un *Sistema Operativo* tanto de **32** como de **64 bits**, aunque si instalamos un SO de 32 bits no podremos utilizar aplicaciones de 64 bits, en cambio las *CPU* de **32 bits** solo pueden usar los *Sistemas Operativos* de **32 bits**.




**DE QUE ESTÁ FORMADO UN SISTEMA OPERATIVO LINUX.**

**KERNEL**

-Es el nucleo del Sistema Operativo. Facilita el acceso seguro de los programas al Hardware. Ocupa 150MG en RAM

**GUI-CLI**

-Son las lineas de comandos y el entorno gráfico, totalmente necesario para el funcionamiento del Sistema Operativo.

El entorno gráfico está formado de lo siguiente:

**Entorno de escritorio**

Ofrece una interfaz gráfica y aplicaciones que se coordinan entre ellas en diferentes ámbitos. Estas aplicaciones són:

-Mate

-Gnome

-KDE

-XFCE

-Cinnamon

**Gestor de ventanas**

Como es lógico su función es la de gestionar las ventanas de cada aplicación. También nos proporciona el Layout.

Un ejemplo de Gestor de ventanas seria OpenBox.

**Ventanas mosaico**

Sirve para controlar el formato mosaico de las ventanas.




**Como cambiar la password de root en Linux**

*Sabiendola*

1-Abre la Terminal

2-Teclea sudo su

3-Introduce tu clave actual

4-Teclea "passwd root" y escribe tu nueva clave

5-Pulsa enter y cierra la terminal

*Sin saberla*

**1-nos dirigimos a la linea Linux16 y cambiamos el conjunto de palabras “rghb quiet” por**

rd.break enforcing= 0

**2-Ahora pulsamos Ctrl+X para que continue el proceso de carga. Si el sistema está encriptado nos pedirá ahora la contraseña de LUKS. 
-Con esto hemos hecho que el sistema de Fedora se cargue en modo de emergencia, ahora hemos de montar el disco duro con el siguiente comando:**

mount -o remount, rw / sysroot

**4-Y ejecutamos el comando chroot para acceder al sistema. Escribiendo lo siguiente:**

chroot / sysroot

**5-Y ahora ya podemos ejecutar el comando passwd para cambiar la contraseña de root. Tras ejecutar el comando se nos pedirá escribir la contraseña de root nueva dos veces. Ahora escribimos dos veces Exit para reiniciar el sistema. Tras ello iniciamos la sesión como root y restauramos los cambios del grub escribiendo esto:**


restorecon -v /etc/shadow

**Y para finalizar**

setenforce 1




**Detectar Hardware en Linux**

-Para revisar desde una Terminal el hardware de nuestro pc (Linux) tenemos que escribir el comando ''lshw'' (Sin las comillas) en cambio si escribimos ''lshw-gui'' podremos revisar también el hardware pero desde una ventana a parte.

-Para Windows nos tenemos que descargar Cpu-z o speccy y ejecutar el programa para ver el Hardware de nuestro PC.




**GNU/GPL**

-És una licencia muy utilizada en el mundillo del Software libre ya que te permite hacer cualquier cosa a tu voluntad sobre el Software.




**Fdisk**

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

**Finalmente para hacer los cambios permanentes:**

sudo vim /etc/fstab

**Al final del archivo agregamos esta línea y guardamos todos los cambios:**

/mnt/120MiB.swap  none  swap  sw  0 0

**Reiniciando el sistema operativo veremos que ya contamos con la nueva memoria swap.**
