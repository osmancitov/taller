# Trazar

Protocolo 1 de 2. El siguiente es [Escalar](escalar.md).

Trazar dibuja la geometría de un corpus literario: sus ejes, su relieve, su densidad, su redundancia y sus vetas. Se corre una sola vez por corpus. El mapa que sale es la entrada de Escalar.

## Qué es esto

Este documento es un protocolo. Un motor (un modelo de lenguaje) lo lee y lo ejecuta palabra por palabra, sin añadir ni quitar nada. Está escrito para correr igual en cualquier motor.

Eso permite medir motores: el corpus es la constante y el motor es la única variable. Si dos motores trazan mapas distintos del mismo corpus, esa diferencia ya es una señal sobre los motores, antes de destilar nada.

## Principio: el mapa es endógeno

El mapa se dibuja solo con el corpus. No se usan datos del lector (highlights, gustos, notas, historial). No se usa conocimiento externo sobre la obra: ni crítica, ni resúmenes, ni lo que el motor recuerde de ella. Si algo no está en el texto recibido, no entra en el mapa.

El corpus se levanta a sí mismo. Un mapa que dependiera de quien lee no sería del corpus.

## Entrada

- El corpus literario completo, en texto plano o markdown.

No hay más entradas. Si el corpus llega incompleto, se dice al principio del mapa y se traza lo que hay.

## Comando

Lee el corpus entero. Después produce el mapa con las cinco secciones siguientes, en este orden y con estos títulos.

### 1. Ejes

Nombra la estructura del corpus tal como el texto la declara: actos, capítulos, libros, cantos, encabezados, voces, secciones numeradas. Indica la forma global que resulta: lineal, matriz (por ejemplo actos por voces), árbol, espiral, colección de piezas sueltas, otra. Una frase para justificar la forma elegida, con una cita corta del texto.

Numera cada tramo (T1, T2, T3...) en orden de aparición. Esa numeración es la que usan las demás secciones y Escalar. Un tramo es una unidad natural del corpus; si no hay divisiones, corta en tramos de tamaño parecido y dilo.

### 2. Relieve

Una tabla con una fila por tramo: número, título o primeras palabras, tamaño aproximado en palabras. Debajo, una línea con el perfil que dibuja: llanura (tramos parejos), pico (uno o pocos tramos dominan), arco (crece o decrece), meseta, otra.

### 3. Densidad

Para cada tramo, una nota de densidad: alta, media o baja. Densidad es cuánta materia distinta hay por palabra: ideas, imágenes, hechos, giros que no aparecen en otro lado. Un tramo largo puede ser de baja densidad y uno corto de alta. Justifica cada nota con media frase, sin más.

### 4. Redundancia

Para cada tramo, di cuánto se repite consigo mismo y con los demás: alta, media o baja. Señala los pares de tramos que se repiten entre sí y qué es lo que se repite (un motivo, una fórmula, una escena, un argumento). Donde el texto se repite, la materia se comprime con poco daño. Lo que no se repite en ningún lado es lo irrepetible.

### 5. Vetas

Las vetas son las líneas de máximo jugo: lo que, si se quitara, el corpus dejaría de ser él mismo. Lista de cinco a diez vetas. Cada una lleva:

- un nombre corto,
- los tramos por los que pasa,
- una cita literal breve del corpus que la ancle,
- una nota de por qué es veta (densidad alta y redundancia baja suele serlo; la redundancia alta con peso estructural también).

Ordénalas de mayor a menor jugo.

## Salida

El mapa, en markdown, con las cinco secciones. Empieza con una línea que diga el título del corpus y el motor que lo trazó, si lo conoce. Nada más: sin prólogo, sin despedida, sin resumen del corpus, sin juicios de valor.

## Reglas

- Solo el texto. Todo lo que se afirme se puede señalar en el corpus recibido.
- Las citas son literales y cortas.
- Los números son aproximados y se presentan como tales. No se inventa precisión.
- Si algo no se puede determinar con el texto, se escribe "no determinable" y se sigue.
- Nada de relleno. El mapa es una herramienta, no un ensayo.
- No se corre una segunda vez sobre el mismo corpus salvo para comparar motores.

## Después

El mapa y el corpus pasan a [Escalar](escalar.md).
