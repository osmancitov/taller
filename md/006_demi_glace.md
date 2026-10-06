# La técnica del demi-glace

En cocina, reducir es quitar agua para concentrar un fondo. El demi-glace clásico parte de un fondo oscuro y una salsa española, y los deja a fuego lento durante horas. No se apura. Con la llama alta el fondo se quema o se pasa de punto, y lo perdido no vuelve. Con la llama baja, cada rato evapora un poco, y el cocinero mira, prueba y decide si sigue.

Dos gestos de oficio sostienen la receta. El primero es decantar: dejar que el agua suba y se vaya mientras el sabor se queda en el fondo de la olla. El segundo es probar: el punto no está en una hora fija, está en el momento en que otro rato de fuego ya no cambia nada.

Esa imagen sirve fuera de la cocina. Un problema grande, informático o de la vida, casi nunca cede a un solo golpe. Se aprende a quitarle lo que sobra de a poco, a mirar qué queda después de cada pasada y a parar cuando ya no sale nada más. La paciencia no es lentitud: es dar cada paso del tamaño que el material aguanta.

Este cuaderno aplica la imagen a un texto. Un destilado no es un resumen, es el mismo texto con menos agua. Lo que sobrevive se copia tal cual: el pliegue corta, no reescribe.

## Producción: de una olla a una cascada

*6 de octubre de 2026 · Macbeth, 18,057 palabras (sin la lista de personajes), `gemini-3.5-flash-lite` en capa gratuita, llamado con `curl` desde Debian.*

Se quiso llevar una obra completa a la mitad, sin tocar una palabra de lo que queda. Esto es lo que funcionó, en orden.

### La instrucción lleva presupuesto

Una sola llamada con la obra entera a la vista, y una instrucción con cifras contadas por el script antes de llamar: palabras totales, la mitad pedida y una tabla con el presupuesto de cada acto y de cada escena. Además, cuatro bloques fijos:

- **No es un resumen:** es un caldo que se reduce.
- **Agua:** repeticiones, rodeos, acotaciones de trámite.
- **Sabor:** líneas citables, imágenes fuertes, datos que la trama necesita después.
- **Reglas:** texto palabra por palabra y en el mismo orden, cada etiqueta de personaje con su texto, encabezados intactos.

Es la receta de `pliegue4.sh`.

### El compresor se queda corto

Se pidió la mitad y esa instrucción dejó 80.0% del texto: un compresor imperfecto que siempre se queda corto. En vez de endurecer la orden, se repitió igual. Cada pasada recibe la salida de la anterior, con la misma instrucción y las cifras recalculadas sobre lo que entra (`pliegue7.sh`, cinco pasadas):

| Pasada | Palabras | % del original | Lo que dejó de lo recibido |
|---|---|---|---|
| 0 | 18,057 | 100.0% | |
| 1 | 14,460 | 80.0% | 80.0% |
| 2 | | 58.3% | 72.9% |
| 3 | | 42.8% | 73.4% |
| 4 | | 38.6% | 90.2% |
| 5 | 6,961 | 38.5% | 99.7% |

La curva se aplana sola. En la pasada 5 el motor ya no encuentra agua y devuelve casi lo que recibió. Ese es el punto de la receta: cuando una pasada deja más de 90% de lo que recibió, se apaga el fuego. Nadie fijó el 38.5%; lo encontró el motor repitiendo la misma instrucción hasta que no hubo más agua.

### El termostato es una línea

La instrucción incluye un rango aceptable para el total. Esa línea es lo que acota el recorte: una variante sin ella (`pliegue8.sh`) llegó a 26.9% y dejó el Acto IV en 14%. La línea se queda.

### Lo que quedó en el caldo

Se alinearon las reducciones contra el original, palabra por palabra.

- **Textual:** 99.8% de las palabras de la cascada aparecen en el original en el mismo orden. En la salida de la corrida, 1,078 de 1,136 líneas son idénticas a una línea del original y 7 no coinciden con ninguna.
- **Con sabor:** de 57 citas famosas de la obra, la cascada conserva 49 (86%) con un texto que es 38.5% del original. Siguen en pie "Fair is foul, and foul is fair", "Is this a dagger which I see before me", "Out, damned spot!", "Tomorrow, and tomorrow, and tomorrow" y "Lay on, Macduff". Un recorte al azar a ese tamaño dejaría cerca de 38%.
- **Parejo:** por acto conserva entre 35% y 44%. Un salto único a 27% dejó el Acto IV en 14%.

### Moraleja

Un compresor imperfecto, aplicado en serie y con un termostato, llega donde ninguna instrucción sola llega. Pedir la mitad una vez dio 80%. Pedirla cinco veces, cada una sobre la salida anterior, dio 38.5% y se detuvo sin ayuda en lo que el motor considera sabor.

### Para repetirlo

Hace falta un corpus en markdown con una marca regular de sección, una llave en `./.gemini_key` con permiso `600`, y `curl`, `jq` y `awk`:

```
PASADAS=5 ./pliegue7.sh macbeth.md
```

El script guarda cada pasada en su carpeta, imprime la curva tras cada una y termina con la prueba de textualidad contra el original. Los scripts, los resultados y los informes viven en la carpeta `markdown` del Drive.
