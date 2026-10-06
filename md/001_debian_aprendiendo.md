# Aprendiendo Debian v12

Cuaderno de estudio de la [Debian Reference (version 2.100)](https://packages.debian.org/bookworm/debian-reference)
Manual de usuario de [Debian 12 (Bookworm)](https://packages.debian.org/bookworm/) 

de [Osamu Aoki](https://salsa.debian.org/osamu) (青木 修).

---
# Prefacio

## 1. Aviso

El sistema Debian es un blanco móvil (moving target): mantener la documentación al día es difícil. Este manual se escribió sobre la versión testing del momento, así que algún detalle puede llegar ya viejo cuando lo leas.

## 2. Qué es Debian

El Debian Project es una asociación de personas unidas por una causa común: crear un sistema operativo libre. Su sello: compromiso con la libertad del software (el Debian Social Contract y las DFSG), esfuerzo voluntario distribuido por internet y sin paga, gran cantidad de paquetes precompilados de alta calidad, foco en estabilidad y seguridad con actualizaciones de seguridad fáciles, upgrades suaves hacia los paquetes más nuevos del archivo testing, y soporte para muchas arquitecturas de hardware.

## 3. Sobre este documento

### 3.1. Principios rectores

Las reglas que siguió el autor: panorama general y nada de casos raros (big picture), KISS (keep it short and simple), no reinventar la rueda (apuntar a las referencias que ya existen), herramientas de consola y no gráficas (ejemplos con shell), y objetividad (datos del popcon).

### 3.2. Prerrequisitos

***Busca tu propia respuesta:***

Este documento solo da puntos de partida eficientes; las respuestas las busca uno mismo, en las fuentes primarias: el sitio https://www.debian.org, el directorio /usr/share/doc/ de tu propio sistema, Wikipedia, el Debian Administrator's Handbook (https://www.debian.org/doc/manuals/debian-handbook/) y TLDP (The Linux Documentation Project) (http://tldp.org/).

***Otras fuentes:***

Antes de ir a las fuentes de afuera conviene entender las que ya vienen dentro de tu propia máquina, porque Debian reparte la ayuda en capas y cada capa responde una pregunta distinta. Las siguientes son las primeras capas.

- The Unix style **manpage**: 
`dpkg -L package_name |grep '/man/man.*/'`

La **manpage** es la capa de referencia. Cada comando, archivo de configuración o llamada del sistema trae su página, que se abre con `man nombre`, y es lo más parecido que hay al `comando /?` de MS-DOS, pero con mucha más sustancia. Las páginas se agrupan en **secciones numeradas**: 1 comandos de usuario, 2 llamadas al sistema, 3 funciones de biblioteca, 4 dispositivos, 5 formatos de archivo y configuración, 6 juegos, 7 miscelánea, 8 administración del sistema, 9 el kernel. Por eso existen `passwd` (el comando, sección 1) y `passwd` (el archivo `/etc/passwd`, sección 5): `man passwd` abre la primera, `man 5 passwd` la segunda. Y si no sabes cómo se llama lo que buscas, `man -k palabra` (o `apropos palabra`) busca la palabra en los títulos y descripciones de todas las páginas instaladas; `man -f nombre` (o `whatis`) te dice en una línea qué es. Lo que la cita muestra, `dpkg -L paquete | grep '/man/man.*/'`, es otra cosa: pregunta qué páginas de manual trae un paquete concreto, ya instalado, y sirve cuando instalaste algo y no sabes qué comandos aportó.

- The GNU style **info page**: 
`dpkg -L package_name |grep '/info/'`

La **info page** es la capa de manual completo, nacida del proyecto GNU. Donde una manpage es una hoja de consulta que se lee de arriba abajo, `info` es un libro hipertextual dividido en **nodos** con enlaces: se entra con `info coreutils`, se salta entre nodos con `n` (siguiente), `p` (anterior) y `u` (subir un nivel), se sigue un enlace con Enter y se sale con `q`; `?` muestra todas las teclas. Si la manpage es el diccionario, el info es el tratado, con tutorial, ejemplos y explicaciones. Muchos comandos GNU tienen una manpage resumida que dice casi al final «la documentación completa está en info». Igual que antes, `dpkg -L paquete | grep '/info/'` lista las páginas info que trae un paquete, y no todos las traen.

- The bug report: [http://bugs.debian.org/*package\_name*](https://bugs.debian.org/)

El **informe de errores** ya no es documentación como tal sino memoria colectiva. Cada paquete de Debian tiene su página en el sistema de bugs, y ahí se ve lo que otras personas encontraron roto, lo que está en estudio y a veces la solución que la manpage no menciona.

- The Debian Wiki <https://wiki.debian.org/> para temas cambiantes y específicos.

La **wiki de Debian** es la capa móvil: lo que cambia rápido o depende de la versión (instalar firmware, configurar la red, trucos de escritorio). Escrita por usuarios, así que se lee con criterio y mirando la fecha, pero se actualiza más rápido que cualquier manual impreso.

- Help.

**`--help`**: casi todo comando acepta `comando --help` y devuelve un resumen de opciones en pocas líneas. Es la memoria rápida: no explica, solo recuerda.

- Share Docs.

**`/usr/share/doc/`**, la carpeta donde cada paquete deja lo suyo: `README.Debian` (lo que Debian cambió respecto al original), el `changelog.Debian.gz`, el `copyright`, y a veces ejemplos de configuración. Aquí es donde se mira cuando el manual no alcanza.

***En resumen:*** 

`--help` es la memoria rápida, `man` es la referencia, `info` es el manual completo, `/usr/share/doc` es lo específico de Debian, y los bugs y la wiki son lo que la gente aprendió después de que el manual se escribió. Se consulta en ese orden, de lo más rápido a lo más amplio.

### 3.3. Convenciones

Convención de los ejemplos: `#` delante del comando significa que se ejecuta en la cuenta root; `$` significa cuenta de usuario normal.

---

# Tarjeta de referencia 

La **refcard** es la tarjeta de referencia del Debian Documentation Project (DDP): una hoja con seis columnas, tres por cara, hecha para imprimir y plegar. La tarjeta deja a mano los comandos para consultar ayuda, configurar el sistema y manejar paquetes.

![Diagrama de plegado de la tarjeta de referencia de Debian](img/2-refcard.png)

Se puede ver la versión de Osmancito de la Refcard aquí:
[Osmancito Refcard v.12](https://github.com/osmancitov/taller/blob/main/md/002_debian-refcard-bookworm.md)

---

# De dónde salen las cosas

Un sistema Debian no viene con un único manual sino con una red de fuentes, y saber cuál abrir ahorra mucho tiempo. Estas son las principales, cada una con su oficio.

Para **conseguir el sistema en sí** (o uno anterior) está el [archivo de imágenes ISO de Debian](https://cdimage.debian.org/cdimage/archive/): ahí quedan guardadas todas las versiones, útil cuando uno quiere instalar justo Bookworm y no la última versión.

La puerta principal a la documentación es la página de [manuales para usuarios de Debian](https://www.debian.org/doc/user-manuals). Es el índice de todo el proyecto: la FAQ de GNU/Linux, la Guía de instalación, las Notas de la versión, la Tarjeta de referencia, el Administrator's Handbook, la Debian Reference (el manual de este cuaderno), el manual de Aptitude, la guía de APT, la FAQ de Java y hasta una guía para radioaficionados. Cuando no se sabe por dónde empezar, se empieza aquí.

La tarjeta de referencia tiene su propia casa: el [repositorio refcard en Salsa](https://salsa.debian.org/ddp-team/refcard), donde viven su texto fuente y los archivos para imprimirla.

Para el entorno de escritorio GNOME, la [ayuda](https://help.gnome.org/index.html) es el manual de lo que se ve y se hace con el ratón, la otra cara de lo que aquí se estudia desde la consola.

Y para saber **qué hay disponible**, el [buscador de paquetes de Debian Bookworm](https://packages.debian.org/bookworm/) dice qué paquetes existen en esta versión, qué contienen y de qué dependen. Como ejemplo, la página del paquete [debian-reference](https://packages.debian.org/bookworm/debian-reference) muestra de dónde sale el manual que se estudia aquí, con su versión 2.100 de Bookworm.
