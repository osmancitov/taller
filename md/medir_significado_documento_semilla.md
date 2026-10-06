# Medir el significado: peso, sustancia y hueso

Destilería Osmancito · Taller · documento semilla · 5 de octubre de 2026.

## La pregunta

¿Se puede medir el significado de cada frase de un corpus y reconocer dónde están su peso, su sustancia y su hueso?

Este cuaderno prepara un experimento, no anuncia una teoría resuelta. Su propósito es dar la misma semilla a varios motores, recoger propuestas independientes y llevarlas al texto. Una tesis que termine en un ensayo hermoso no alcanza: debe dejar una medida que se pueda calcular, una predicción y una manera de demostrar que estaba equivocada.

El resultado buscado no es una nota de calidad literaria ni un ranking de escritores. Es un instrumento que ayude a decidir qué conservar, qué comprimir y qué se rompe cuando se quita demasiado.

## De dónde viene

La Destilería parte de una hipótesis: un destilado no es un resumen, sino una semilla. Se quita hasta que quitar un poco más impida que el texto despliegue su árbol en otro lector. A eso se llama germinar. Todavía falta convertir esa imagen en una prueba observable.

La cadena CPL → BCPL → B → C ha servido aquí como analogía de reducción y transformación, no como demostración de que la literatura obedezca la misma ley. La búsqueda es la de una "ecuación perdida": qué relaciones hacen funcionar una obra y qué forma mínima podría conservarlas. La semilla no tendría que guardar cada detalle; tendría que conservar lo que permite volver a producir el movimiento del texto.

El instrumento emergente, llamado `trajes_lat` por trazar-ejes-espacio-latente, ensayó otro camino: dejar que los ejes aparezcan al medir los pasajes, en vez de imponer una lista de instrumentos. La imagen es una radiografía: encontrar los huesos bajo el traje de carne. El humano bautiza los ejes. Un algoritmo que agrupa pasajes no demuestra por ello qué significan sus grupos.

Los [cuatro criterios para mapear un corpus](criterios_para_mapear_un_corpus.md) reúnen lo que se tiene: rareza interna, eco del autor, similitud vectorial y enlaces estructurales. Allí están su estado y sus límites. Este documento no los sustituye ni los repite enteros; les pide un paso más.

## Regla del mundo cerrado

"Afuera del corpus no existe."

Las frecuencias se calculan dentro de cada obra. No entran los subrayados del lector, la fama del autor, las reseñas ni los resúmenes que un motor recuerde. Cada afirmación sobre el texto debe poder anclarse en el texto recibido.

Eso no vuelve endógeno a cualquier instrumento. Un modelo preentrenado, un lematizador y hasta las reglas de un stemmer traen infraestructura de afuera. Cada propuesta debe declarar qué toma del corpus y qué conocimiento externo incorpora. Contar frecuencias internas y juzgar con un modelo entrenado fuera no son la misma operación. El corpus puede ser la única evidencia de una afirmación sin ser la única fuente del instrumento que la produce.

No se permite ocultar esa diferencia bajo la palabra "semántico". Para la comparación habrá que separar medidas estrictamente internas de medidas asistidas por modelos.

## Lo que ya se midió

El banco inicial es el original de *Macbeth*, no un recuento, y *El libro de arena*. No son textos intercambiables: teatro inglés y prosa española difieren en lengua, forma y segmentación.

El boot de unigrama asigna a una palabra el peso `-log2(frecuencia / total de tokens)`. La entropía es el promedio de esos pesos. Es sorpresa según la distribución del propio corpus, no significado.

La primera medición de Macbeth contó etiquetas de hablante: 17.973 tokens. El boot 2.0 las quitó y dejó 17.157. Borges mantuvo 24.822. Por eso la comparación honesta del recorte es entre el texto limpio sin stemmer y ese mismo texto con stemmer, no entre dos preparaciones distintas.

### Boot 2.0, ejecutado el 5 de octubre de 2026

| Medida | Macbeth | El libro de arena |
| --- | ---: | ---: |
| Tokens del texto limpio | 17.157 | 24.822 |
| Entropía sin stemming, bits/token | 9,378505 | 9,493503 |
| Entropía con stemming, bits/token | 9,161285 | 9,003996 |
| Descenso de entropía, aproximado | 0,217220 | 0,489507 |
| Hapax tras el recorte, porcentaje de tipos | 52,4 % | 51,8 % |
| Relieve informado tras el recorte | 1,739 | 1,663 |

Los hapax son tipos que aparecen una sola vez. Los porcentajes anteriores al recorte rondaban 59,5 % y 65,6 %; esa comparación exige conservar la columna y la preparación de origen. El relieve histórico se había informado como 1,78 y 1,60. No debe tratarse toda la variación como efecto aislado del stemmer, porque Macbeth también se limpió.

En esta pareja de corpus, el descenso de entropía de Borges fue más del doble del de Macbeth. "El español se dejó recortar más del doble" describe este resultado; no es una ley sobre todas las obras de esas lenguas. Es compatible con una contribución de la flexión a la rareza, pero no demuestra que cada tipo fusionado fuera una conjugación sobrante.

El procedimiento usó `snowballstemmer==3.1.1`. Stemming es poda, no lematización: recorta formas mediante reglas y no promete infinitivos ni familias lingüísticas perfectas. Una raíz cortada no es una palabra comprendida.

La cercanía de los hapax y del relieve no prueba que ambos autores tengan el mismo significado, intensidad o calidad. El relieve del informe describe la variación de rareza en ventanas de 200 tokens; hay que conservar su fórmula exacta al reproducirlo. Una ventana igual en tokens tampoco garantiza una unidad literaria comparable.

La lección para esta tesis es concreta: una medida puede cambiar mucho al cambiar la representación. Antes de llamar "sustancia" a un pico hay que averiguar cuánto viene de morfología, longitud, nombres propios, formato o limpieza.

## Tres nombres provisionales, no tres verdades

| Eje de trabajo | Pregunta operativa propuesta | Confusión que debe evitarse |
| --- | --- | --- |
| Peso | ¿Cuánto cambia una propiedad declarada del corpus si se retira esta frase? | Confundir rareza o longitud con importancia. |
| Sustancia | ¿Qué relaciones o contenido conserva esta frase que no quedan cubiertos por otras? | Confundir novedad con necesidad; una repetición puede sostener el texto. |
| Hueso | ¿Qué pérdida ya no puede compensarse al reducir el texto, según una prueba de conservación fijada antes? | Llamar esencia a la preferencia del juez. |

Estas son preguntas para diseñar medidas, no definiciones finales. Puede que el significado necesite un vector y no un número. Una frase puede ser común en vocabulario, decisiva en estructura y redundante en información. No se sumarán esos ejes con pesos elegidos después de ver el resultado.

La coincidencia de mapas diferentes señala un candidato a hueso. No lo certifica. Dos instrumentos pueden coincidir porque tienen el mismo sesgo.

## La cascada: qué hay publicado y qué falta fijar

[Trazar](trazar.md) levanta el mapa del corpus. [Escalar](escalar.md) toma una copa de un quinto del resto vigente, conserva su procedencia y devuelve el resto. La imagen que guía la investigación es acercarse a una semilla mediante escalones separados: un quinto, luego otro nivel de reducción, hasta que no pueda decirse algo sin destruirlo.

Hay una ambigüedad que no debe pasar al experimento. El encabezado de Escalar anuncia `1/5, 1/25, 1/125...`, pero su paso 4 define el siguiente resto como el texto anterior menos lo tomado. Extraer un quinto de ese resto no equivale a comprimir la copa anterior a un quinto. Este cuaderno no corrige el protocolo por su cuenta.

Antes de medir supervivencia hay que fijar una variante:

- **Extracción del resto:** cada copa toma materia aún no seleccionada. Se estudia en qué vuelta entra cada frase y qué función conserva la copa.
- **Compresión sucesiva:** cada nueva copa reduce la copa anterior. Se estudia qué contenido persiste a través de los niveles. Esta es una variante experimental propuesta, no una ejecución ya realizada.

La prueba central siguiente se refiere a compresión sucesiva. No se pueden mezclar sus resultados con los de extracción. La cascada aún no ha validado una medida de significado.

## Prueba central: predecir antes de destilar

Hipótesis de trabajo: una buena medida de sustancia debería predecir qué contenido de las frases sobrevive a la cascada de quintos. La semilla puntúa alto y la paja bajo. Si no predice mejor que controles baratos, no ha ganado su nombre.

"Sobrevivir" no significa conservar las mismas palabras. Una copa puede reescribir, fusionar varias frases o repartir una función entre pasajes. Hay que guardar una tabla de procedencia desde cada frase original hasta su realización en cada copa. También puede haber sustancia distribuida: dos frases juntas podrían cargar algo que ninguna expresa sola.

### Diseño mínimo propuesto

1. Fijar los archivos y sus SHA-256, la limpieza, la tokenización y la segmentación. Dar identificadores estables a las frases. En teatro, declarar cómo se tratan versos, parlamentos y acotaciones; en Borges, diálogos y párrafos. Conservar una tabla que permita volver al original.
2. Registrar las medidas, los controles, la predicción y el criterio de fracaso antes de generar las copas. No ajustar el instrumento usando las mismas copas con las que se lo evalúa.
3. Separar las funciones de medir, destilar y evaluar conservación. El destilador no debe recibir el ranking cuya capacidad predictiva se prueba: si corta obedeciéndolo, el resultado sería circular.
4. Generar copas con tamaños y tolerancias declarados. Guardar motor, versión identificable, parámetros, fecha, entradas y salidas completas. Repetir con otros motores; una sola destilación expresa también las preferencias de su autor mecánico.
5. Comparar contra azar, longitud, posición en el texto, rareza unigrama y repetición. Probar ablaciones: retirar cada componente para ver si aporta algo.
6. Evaluar en material no usado para ajustar la medida. Declarar si se separan escenas, cuentos u obras completas y qué dependencias quedan entre ellos. Probar después en el otro corpus sin retocar la regla para salvarla.

Cada motor debe proponer cómo resolver la tabla de supervivencia sin convertir a otro modelo en árbitro infalible. La revisión humana puede verificar relaciones, citas y pérdidas; tampoco debe presentarse como una medición sin criterio declarado.

Una segunda prueba propuesta es la ablación: retirar frases o conjuntos de frases que puntúan alto y bajo, con presupuestos comparables, y comprobar qué relaciones se pierden. Esto ayudaría a distinguir "el destilador la conservó" de "la obra la necesitaba". Germinar requiere una tarea observable, por ejemplo conservar relaciones causales o reconstruir una trayectoria con evidencia textual. La tarea elegida mide esa capacidad, no todo el significado.

## Comando común para cada motor

Desarrolla una propuesta de investigación a partir de este documento y de los corpus suministrados. Trabaja de forma independiente, sin leer las propuestas de los demás motores antes de cerrar la tuya.

No prometas medir "el significado" sin decir qué operación y qué propiedad observas. Propón medidas de peso, sustancia y hueso, o explica con precisión por qué esos ejes deben cambiar. El humano pondrá los nombres finales.

Entrega un capítulo con estas partes:

1. **Hipótesis y alcance.** Qué aspecto del significado intentas medir y cuál queda fuera. Distingue hechos del corpus, hipótesis y decisiones de diseño.
2. **Medidas ejecutables.** Para cada una: unidad, entradas, fórmula o algoritmo, salida, normalización, costo y dependencias externas. Incluye pseudocódigo suficiente para implementarla y un ejemplo pequeño que pueda calcularse a mano.
3. **Predicciones falsables.** Al menos una por medida sobre Macbeth y/o El libro de arena. Declara qué resultado la refutaría, frente a qué control y en qué material no usado para ajustar. El umbral propuesto debe fijarse antes de la prueba y justificarse, no inventarse como resultado.
4. **Pruebas de engaño.** Cómo responde a palabras raras añadidas, conjugaciones, nombres, repetición, cambio de longitud, paráfrasis y supresión de una relación decisiva. Qué fracaso revelaría cada prueba.
5. **Cascada y germinación.** Cómo medirías supervivencia semántica, procedencia y pérdidas, con la variante de cascada explícita. Cómo evitarías el círculo entre juez y destilador.
6. **Plan mínimo y límites.** El experimento más barato que permita descartar tu propuesta. Qué falta, qué no sabes y qué hallazgo te haría abandonarla.

Si no recibes los corpus completos, no inventes frases, puntuaciones ni resultados. Presenta solo el diseño y señala los datos faltantes. Un enlace no significa que se haya leído su contenido: el paquete de ejecución debe incluir este documento, los tres cuadernos enlazados y los archivos del corpus, con sus huellas y versiones.

## Cómo se compararán las tesis

Se comparará lo ejecutable, no la elocuencia. Una propuesta que necesita datos externos debe decirlo; una que no produce predicciones todavía es una intuición. Se guardarán las versiones originales antes de cruzarlas, para no fabricar convergencia mediante correcciones mutuas.

Las IA comparten entrenamiento y moda. Su convergencia no prueba verdad ni independencia de sus errores. El acuerdo entre motores solo da una pista para probar. La prueba vendrá de controles, predicciones fuera de muestra y pérdidas verificables en el corpus.

Para medir conviene un instrumento aburrido: versiones fijas, reglas visibles y resultados auditables. Un modelo puede servir para proponer o destilar; si también mide, sus cambios y variaciones pasan a ser parte de la incertidumbre. Temperatura cero no equivale a repetibilidad bit a bit. Guardar una salida permite auditar lo ocurrido, no garantiza que una llamada futura la repita.

## Criterio de éxito

No hace falta que aparezca una teoría universal. Bastaría una medida nueva que supere un control simple, anticipe una pérdida real y mantenga esa ventaja fuera del texto con el que se diseñó. Si ninguna lo consigue, habrá que conservar el resultado negativo y volver al instrumento.

El tesoro no es que una máquina diga dónde está el hueso. Es poder señalar qué observó, por qué lo llama hueso y en qué prueba dejaría de llamarlo así.

## Fuentes y estado

- [Cuatro criterios para mapear un corpus](criterios_para_mapear_un_corpus.md): registro de criterios y límites, 5 de octubre de 2026. Su "siguiente paso" describe el estado anterior al boot 2.0.
- [Trazar](trazar.md) y [Escalar](escalar.md): protocolos vigentes del Taller; la ambigüedad de la cascada queda señalada arriba.
- [Destilería Osmancito](https://github.com/osmancitov/destileria): proyecto y protocolos de destilación.
- Bitácora de trabajo del 4 y 5 de octubre de 2026: duelo de mapas, regla endógena y boot de unigrama. Las entropías y los conteos limpios del boot 2.0 proceden de la salida ejecutada en Debiancito; hapax y relieve, de la lectura del informe de esa corrida. Son resultados informados, no una nueva reproducción realizada para este cuaderno.
- Hipótesis de la semilla, ecuación perdida e instrumento emergente: antecedentes de trabajo de la Destilería. Se usan como punto de partida, no como conclusiones demostradas.

Estado: documento semilla. Ningún capítulo de motor ni experimento nuevo se ha ejecutado como parte de su redacción.
