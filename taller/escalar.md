# Escalar

Protocolo 2 de 2. Antes: [Trazar](trazar.md).

Escalar corta la siguiente copa del corpus y la destila. Es recursivo: cada vez toma un quinto del resto vigente. El corpus se reduce 1/5, 1/25, 1/125... y cada copa es más pequeña y más barata que la anterior.

## Qué es esto

Este documento es un protocolo. Un motor (un modelo de lenguaje) lo lee y lo ejecuta palabra por palabra, sin añadir ni quitar nada. Está escrito para correr igual en cualquier motor.

Con Trazar y Escalar el corpus es la constante y el motor la única variable. Las copas de dos motores sobre el mismo corpus se pueden poner lado a lado. El mapa se paga una vez; cada copa cuesta menos que la anterior, así que evaluar un motor cuesta una fracción del corpus.

## Principio: destilar es dejar la semilla

Un destilado no es un resumen. Es una semilla: el texto mínimo que, sembrado en un lector, todavía despliega el árbol. Se destila quitando, y quitando, hasta que quitar un poco más ya no sea posible sin destruir la esencia. El criterio de parada es que la semilla todavía germine.

Un resumen cuenta lo que pasa. Una semilla conserva lo que hace funcionar al texto: su ecuación, sus gestos, lo que no se puede sustituir.

## Por qué quintos

La distancia entre escalones es un quinto y no una mitad. Con mitades, cada copa se parece demasiado a la anterior y se siente repetición. Con quintos, cada escalón es distinto del anterior en tamaño y en cosa que dice.

## Entrada

- El mapa que produjo [Trazar](trazar.md) para este corpus.
- El resto vigente del corpus. En la primera vuelta es el corpus entero. En las siguientes, es lo que devolvió la vuelta anterior.
- El número de vuelta: 1, 2, 3...

## Comando

Ejecuta estos pasos en orden.

### 1. Medir el resto

Estima el tamaño del resto vigente en palabras. Llámalo R. La copa de esta vuelta pesa un quinto de R. Llámalo C = R / 5.

### 2. Cortar siguiendo las vetas

Elige qué parte del resto va en esta copa. No cortes al azar ni de principio a fin. Corta por las vetas del mapa:

- Toma lo que cae en las vetas de mayor jugo que aún están en el resto vigente.
- Prefiere lo de densidad alta y redundancia baja.
- Lo de redundancia alta se puede comprimir: basta una muestra que lo represente.
- Conserva la procedencia: anota de qué tramos (T1, T2...) sale cada pieza.

### 3. Destilar

Con lo cortado, escribe la copa. Pesa C palabras, con una tolerancia de un diez por ciento. Es una semilla, no un resumen:

- Quita todo lo que se pueda quitar sin que la semilla deje de germinar.
- Conserva lo que no se puede sustituir: la estructura que carga el sentido, las citas literales que son la obra misma, el gesto central.
- No expliques, no comentes, no valores. No añadas nada que el corpus no diga.
- Si para llegar a C hay que destruir la esencia, entrega una copa más larga y dilo en la nota final.

### 4. Devolver el resto

El nuevo resto vigente es el resto anterior menos lo que se tomó para la copa. Devuélvelo por tramos, indicando cuánto queda de cada uno. La siguiente vuelta pesa un quinto de este nuevo resto.

## Salida

Tres bloques, en este orden y con estos títulos:

1. **Copa** (vuelta N): la semilla destilada.
2. **Procedencia**: de qué tramos y vetas sale la copa, en una línea por veta.
3. **Resto**: el nuevo resto vigente y su tamaño aproximado.

Sin prólogo, sin despedida. Si hubo una desviación de tamaño o un corte difícil, una sola línea al final, con el encabezado "Nota".

## Reglas

- Solo el corpus y el mapa. Ningún dato del lector ni conocimiento externo sobre la obra.
- Las citas son literales.
- Nunca se toma de lo ya cortado en vueltas anteriores. El resto solo se reduce.
- Una vuelta, una copa. No se encadenan varias en una sola ejecución.
- Si el mapa y el texto no coinciden, manda el texto, y se dice en la "Nota".
- Se detiene cuando la copa ya es demasiado pequeña para decir algo. Lo dice y no produce otra.

## Para comparar motores

Corran Trazar una vez por motor y comparen los mapas. Corran Escalar con el mismo mapa en todos los motores y comparen las copas de la vuelta 1. Después de la vuelta 1, cada motor sigue con su propio resto, y la divergencia también es un dato.

## Antes

El mapa viene de [Trazar](trazar.md).
