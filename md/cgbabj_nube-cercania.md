13 de octubre de 2026

# La nube de cercanía

Una nube de cercanía pone cada frase de una obra como un punto en el espacio. El color dice qué tan cerca está esa frase del centro de la obra: rojo, cerca; azul, lejos. Se puede girar, acercar, mover, y tocar un punto para leer la frase.

Esta es la plantilla. Para otra obra solo cambian la obra, los motores y las secciones. Todo lo demás se copia igual.

La página de referencia es la de *El Libro de Arena*, de Borges: [Nube en 3D de El Libro de Arena](https://osmancitov.github.io/taller/html/cgbabe_nube-arena-3d.html). Es un solo archivo, sin servidor.

## Qué hace falta

1. La obra partida en frases. Cada frase lleva un ID, su texto y la sección a la que pertenece. En Arena: 1.853 frases con ID BD0005 en adelante, repartidas en 13 cuentos y un epílogo.
2. Un vector por frase y por motor. Un motor de embeddings es el programa que convierte una frase en una lista de números. En Arena son cuatro: Nemotron, Cohere Embed v4, Gemini Embedding 2 y Liquid LFM 2.5.

## Paso 1: vectores de longitud uno

Cada vector se divide por su longitud. Así todos miden uno y solo importa hacia dónde apuntan.

## Paso 2: dónde cae cada punto

Cada motor tiene su propia nube. Se reducen los vectores a 50 ejes con PCA, y esos 50 a 3 con UMAP:

```python
Z = PCA(50, random_state=42).fit_transform(X)
U = umap.UMAP(n_components=3, n_neighbors=15, min_dist=0.1,
              metric='euclidean', random_state=42).fit_transform(Z)
U -= U.mean(0)          # centrar
U /= np.abs(U).max()    # el punto más lejano queda en 1
xyz = np.round(U * 1000).astype(int)
```

Los tres ejes no significan nada por sí solos. Solo importa que frases parecidas queden cerca.

## Paso 3: la cercanía

El centro es el promedio de los vectores de todas las frases de la obra, siempre el de la obra entera, también cuando la página muestra una sola sección. Cada frase se compara con ese centro:

```python
centro = U.mean(0)              # U: vectores de longitud uno, una fila por frase
puntaje = U @ centro
n = (puntaje - puntaje.min()) / (puntaje.max() - puntaje.min())
n = np.rint(n * 1000).astype(int)
```

La distancia que muestra la página es 1 menos n, con tres decimales. Cero es la frase más cercana al centro; uno, la más lejana. Se normaliza por motor, así que sirve para comparar frases dentro de un mismo motor, no entre motores.

Comprobado con Nemotron sobre los vectores guardados: el cálculo da los mismos valores que la página, salvo 9 frases de 1.853 que difieren en una milésima.

## Paso 4: los datos de la página

Dentro de la página hay un bloque `<script id="data" type="application/json">` con:

- `cuentos`: los nombres de las secciones, en orden.
- `s`: para cada frase, el número de su sección.
- `t`: el texto de cada frase.
- `ids`: el ID de cada frase.
- `m`: un bloque por motor, con `name`, `xyz` (tres enteros por frase) y `n` (la cercanía, de 0 a 1000).

Antes de publicar se revisa que `n` tenga un 0 y un 1000 en cada motor, que `xyz` llegue a 1000 en valor absoluto y que todas las listas tengan una entrada por frase.

## Paso 5: la página

La página no se reescribe: se copia la de Arena y se cambia el bloque de datos y los textos. Lo que trae, y no se toca:

- **Arriba:** la fecha, el título, el dibujo, el autor y el número de frases. Después una fila con un botón por motor, y otra con «Libro entero» y «Un cuento». Con «Un cuento» aparece un selector con las secciones elegibles. El epílogo se ve en el libro, como rombos, pero no se elige solo.
- **La nube:** vista en 3D con ejes tenues, perspectiva, giro con el dedo o el ratón, pellizco o rueda para el zoom (de 0,5 a 5,2 veces), botón ✥ para mover la vista, ⟲ para volver al principio y ↻ para que gire sola. Cada punto tiene el mismo tamaño en el libro y en una sección; el seleccionado se ve más grande y con un anillo blanco.
- **El color:** un degradado continuo de 0 a 1 con estos extremos y paradas. No hay blanco ni negro.

| Distancia | Color |
|---|---|
| 0 | rojo (215, 38, 61) |
| 0,12 | rojo anaranjado (255, 90, 60) |
| 0,24 | naranja (255, 155, 58) |
| 0,36 | amarillo (230, 224, 74) |
| 0,48 | verde (111, 224, 122) |
| 0,62 | turquesa (47, 208, 208) |
| 0,78 | azul (47, 140, 240) |
| 1 | azul oscuro (58, 79, 214) |

- **Debajo de la nube:** la barra de color con «0 · cerca del centro» y «1 · lejos del centro», y el texto de ayuda.
- **El panel de la frase,** de arriba abajo: «frase N de M · ID» con el botón de cerrar; la fila «En el cuento» con ⇤ ‹ › ⇥ (primera, anterior, siguiente, última); la fila «Por cercanía» con ⇈ ↑ ↓ ⇊ (la más cercana, una más cercana, una más lejana, la más lejana); la línea «puesto r de M · distancia d»; el título de la sección; y el texto. Los botones van siempre arriba y el texto debajo, para que no se muevan cuando la frase ocupa más líneas en el teléfono.
- **El puesto** ordena de la más cercana a la más lejana entre las frases que se ven: todo el libro, o la sección elegida. Si dos empatan, va primero la que aparece antes en la obra.
- **La dirección** guarda el estado: `#f<frase>&<motor>&t<sección>`, para compartir un punto exacto.

## Cambiar de obra

Se cambian cuatro cosas:

1. El bloque de datos, con las frases, los IDs, las secciones y los motores de la nueva obra. La lista de motores puede ser más corta o más larga; la fila de botones se arma sola.
2. Los textos: título, autor, fecha, número de frases y la descripción.
3. La palabra «cuento»: según la obra será acto, capítulo o escena. Aparece en «Un cuento», «En el cuento» y en las etiquetas de los botones.
4. El epílogo: si la obra no tiene una sección aparte como esa, no se pone.

La imagen que se comparte al enviar el enlace (`og:image`) es un dibujo propio de la página, también se coloca arriba, después del título: JPG al 80 %, 1280 por 640.

## Antes de publicar

Se abre la página publicada, no el archivo local, con el ancho de un teléfono, 390 píxeles:

- Nada se sale de la pantalla.
- Con la frase más corta y con la más larga de una sección, los botones quedan en el mismo lugar.
- Los puntos miden lo mismo en el libro y en una sección, en todos los motores.
- Se ven los extremos del color, rojo en 0 y azul en 1, y los intermedios.
- Un punto de cada extremo del puesto da la distancia esperada: 0,000 y 1,000.
- La consola no muestra errores.

Osmancito, con la asistencia de Instinct
