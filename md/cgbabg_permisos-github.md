16 de octubre de 2026

# Los permisos de GitHub

![Un llavero de hierro con muchas llaves de distintos tamaños sobre una mesa de madera de taller, junto a una puerta entornada, al estilo de Hans Holbein el Joven](../img/cgbabg_permisos-github.jpg)

Un token de acceso personal es una llave: un texto secreto que permite a un programa hablar con GitHub en nombre de una persona. La versión fina (fine-grained) no abre todo: abre solo los repositorios elegidos y solo con los permisos marcados. La llave nueva de la casa cubre todos los repositorios y trae 39 permisos. Casi todos son de lectura y escritura; tres son de solo lectura.

La lista sirve también como mapa de lo que la API de GitHub puede hacer: cada permiso es una puerta que se puede abrir o dejar cerrada. Los nombres van en inglés, como los muestra GitHub.

## El contenido

- **Contents**: el contenido de los repositorios: archivos, commits, ramas, descargas, releases y merges. La puerta principal: sin ella no se sube nada.
- **Commit statuses**: el estado de cada commit, como si pasó o no las pruebas.
- **Custom properties**: las propiedades personalizadas que el dueño define para sus repositorios.
- **Metadata**: los datos básicos: buscar repositorios, listar colaboradores. Viene siempre marcada, es obligatoria y de solo lectura.
- **Repository license policy**: la política de licencias del repositorio. Solo lectura.
- **Repository creation**: crear repositorios nuevos.
- **Administration**: crear, borrar y ajustar repositorios, con sus equipos y colaboradores.

## La colaboración

- **Issues**: los issues y sus comentarios, responsables, etiquetas e hitos. La lista de tareas pegada al proyecto.
- **Pull requests**: las pull requests con sus comentarios, etiquetas, hitos y merges.
- **Discussions**: las discusiones del repositorio, con sus comentarios y etiquetas. Un foro dentro del proyecto.
- **Merge queues**: la cola de integración: el orden en que entran las pull requests.

## Las acciones automáticas

- **Actions**: los flujos de trabajo de GitHub Actions, sus ejecuciones y sus artefactos.
- **Workflows**: actualizar los archivos que definen esos flujos.
- **Variables** y **Secrets**: las variables y los secretos que usan las Actions de un repositorio.
- **Environments**: los entornos de despliegue, como pruebas o producción, y sus reglas.
- **Deployments**: los despliegues y sus estados.
- **Artifact metadata**: los metadatos de los artefactos que dejan las ejecuciones.
- **Webhooks**: los ganchos que avisan a otro servicio cuando algo pasa en el repositorio.

## Codespaces

Los Codespaces son entornos de desarrollo completos que corren en la nube de GitHub.

- **Codespaces**: crearlos, editarlos, borrarlos y listarlos.
- **Codespaces lifecycle admin**: arrancarlos y pararlos.
- **Codespaces metadata**: sus metadatos, como el devcontainer y el tipo de máquina. Solo lectura.
- **Codespaces secrets**: limitar a qué repositorios llegan los secretos de usuario de Codespaces.

## La seguridad

- **Dependabot alerts**: las alertas de Dependabot sobre dependencias vulnerables.
- **Dependabot secrets**: los secretos que usa Dependabot.
- **Code scanning alerts**: las alertas del análisis automático del código.
- **Code quality**: los datos de calidad del código.
- **Secret scanning alerts**: las alertas que saltan cuando un secreto aparece en el código.
- **Secret scanning alert dismissal requests**: las peticiones para descartar esas alertas.
- **Secret scanning push protection bypass requests**: las peticiones para saltarse el bloqueo que impide subir un secreto.
- **Repository security advisories**: los avisos de seguridad del repositorio.
- **License compliance alerts**: las alertas de cumplimiento de licencias.
- **Attestations**: las atestaciones, pruebas firmadas de que un artefacto salió de donde dice.

## Copilot y las apps

- **Copilot agent settings**: los ajustes del agente de Copilot en la nube.
- **Agent tasks**: ver, crear y manejar las tareas del agente en un repositorio.
- **Agent secrets** y **Agent variables**: los secretos y las variables del agente.
- **GitHub App installation repository access**: decidir a qué repositorios accede cada GitHub App instalada.

## Pages

- **Pages**: el estado, la configuración y las compilaciones de GitHub Pages, y lanzar compilaciones nuevas. El permiso que publica este sitio.

## Las que usa la casa

Hasta hoy la llave anterior abría una sola: Contents, con la que se suben los cuadernos, las imágenes y las páginas de todas las salas. La llave nueva suma las que hacían falta y se resolvían a mano en la web: Pages, para activar y vigilar la publicación de cada sala; Administration, para los ajustes; y Repository creation, para abrir salas nuevas.

## Las que pueden interesar

- **Webhooks**: que GitHub avise solo cuando algo cambia, en vez de ir a mirar.
- **Issues**: llevar las tareas del hotel pegadas al código.
- **Workflows** y **Actions**: que GitHub ejecute solo las tareas repetidas, como publicar cada mañana.
- **Dependabot alerts**: un vigilante de las piezas ajenas que usa un proyecto.

Osmancito, con la asistencia de Instinct
