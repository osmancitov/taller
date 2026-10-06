# Confiar en la confianza

*Ken Thompson · Reflections on Trusting Trust · 1984*  
*Versión destilada en castellano · Destilería Osmancito*

Cuaderno de lectura · 5 de octubre de 2026.

## El escrito

El texto que sigue conserva la destilación preparada el 30 de septiembre de 2026. No es una traducción íntegra del ensayo: es una lectura de sus tres etapas y de su cierre ético.

Puedes borrar la traición del texto sin borrarla de la máquina.

Un programa puede imprimir una copia exacta de su propio código fuente. Se llama *quine*. Puede llevar, además, cualquier carga que se reproduzca con él. Lo que parece un juego contiene una semilla: una instrucción puede perpetuarse junto con aquello que la copia.

Un compilador transforma código fuente en un programa ejecutable. El de C está escrito en C: un compilador anterior produce el siguiente. Para enseñarle una nueva secuencia, `\v`, que representa el tabulador vertical, no basta con escribirla en su código: el compilador viejo todavía no la entiende. Primero se le da el valor numérico, 11 en ASCII. El ejecutable resultante ya conoce la secuencia; desde entonces puede compilar el código que la usa para definirla. Aprende una vez y transmite lo aprendido al recompilarse.

Ahora Thompson enseña otra cosa. Modifica el compilador para que reconozca el código de `login`, el programa que controla la entrada en UNIX. Al compilarlo, introduce una contraseña adicional que permite entrar como cualquier usuario. El código fuente de `login` puede seguir siendo inocente: la traición ocurre al convertirlo en ejecutable. No es un error. Es un caballo de Troya.

Pero la trampa aún figura en el código del compilador. Thompson añade un segundo reconocimiento: cuando este compile su propio código, insertará en el nuevo ejecutable las dos trampas, la que altera `login` y la que vuelve a introducirlas. La técnica de reproducción del primer juego proporciona la carga; el aprendizaje del segundo permite instalarla. Con un compilador normal obtiene primero el ejecutable infectado. Lo instala y borra las modificaciones del código fuente.

Ya no hay nada sospechoso que leer. Cada vez que el compilador infectado recompila ese código limpio, engendra otro compilador infectado. Cada vez que compila `login`, vuelve a abrir la entrada secreta. La fuente ha sido lavada; la herencia permanece.

Revisar el código fuente, por escrupulosamente que se haga, no basta para certificar lo que ejecutamos si desconfiamos de la herramienta que lo convirtió en máquina. Thompson eligió el compilador, pero la trampa podría vivir en un ensamblador, un cargador o el microcódigo del hardware. Cuanto más abajo se esconde, más difícil resulta verla. La pregunta atraviesa las capas: ¿qué sostiene nuestra confianza en aquello con lo que comprobamos lo demás?

Al final, Thompson devuelve la responsabilidad a las personas. Rechaza que la prensa convierta las intrusiones en hazañas: entrar en un sistema ajeno no deja de ser una invasión porque la puerta esté abierta.

---

## Nota del operador (Instinct)

Esta es una destilación, no una traducción íntegra. Conserva las tres etapas de la demostración y el giro ético final; deja fuera los agradecimientos y los listados de código. La frase inicial y las imágenes de la semilla, la herencia y la fuente lavada pertenecen a esta versión, no son citas de Thompson.

Fuente: Ken Thompson, "Reflections on Trusting Trust", *Communications of the ACM*, volumen 27, número 8, agosto de 1984, pp. 761-763. [Ensayo original](https://www.cs.cmu.edu/~rdriley/487/papers/Thompson_1984_ReflectionsonTrustingTrust.pdf).

## Al margen: la herramienta también tiene historia

Para quien está aprendiendo Debian 12, este escrito abre una pregunta anterior a cualquier comando: ¿con qué se construyó el programa que va a ejecutarse? El código fuente describe una intención; el ejecutable es el resultado de una transformación. Entre ambos trabaja una herramienta que también fue construida por otra herramienta.

Thompson lleva esa cadena hasta el punto donde una revisión del texto ya no alcanza. No demuestra que todo compilador esté contaminado. Demuestra que un compilador puede transmitir una alteración que no figura en el código fuente que se está leyendo. Son afirmaciones distintas: una posibilidad no es una acusación.

> Ninguna cantidad de verificación o examen del código fuente te protegerá de usar código en el que no se puede confiar.

Traducción de una frase de la sección «Moral» del original. El alcance importa: inspeccionar la fuente por sí sola no resuelve la desconfianza en la herramienta que produce el binario. El texto no vuelve inútil la revisión; muestra el límite de tomarla como garantía completa.

La pequeña lección de `\v` ayuda a entender la trampa sin confundirla con magia. Primero se introduce una definición que el compilador anterior entiende. Después, el nuevo ejecutable permite expresar esa misma definición de forma autorreferente. El caballo de Troya aprovecha esa continuidad: lo aprendido sobrevive a la limpieza del texto.

Por eso el quine no es una curiosidad aparte. Enseña a llevar una carga junto con la copia; el compilador enseña a heredarla. Una fuente limpia puede ser descendiente de una máquina que no lo estaba.

## La puerta abierta

El ensayo termina fuera del compilador, ante la puerta de otra persona. Thompson rechaza el aplauso a quienes entran en sistemas ajenos y recuerda que una falla de protección no concede permiso.

> No debería importar que la puerta del vecino esté sin llave.

Traducción de una frase del cierre del original. La confianza tiene aquí dos caras: la que se deposita en una herramienta y la que se debe a quien deja algo a nuestro alcance. Saber abrir una puerta no da derecho a cruzarla.

## Para seguir leyendo

- [Reflections on Trusting Trust, ensayo original en inglés](https://www.cs.cmu.edu/~rdriley/487/papers/Thompson_1984_ReflectionsonTrustingTrust.pdf). Ken Thompson, *Communications of the ACM*, 27(8), agosto de 1984, pp. 761-763.
- [Ficha de la publicación en ACM](https://dl.acm.org/doi/10.1145/358198.358210).
- [Aprendiendo Debian](007_debian_aprendiendo.md): el cuaderno de estudio al que esta lectura acompaña.

Las notas al margen y las traducciones breves de este cuaderno son comentarios de lectura; no forman parte de la destilación anterior ni sustituyen el ensayo completo.
