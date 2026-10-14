12 de octubre de 2026

# El ramillete y la ventana

Una frase sola puede ser una piedra. Cinco seguidas le devuelven el suelo, la voz y el movimiento. Pero no cualquier lugar del cuento abre una buena ventana.

Trabajamos sobre *El Libro de Arena*, de Borges: trece cuentos y 26 citas publicadas, dos por cuento. Osmancito propuso separar las dos tareas: el ramillete semántico ofrece cinco lugares posibles y la lectura elige dónde detenerse. La página sirve después dos frases anteriores, la elegida y dos posteriores, en el orden de Borges. El aparato busca el lugar. La narrativa hace el lucimiento.

## La regla

De las 26 citas, una por cuento la eligió Nemotron y otra Cohere, dos motores de embeddings: convierten cada frase en un vector, y la cercanía entre vectores se mide por coseno. Para cada cita buscamos sus cuatro vecinas más cercanas dentro del mismo cuento y del mismo motor, sin llamar de nuevo a los motores. Después leímos las cinco ventanas de cada ramillete y preferimos la escena que un invitado puede seguir desde cero, con voz, movimiento o una idea que se complete en el pasaje. La distancia propone; no decide.

## El resultado

Cambiaron 17 de las 26 frases centrales; las otras 9 ganaron su ventana sin cambiar de centro. Ninguna ventana cruza a otro cuento ni se solapa con la otra del mismo cuento. Para la página, los cinco segmentos de cada ventana se juntan en prosa corrida, sin cambiar las palabras de Borges.

## Un ejemplo: El Otro

La cita original de Nemotron era "Vaciló y me dijo: —¿Y usted?", que depende de una conversación anterior. Sus cuatro vecinas más cercanas, por coseno:

1. "Me contestó que sí."
2. "—Usted no lo conoce —exclamó—."
3. "Yo le contesté: —Puedo probarte que no miento."
4. "—Oí —le dije—, ¿tenés algún dinero?"

Escogimos la tercera: la ventana pone frente a frente los dos lugares y las dos edades, y la prueba empieza con un objeto de familia.

> Al cabo de un tiempo insistió: —Yo estoy aquí en Ginebra, en un banco, a unos pasos del Ródano. Lo raro es que nos parecemos, pero usted es mucho mayor, con la cabeza gris. Yo le contesté: —Puedo probarte que no miento. Voy a decirte cosas que no puede saber un desconocido. En casa hay un mate de plata con un pie de serpientes, que trajo del Perú nuestro bisabuelo.

## Las 26 escogidas

El centro de cada ventana, cuento por cuento:

1. **El Otro** · Nemotron: "Puedo probarte que no miento". Cohere: "su libro se refería a la gran masa de los oprimidos y parias".
2. **Ulrica** · Nemotron: "Tal vez —dijo en voz baja— la has encontrado". Cohere: "Oí de pronto el lejano aullido de un lobo".
3. **El Congreso** · Nemotron: "Algo de lo que entrevimos perdura". Cohere: "Ejercía diversas soberbias".
4. **There Are More Things** · Nemotron: "Ninguna de las formas insensatas que esa noche me deparó correspondía a la figura humana". Cohere: "A la brusca luz de un relámpago me hallé a unos pasos de la verja".
5. **La Secta de los Treinta** · Nemotron: "está predestinada a la muerte". Cohere: "Voluntarios sólo hubo dos: El Redentor y Judas".
6. **La Noche de los Dones** · Nemotron: "sos de los que madrugan temprano". Cohere: "fue como si entraran a caballo, en las piezas de un sueño".
7. **El Espejo y la Máscara** · Nemotron: "El poeta dijo el poema". Cohere: "No era una descripción de la batalla, era la batalla".
8. **Undr** · Nemotron: "una que otra pedrada me alcanzó". Cohere: "No referiré sus azares ni trataré de recordar el orden cabal de sus inconstancias".
9. **Utopía de un Hombre que Está Cansado** · Nemotron: "hechos que es una vergüenza ignorar". Cohere: "Las delicadas manos tañeron las cuerdas del arpa".
10. **El Soborno** · Nemotron: "Einarsson recibió el encargo oficial de viajar a Wisconsin". Cohere: "trató de comprender y justificar la causa del Sur".
11. **Avelino Arredondo** · Nemotron: "Arredondo vivía en las afueras". Cohere: "no sentía miedo, sintió una suerte de respeto".
12. **El Disco** · Nemotron: "puse la punta de los dedos sobre la palma". Cohere: "Abrí y entró un desconocido".
13. **El Libro de Arena** · Nemotron: "No puede ser, pero es". Cohere: "Declinaba el verano, y comprendí que el libro era monstruoso".

## Para llevar

La distancia encuentra parecidos. La lectura encuentra un sitio donde esos parecidos pueden respirar. No hicimos un collar con cinco frases dispersas: abrimos una ventana en el cuento.

Osmancito, con la asistencia de Instinct
