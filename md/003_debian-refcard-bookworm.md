# Tarjeta de Referencia Debian 

*Las 101 cosas más importantes para el uso de Debian.*

Edición: Refcard v. 12.0 (Bookworm), publicada el 22 de marzo de 2023. Conversión a Markdown: 1 de octubre de 2026.

Fuente: [repositorio oficial de refcard](https://salsa.debian.org/ddp-team/refcard), etiqueta `12.0`.

> Las 85 entradas y las 9 secciones están completas. El subtítulo "101 cosas" es el original y no representa el conteo real de entradas.

## Pidiendo ayuda

  - man comando 
    Muestra la página de manual del comando indicado. Todas las órdenes y muchos otros archivos tienen páginas de manual. Para aprender acerca de funciones internas, consulte `man bash`.

  - comando   \[`--`help, `-`h\]  
    Breve ayuda para la mayor parte de las órdenes.

  - `/usr/share/doc/ paquete/`  
    Busque aquí toda la documentación. El archivo opcional `README.Debian` contiene información específica para Debian.

  - [Documentación Web](https://www.debian.org/doc/)  
    Puede encontrar la Referencia de Debian, el Manual de instalación, las preguntas frecuentes (FAQs), guías y demás documentación en `https://www.debian.org/doc/`

  - [Listas de correo](https://lists.debian.org/) en `https://lists.debian.org/`  
    La comunidad de Debian siempre está dispuesta a ayudar, consulte en primer lugar la sección `users` en `https://lists.debian.org/`

  - [El Wiki](https://wiki.debian.org/) en `https://wiki.debian.org/`  
    Contiene todo tipo de información útil.

## Instalación

  - [Instalador](https://www.debian.org/devel/debian-installer/)  
    Toda la información respecto al instalador está disponible en `https://www.debian.org/devel/debian-installer/`.

  - [Imágenes de CD](https://www.debian.org/distrib/)  
    Puede bajarlas de `https://www.debian.org/distrib/`.

  - `boot: expert`  
    E.g. to set up the network w/o DHCP or to adapt bootloader installation.

  - Or use a [Live image](https://www.debian.org/CD/live/)  
    Containing the user-friendly Calamares installer: `https://www.debian.org/CD/live/`

## Bugs

  - [Seguimiento](https://bugs.debian.org/) en `https://bugs.debian.org/`  
    Puede consultar informes de fallas existentes y corregidos.

  - Específico a paquete  
    Ver `https://bugs.debian.org/paquete/`. El pseudo-paquete `wnpp` se utiliza para solicitar paquetes aún no incluidos en Debian.

  - reportbug  
    Informa una falla por correo.

  - [Reportar](https://www.debian.org/Bugs/Reporting)  
    Instrucciones en `https://www.debian.org/Bugs/Reporting`.

## Configuración

  - `/etc/`  
    Todos los archivos de configuración del sistema están en el directorio `/etc/`.

  - editor archivos  
    Editor de textos por defecto. Puede ser `nano`, `emacs`, `vi`, `joe`.

  - [CUPS](http://localhost:631) en `http://hostname:631`  
    Interfaz web a la configuración de impresoras.

  - dpkg-reconfigure nombre-de-paquete  
    Reconfigura un paquete, p. ej. keyboard-configuration (teclado), locales (localización).

  - update-alternatives opciones  
    Gestiona alternativas en los comandos.

  - update-grub  
    Después de cambiar `/etc/default/grub`.

## Demonios y sistema

  - `systemctl restart nombre.service`  
    Reinicia un servicio o demonio.

  - `systemctl stop nombre.service`  
    Detiene un servicio o demonio.

  - `systemctl start nombre.service`  
    Inicia un servicio o demonio.

  - systemctl halt  
    Detiene el sistema.

  - systemctl reboot  
    Reinicia el sistema.

  - systemctl poweroff  
    Apaga el sistema.

  - systemctl suspend  
    Suspende el sistema.

  - systemctl hibernate  
    Pone a hibernar el sistema.

  - `/var/log/`  
    Todos los archivos de bitácora están en este directorio.

  - `/etc/default/`  
    Valores por defecto para muchos demonios y servicios.

## Comandos básicos del shell

  - cat archivos  
    Muestra los archivos en pantalla.

  - cd directorio  
    Cambia al directorio.

  - cp archivos dest  
    Copia archivos y directorios.

  - echo cadena  
    Muestra una cadena en pantalla.

  - gzip, bzip2, xz \[`-d`\] archivos  
    Comprime/descomp
    rime archivos.

  - pager archivos  
    Muestra los contenidos de los archivos.

  - ls \[archivos\]  
    Lista archivos.

  - mkdir nombres-directorio  
    Crea directorios.

  - mv archivo1 archivo2  
    Mueve/renombra archivos.

  - rm archivos  
    Elimina archivos.

  - rmdir dirs  
    Elimina directorios vacíos.

  - tar \[c\]\[x\]\[t\]\[z\]\[j\]\[J\] -f archivo.tar \[archivos\]  
    Crea (c), extrae (x), lista tabla de (t) archive file, *z* for `.gz`, *j* for `.bz2`, *J* for `.xz`.

  - find directorios expresiones  
    Encuentra archivos por condición como `-name nombre` o `-size +1000`, etc.

  - grep cadena-busq archivos  
    Encuentra la cadena de búsqueda en los archivos.

  - ln -s archivo liga  
    Crea un enlace simbólico a un archivo.

  - ps \[opciones\]  
    Mostrar los procesos actuales.

  - kill \[-9\] PID  
    Envía una señal a un proceso (p. ej. terminarlo). Busque el PID con `ps`.

  - su - \[usuario\]  
    Convertirse en otro usuario, por defecto en `root`.

  - sudo comando  
    Ejecuta un comando como `root` siendo un usuario normal, los permisos se especifican en `/etc/sudoers`.

  - comando `>` archivo  
    Sobreescribe el archivo con la salida del comando.

  - comando `>>` archivo  
    Agrega la salida del comando al archivo.

  - comando1 `|` comando2  
    Envía la salida del comando 1 como entrada para el comando 2.

  - comando `<` archivo  
    Usa al archivo como entrada para el comando.

## APT

  - apt update  
    Actualiza la lista de paquetes de los repositorios listados en `/etc/apt/sources.list`. Ejecútelo si modificó este archivo o si cree que hay actualizaciones.

  - apt search cadena-busq  
    Busca paquetes y descripciones que contengan cadena-de-búsqueda.

  - apt list -a nombre-paquete  
    Muestra versiones y areas de archivo de paquetes disponibles.

  - apt show -a nombre-paquete  
    Muestra información del paquete incluyendo descripción.

  - apt install nombre-paquetes  
    Instala paquetes de los repositorios, satisfaciendo las dependencias.

  - apt upgrade  
    Instala las últimas versiones de todos los paquetes actualmente instalados.

  - apt full-upgrade  
    Como `apt upgrade`, pero con una resolución de conflictos mejorada.

  - apt remove nombre-paquetes  
    Remove packages.

  - apt autoremove  
    Elimina los paquetes de los que no dependa ningún otro paquete.

  - apt depends nombre-paquete  
    Muestra todos los paquetes requeridos por el indicado.

  - apt rdepends nombre-paquete  
    Muestra todos los paquetes que requieren al indicado.

  - apt-file update  
    Actualiza los contenidos de los repositorios de paquetes, ver `apt update`.

  - apt-file search nombre-archivo  
    Busca a qué paquete corresponde un determinado archivo.

  - apt-file list nombre-paquete  
    Muestra los contenidos de un paquete.

  - aptitude  
    Interfaz de consola para APT, requiere `aptitude`.

  - synaptic  
    Interfaz GUI para APT, requiere `synaptic`.

## Dpkg

  - dpkg -l \[nombres\]  
    Muestra paquetes.

  - dpkg -I paq.deb  
    Muestra información respecto a un paquete.

  - dpkg -c paq.deb  
    Muestra los contenidos del archivo de paquete.

  - dpkg -S archivo  
    Muestra a qué paquete pertenece un archivo.

  - dpkg -i paq.deb  
    Instala los paquetes.

  - dpkg -V \[package-names\]  
    Audit check sums of installed packages.

  - dpkg-divert \[opciones\] archivo  
    Sustituye la versión de archivo de un paquete.

  - dpkg `--compare-versions` v1 gt v2  
    Compare version numbers; view results with `echo $?`.

  - dpkg-query -W         `--showformat`=formato  
    Consulta los paquetes instalados, usando el formato indicado:
    
        '${Package}
    
        ${Version}
    
        ${Installed-Size}\n'

  - dpkg `--get-selections` \> archivo  
    Graba la selección de paquetes en un archivo.

  - dpkg `--set-selections` \< archivo  
    Lee de un archivo la selección de paquetes.

## La Red

  - `/etc/network/interfaces`  
    Interface configuration (if not controlled via network-manager).

  - if \[up\]\[down\] interfaz  
    Start, stop network interfaces according to the file above.

  - ip  
    Muestra y manipula las interfaces de red y el encaminamiento, requiere de `iproute2`

  - ssh -X usuario@sistema  
    Abre sesión en un sistema remoto.

  - scp archivos usuario@sistema: ruta  
    Copia archivos de/a otro sistema.

## Créditos y licencia

Copyright © 2004, 2010 W. Martin Borgert; 2016, 2019, 2023 Holger Wansing.

Traducción al español: © 2005, 2008, 2010 Gunnar Wolf; 2014 Javier Fernández-Sanguino; 2016 Octavio Alvarez.

Este documento puede ser utilizado según los términos de la Licencia Pública General de GNU (GPL) versión 3 o posterior. Puede encontrar el texto de la licencia en [GNU GPL](https://www.gnu.org/copyleft/gpl.html) y en `/usr/share/common-licenses/GPL-3`.
