# Cuatro criterios para mapear un corpus

*Destilería Osmancito · Taller · cuaderno de registro*

Cuaderno de registro · 5 de octubre de 2026.

## Para qué sirve

Antes de destilar un texto hay que saber dónde pesa. Un mapa del corpus dice qué partes sostienen a las demás, y de ese mapa depende lo que se conserve al destilar. [Trazar](005_trazar.md) y [Escalar](006_escalar.md) son los protocolos que lo usan.

Estos cuatro criterios son lo mejor que se ha encontrado hasta ahora para llevar la destilación a un nivel nuevo. Se pensaron entre el 4 y el 5 de octubre de 2026, midiendo *Macbeth* de Shakespeare (el original, no su recuento) y *El libro de arena* de Borges. Este cuaderno los deja anotados con su estado y sus límites, para que no se pierdan.

Regla común: el corpus se mide con sus propias palabras. Lo que queda fuera del texto no cuenta.

| Criterio | Qué mira | Estado |
|---|---|---|
| 1. Sismograma shannoniano | rareza de cada palabra dentro del corpus | hecho |
| 2. Eco del autor | frases que el texto repite y replantea | pendiente |
| 3. Similitud vectorial | cercanía de sentido entre partes, según modelos | hecho, con reservas |
| 4. Enlaces estructurales | personajes que coinciden, ecos dramáticos | pendiente |

## 1. Sismograma shannoniano

**Qué mide.** El peso de cada palabra como sorpresa: cuanto menos frecuente es dentro del propio corpus, más información lleva, según la idea de Claude Shannon. Se parte del unigrama (la palabra suelta), sin tablas de frecuencia externas. Al trazar el peso a lo largo del texto aparecen picos y calmas, como en un sismograma. De ahí el nombre.

**Qué se hizo.** Se midieron *Macbeth* y *El libro de arena*. Cada autor se trata como un mundo aparte y los mundos se comparan por su forma.

**Límite.** Mide rareza, no sentido. Es importante, pero no lo es todo. Su punto débil tiene nombre: el tramposo erudito. Quien conjuga y palabrea puede colgarse palabras insólitas como medallas y engañar a una medida enamorada de la extrañeza. Dos formas de la misma palabra cuentan como dos rarezas.

**Siguiente paso.** Una versión lematizada (comprimir a verbo, no a conjugación) que compare *Macbeth* con Borges. Está ofrecida y sin confirmar. También queda abierta la rareza a nivel de frase: sumar el peso de las palabras o medir la sorpresa condicional de cada una dada la anterior.

## 2. Eco del autor

**Qué mide.** La centralidad por repetición. Una frase que el texto retoma y replantea es una frase que el autor considera suya. El ejemplo de *Macbeth* es «fair is foul», que vuelve transformada y se replantea sola.

**Estado.** Conceptualizado y computable, sin ejecutar. Es conteo puro sobre frases repetidas: no necesita modelos externos ni jueces. Por eso es el más alcanzable de los cuatro.

**Límite conocido.** Un eco puede ser una marca puesta a propósito por el autor, y medirlo premia esa marca. Hay que leerlo junto al criterio 4, que arrastra la misma sospecha.

## 3. Similitud vectorial

**Qué mide.** Qué tan cerca están dos partes del texto en el espacio de significado de un modelo. Se corrió un duelo de cuatro jueces: MiniLM multilingüe y multilingual-e5-large, ambos en local, y voyage-3-large y voyage-code-4, ejecutados desde la máquina Debiancito. Sobre cada grafo de cosenos se calculó PageRank.

**Resultado.** Sin grandes descubrimientos. El PageRank sobre cosenos quedó declarado farsa: en ese grafo cada nodo vota por todos los demás, y en una red así los vínculos ya no distinguen nada. Un grafo de Google funciona porque sus enlaces son escasos y decididos.

**Límite.** Las reparaciones posibles eran podar a los k vecinos más cercanos, dirigir las aristas o usar enlaces puestos por el autor. Solo la tercera apunta a algo verdadero, y es justo el criterio 4.

**Queda abierta** la idea de repetir el recorrido con voyage-4-large, sin costo.

## 4. Enlaces estructurales

**Qué mide.** Los vínculos que están en la obra: personajes que coinciden en escena, ecos dramáticos entre escenas, correspondencias que el texto establece. Es lo que se llamó «lo verdadero», porque nace del texto y no de un juez externo.

**Estado.** Pendiente. Es el más artesanal: en buena parte se hace a mano.

**Límite.** Los enlaces puestos por el autor funcionan como su propio posicionamiento. Distorsionan el peso y no son lo que se busca por sí solos.

## Lo que une a los cuatro

Ninguno basta solo. El sismograma ve la sorpresa, el eco ve la insistencia, el vector ve la vecindad y los enlaces ven la estructura. La esperanza está en el cruce: lo que pesa en varios mapas a la vez es candidato a semilla.

El tesoro máximo sería medir el significado. Los cuatro criterios son aproximaciones honestas, no esa medida. Un modelo pequeño que reprodujera el mismo sismograma sería una especie de llave, un mini-lector inspirado en Shannon.

La imagen que guía todo esto es la demi-glace: un fondo reducido hasta la mitad, al que se le va el agua y no el sabor. Destilar es lo mismo. Comprimir el texto debe intensificarlo, no empobrecerlo.

## Para seguir leyendo

- [Trazar](005_trazar.md): el protocolo que dibuja el mapa del corpus.
- [Escalar](006_escalar.md): el protocolo que usa ese mapa para destilar.
- Claude Shannon, «A Mathematical Theory of Communication», *Bell System Technical Journal*, 1948.
