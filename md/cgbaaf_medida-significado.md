5 de octubre de 2026

# La medida del significado

## La pregunta

¿Se puede medir el significado de cada frase de un corpus y reconocer dónde están su peso, su sustancia y su hueso?

Este cuaderno prepara un experimento: dar la misma semilla a varios motores, recoger propuestas independientes y llevarlas al texto. Una tesis que termine en un ensayo hermoso no alcanza: debe dejar una medida calculable, una predicción y una manera de demostrar que estaba equivocada. El resultado buscado no es una nota de calidad literaria: es un instrumento que ayude a decidir qué conservar, qué comprimir y qué se rompe cuando se quita demasiado.

## De dónde viene

La Destilería parte de una hipótesis: un destilado no es un resumen, sino una semilla. Se quita hasta que quitar un poco más impida que el texto despliegue su árbol en otro lector. A eso se llama germinar. Falta convertir esa imagen en una prueba observable.

La imagen de trabajo es una radiografía: hallar los huesos bajo el traje de carne. Un primer instrumento dejó que los ejes aparecieran al medir los pasajes, en vez de imponerlos; el humano los bautiza, porque un algoritmo que agrupa pasajes no demuestra qué significan sus grupos. Los [cuatro criterios para mapear un corpus](cgbaaf_criterios-corpus.md) reúnen lo que se tiene: rareza interna, eco del autor, similitud vectorial y enlaces estructurales. Este documento les pide un paso más.

## Regla del mundo cerrado

"Afuera del corpus no existe." Las frecuencias se calculan dentro de cada obra: no entran los subrayados del lector, la fama del autor ni los resúmenes que un motor recuerde. Cada afirmación sobre el texto debe poder anclarse en el texto recibido.

Eso no vuelve inocente a cualquier instrumento: un modelo preentrenado trae conocimiento de afuera. Cada propuesta debe declarar qué toma del corpus y qué incorpora de fuera, y la palabra "semántico" no puede ocultar la diferencia.

## Lo que ya se midió

El banco de pruebas es el original de *Macbeth* y *El libro de arena*: teatro inglés y prosa española. A cada palabra se le asigna un peso según su frecuencia en la obra, y la entropía es el promedio de esos pesos: sorpresa según la distribución del propio corpus, no significado.

Al recortar las palabras a sus raíces, la entropía de Borges bajó más del doble que la de Macbeth: "el español se dejó recortar más" describe este resultado, no es una ley sobre las lenguas. La lección es concreta: una medida puede cambiar mucho al cambiar la representación. Antes de llamar "sustancia" a un pico hay que averiguar cuánto viene de morfología, longitud, nombres propios o limpieza.

## Tres nombres provisionales, no tres verdades

| Eje | Pregunta operativa | Confusión que debe evitarse |
| --- | --- | --- |
| Peso | ¿Cuánto cambia una propiedad declarada del corpus si se retira esta frase? | Confundir rareza o longitud con importancia. |
| Sustancia | ¿Qué conserva esta frase que no queda cubierto por otras? | Confundir novedad con necesidad; una repetición puede sostener el texto. |
| Hueso | ¿Qué pérdida ya no puede compensarse al reducir el texto? | Llamar esencia a la preferencia del juez. |

Son preguntas para diseñar medidas, no definiciones. Puede que el significado necesite un vector y no un número: una frase puede ser común en vocabulario, decisiva en estructura y redundante en información. La coincidencia de mapas diferentes señala un candidato a hueso; no lo certifica, porque dos instrumentos pueden coincidir en el mismo sesgo.

## Prueba central: predecir antes de destilar

Hipótesis de trabajo: una buena medida de sustancia debería predecir qué contenido sobrevive a la cascada de destilación. La semilla puntúa alto y la paja bajo. Si no predice mejor que controles baratos (azar, longitud, posición, rareza), no ha ganado su nombre.

"Sobrevivir" no significa conservar las mismas palabras: una copa puede reescribir o repartir una función entre pasajes, y hay que guardar la procedencia de cada frase original. El diseño mínimo:

1. Fijar archivos, limpieza y segmentación, con identificadores estables.
2. Registrar medidas, controles, predicción y criterio de fracaso antes de destilar.
3. Separar quien mide, quien destila y quien evalúa: si el destilador corta obedeciendo el ranking que se prueba, el resultado es circular.
4. Evaluar en material no usado para ajustar la medida, y después en el otro corpus, sin retocar la regla para salvarla.

Una segunda prueba: retirar frases que puntúan alto y bajo y ver qué relaciones se pierden; distingue "el destilador la conservó" de "la obra la necesitaba".

## Qué se pide a cada motor

Un capítulo con hipótesis y alcance; medidas ejecutables, con unidad, fórmula y un ejemplo calculable a mano; predicciones falsables sobre *Macbeth* o *El libro de arena*, con el umbral fijado antes de la prueba; pruebas de engaño (palabras raras añadidas, conjugaciones, repetición, paráfrasis); y el experimento más barato que permita descartar la propuesta. Sin los corpus completos no se inventan frases ni resultados: se presenta el diseño y se señalan los datos faltantes.

## Cómo se compararán las tesis

Se comparará lo ejecutable, no la elocuencia. Las IA comparten entrenamiento y moda: su convergencia no prueba verdad, da una pista para probar. La prueba vendrá de controles, predicciones fuera de muestra y pérdidas verificables. Para medir conviene un instrumento aburrido: versiones fijas, reglas visibles y resultados auditables.

## Criterio de éxito

No hace falta una teoría universal. Bastaría una medida nueva que supere un control simple, anticipe una pérdida real y mantenga esa ventaja fuera del texto con el que se diseñó. Si ninguna lo consigue, se conserva el resultado negativo y se vuelve al instrumento.

El tesoro no es que una máquina diga dónde está el hueso. Es poder señalar qué observó, por qué lo llama hueso y en qué prueba dejaría de llamarlo así.

## Fuentes

- [Cuatro criterios para mapear un corpus](cgbaaf_criterios-corpus.md): registro de los criterios y sus límites.
- [Destilería Osmancito](https://github.com/osmancitov/destileria): proyecto y protocolos de destilación.
