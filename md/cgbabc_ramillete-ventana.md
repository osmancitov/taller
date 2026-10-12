12 de octubre de 2026

# El ramillete y la ventana

Una frase sola puede ser una piedra. Cinco seguidas le devuelven el suelo, la voz y el movimiento. Pero no cualquier lugar del cuento abre una buena ventana.

Osmancito propuso separar las dos tareas: el ramillete semántico ofrece cinco lugares posibles; la lectura elige dónde detenerse. La página sirve después dos frases anteriores, la elegida y dos posteriores, en el orden de Borges. El aparato busca el lugar. La narrativa hace el lucimiento.

## La regla

Partimos de las 26 citas publicadas: dos por cuento, una de Nemotron y otra de Cohere. Para cada cita buscamos sus cuatro vecinas más cercanas por coseno dentro del mismo cuento y del mismo motor. Convertimos los vectores int8 guardados a números flotantes y los normalizamos a longitud uno antes del producto escalar. En los empates manda el orden del texto. No se hicieron nuevas llamadas de embeddings.

La búsqueda usa todos los vectores disponibles del cuento: Nemotron tiene 1.802 en el libro y Cohere 1.853. Esta revisión no vuelve a aplicar el filtro de tres palabras del ranking original. Son caches cuantizados; el coseno no recupera la precisión de los vectores flotantes originales. El centro original entra siempre entre las cinco candidatas.

Leímos las cinco ventanas de cada ramillete. Se prefirió una escena que pudiera seguir un invitado desde cero, con voz, movimiento o una idea que se complete en el pasaje. No se escogió una frase por ser la más cercana: esa distancia propone, no decide. Los puentes se volvieron a escribir para llegar al comienzo de cada ventana y salir de su final, sin repetir lo que Borges acaba de decir.

## El resultado

Cambiaron 17 de las 26 frases centrales. Las otras 9 ganaron su ventana sin cambiar de centro. Las 26 ventanas tienen cinco segmentos del molde; ninguna cruza a otro cuento o al epílogo y ninguna se solapa con la otra del mismo cuento. Cuando un centro se movió después del otro, los pasajes volvieron a ordenarse según el texto.

Contamos segmentos del molde, no siempre oraciones gramaticales completas: el diálogo puede separar una pregunta de su atribución. Para la página se juntan en prosa corrida, sin cambiar las palabras.

## Los identificadores

El acta de la primera destilación conservaba la numeración anterior a la migración global. Las 26 citas se reconciliaron por texto exacto y cuento con el molde vigente. Por eso cada registro guarda el ID del acta y el ID global; un cambio de numeración no cuenta como cambio de frase. Las ventanas siguen char_start, no la aritmética del ID.

## Los ramilletes

El coseno de cada vecina se mide contra la cita original. La primera entrada es esa cita, no el resultado de una nueva competencia. La escogida lleva su ventana natural completa.

### 1. El otro

#### Nemotron

Original: `BD0075` en el acta; `BD0079` en el molde global.

1. `BD0079` · coseno 1.00000000: Vaciló y me dijo: —¿Y usted?

2. `BD0033` · coseno 0.49966621: Me contestó que sí.

3. `BD0153` · coseno 0.45804849: —Usted no lo conoce —exclamó—.

4. `BD0040` · coseno 0.45408636 · escogida: Yo le contesté: —Puedo probarte que no miento.

5. `BD0166` · coseno 0.43290755: —Oí —le dije—, ¿tenés algún dinero?


Escogida: `BD0040`. Ventana: `BD0038`, `BD0039`, `BD0040`, `BD0041`, `BD0042`.

La ventana pone frente a frente los dos lugares y las dos edades; la prueba empieza con un objeto de familia. La pregunta original dependía de una conversación anterior.

> Al cabo de un tiempo insistió: —Yo estoy aquí en Ginebra, en un banco, a unos pasos del Ródano. Lo raro es que nos parecemos, pero usted es mucho mayor, con la cabeza gris. Yo le contesté: —Puedo probarte que no miento. Voy a decirte cosas que no puede saber un desconocido. En casa hay un mate de plata con un pie de serpientes, que trajo del Perú nuestro bisabuelo.

#### Cohere

Original: `BD0111` en el acta; `BD0115` en el molde global.

1. `BD0115` · coseno 1.00000000: Sin hacerme caso, me aclaró que su libro cantaría la fraternidad de todos los hombres.

2. `BD0119` · coseno 0.54836993 · escogida: Me dijo que su libro se refería a la gran masa de los oprimidos y parias.

3. `BD0117` · coseno 0.49229929: Me quedé pensando y le pregunté si verdaderamente se sentía hermano de todos.

4. `BD0083` · coseno 0.48507179: Me agradó que nada me preguntara sobre el fracaso o éxito de los libros.

5. `BD0109` · coseno 0.48432759: Le pregunté qué estaba escribiendo y me dijo que preparaba un libro de versos que se titularía Los himnos rojos.


Escogida: `BD0119`. Ventana: `BD0117`, `BD0118`, `BD0119`, `BD0120`, `BD0121`.

La enumeración de hermanos posibles enfrenta la fraternidad abstracta con los individuos. La ventana contiene pregunta, respuesta y objeción, sin necesitar los títulos de los versos.

> Me quedé pensando y le pregunté si verdaderamente se sentía hermano de todos. Por ejemplo, de todos los empresarios de pompas fúnebres, de todos los carteros, de todos los buzos, de todos los que viven en la acera de los números pares, de todos los afónicos, etcétera. Me dijo que su libro se refería a la gran masa de los oprimidos y parias. —Tu masa de oprimidos y de parias —le contesté— no es más que una abstracción. Sólo los individuos existen, si es que existe alguien.

### 2. Ulrica

#### Nemotron

Original: `BD0289` en el acta; `BD0295` en el molde global.

1. `BD0295` · coseno 1.00000000: —Por supuesto —me dijo—.

2. `BD0223` · coseno 0.58451001: —Así es —dijo ella—.

3. `BD0216` · coseno 0.45561977: —Soy feminista —dijo—.

4. `BD0261` · coseno 0.44196775 · escogida: —Tal vez —dijo en voz baja— la has encontrado.

5. `BD0287` · coseno 0.44128377: —Javier Otárola —le dije.


Escogida: `BD0261`. Ventana: `BD0259`, `BD0260`, `BD0261`, `BD0262`, `BD0263`.

La búsqueda de un libro se vuelve encuentro amoroso. La réplica desemboca en el beso y en la promesa; tiene más vida que el asentimiento sobre la saga.

> —De Quincey —respondí— dejó de buscarla. Yo, a lo largo del tiempo, sigo buscándola. —Tal vez —dijo en voz baja— la has encontrado. Comprendí que una cosa inesperada no me estaba prohibida y le besé la boca y los ojos. Me apartó con suave firmeza y luego declaró: —Seré tuya en la posada de Thorgate.

#### Cohere

Original: `BD0235` en el acta; `BD0241` en el molde global.

1. `BD0241` · coseno 1.00000000: Al día siguiente bajé temprano al comedor.

2. `BD0305` · coseno 0.44148008: El aposento oscuro era bajo, con un techo a dos aguas.

3. `BD0244` · coseno 0.42675131: Ulrica me invitó a su mesa.

4. `BD0282` · coseno 0.41591424: Arribaremos más pronto a Thorgate.

5. `BD0252` · coseno 0.41293555 · escogida: Oí de pronto el lejano aullido de un lobo.


Escogida: `BD0252`. Ventana: `BD0250`, `BD0251`, `BD0252`, `BD0253`, `BD0254`.

El amor declarado, el lobo que nunca se había oído y la calma de Ulrica abren la rareza dentro del paisaje. La mesa sola era una transición.

> Le propuse que fuéramos a Thorgate, que queda río abajo, a unas millas. Sé que ya estaba enamorado de Ulrica; no hubiera deseado a mi lado ninguna otra persona. Oí de pronto el lejano aullido de un lobo. No he oído nunca aullar a un lobo, pero sé que era un lobo. Ulrica no se inmutó.

### 3. El Congreso

#### Nemotron

Original: `BD0619` en el acta; `BD0627` en el molde global.

1. `BD0627` · coseno 1.00000000 · escogida: Algo de lo que entrevimos perdura —el rojizo paredón de la Recoleta, el amarillo paredón de la cárcel, una pareja de hombres bailando en una esquina sin ochava, un atrio ajedrezado con una verja, las barreras del tren, mi casa, un mercado, la insondable y húmeda noche— pero ninguna de esas cosas fugaces, que acaso fueron otras, importa.

2. `BD0550` · coseno 0.37070518: Volví a mi antiguo alojamiento en la calle Chile; aquel día y el otro los pasamos hablando y caminando.

3. `BD0501` · coseno 0.36882616: Extrañaba los leones de un portón de la calle Jujuy, cerca de la plaza del Once, o la luz de cierto almacén de imprecisa topografía, no los lugares habituales.

4. `BD0388` · coseno 0.36755537: Antes, quiero recordar al lector mi situación de entonces: yo era un pobre muchacho de Casilda, hijo de chacareros, que había llegado a Buenos Aires y que de pronto se encontraba, así la sentí, en el íntimo centro de Buenos Aires y tal vez, quién sabe, del mundo.

5. `BD0540` · coseno 0.35334975: En la áspera frontera del Brasil me había acosado la nostalgia; no así en el rojo laberinto de Londres, que me dio tantas cosas.


Escogida: `BD0627`. Ventana: `BD0625`, `BD0626`, `BD0627`, `BD0628`, `BD0629`.

Conservo el centro: las imágenes de la ciudad desembocan en la revelación del Congreso y en su pérdida. El puente debe nombrar antes a Beatriz y a Twirl.

> Las palabras inglesas no me trajeron la imagen de Beatriz. A mis espaldas Twirl murmuró: —He querido hacer el mal y hago el bien. Algo de lo que entrevimos perdura —el rojizo paredón de la Recoleta, el amarillo paredón de la cárcel, una pareja de hombres bailando en una esquina sin ochava, un atrio ajedrezado con una verja, las barreras del tren, mi casa, un mercado, la insondable y húmeda noche— pero ninguna de esas cosas fugaces, que acaso fueron otras, importa. Importa haber sentido que nuestro plan, del cual más de una vez nos burlamos, existía realmente y secretamente y era el universo y nosotros. Sin mayor esperanza, he buscado a lo largo de los años el sabor de esa noche; alguna vez creí recuperarla en la música, en el amor, en la incierta memoria, pero no ha vuelto, salvo una sola madrugada, en un sueño.

#### Cohere

Original: `BD0473` en el acta; `BD0481` en el molde global.

1. `BD0481` · coseno 1.00000000: Sin duda por sus venas corrían sangre india y sangre negra.

2. `BD0483` · coseno 0.46124080: Casi todos usaban chiripá y uno que otro, bombacha.

3. `BD0373` · coseno 0.46058016: Ante el negro y el niño había dos tazas de chocolate.

4. `BD0480` · coseno 0.45171689: Para entenderse entre ellos, usaban parcamente un gangoso español abrasilerado.

5. `BD0421` · coseno 0.44101589 · escogida: Ejercía diversas soberbias: la de ser oriental, la de ser criollo, la de atraer a todas las mujeres, la de haber elegido un sastre costoso y, nunca sabré por qué, la de su estirpe vasca, gente que al margen de la historia no ha hecho otra cosa que ordeñar vacas.


Escogida: `BD0421`. Ventana: `BD0419`, `BD0420`, `BD0421`, `BD0422`, `BD0423`.

La ventana une la defensa de Ferri, el rechazo de Eguren y la lista de sus soberbias. El retrato tiene voz y conflicto; no queda reducido al catálogo de los gauchos.

> Don Alejandro lo miró con severidad y dijo sin apuro: —El señor Ferri está en representación de los emigrantes, cuya labor está levantando el país. Nunca Fermín Eguren me pudo ver. Ejercía diversas soberbias: la de ser oriental, la de ser criollo, la de atraer a todas las mujeres, la de haber elegido un sastre costoso y, nunca sabré por qué, la de su estirpe vasca, gente que al margen de la historia no ha hecho otra cosa que ordeñar vacas. Un incidente de lo más trivial selló nuestras enemistades. Después de una sesión, Eguren propuso que fuéramos a la calle Junín.

### 4. There Are More Things

#### Nemotron

Original: `BD0718` en el acta; `BD0728` en el molde global.

1. `BD0728` · coseno 1.00000000: Me bastó verlo para descartar las estratagemas que había urdido la víspera.

2. `BD0708` · coseno 0.44428243: Noches pasadas, yo venía de una farra.

3. `BD0713` · coseno 0.43731147: Aquella noche no dormí.

4. `BD0700` · coseno 0.40115506: Era casi de noche.

5. `BD0768` · coseno 0.36520911 · escogida: Ninguna de las formas insensatas que esa noche me deparó correspondía a la figura humana o a un uso concebible.


Escogida: `BD0768`. Ventana: `BD0766`, `BD0767`, `BD0768`, `BD0769`, `BD0770`.

La ventana lleva de una reflexión sobre la percepción al terror concreto de los muebles. La visita al carpintero se entiende, pero todavía no deja ver la extrañeza del cuento.

> El salvaje no puede percibir la biblia del misionero; el pasajero no ve el mismo cordaje que los hombres de a bordo. Si viéramos realmente el universo, tal vez lo entenderíamos. Ninguna de las formas insensatas que esa noche me deparó correspondía a la figura humana o a un uso concebible. Sentí repulsión y terror. En uno de los ángulos descubrí una escalera vertical, que daba al otro piso.

#### Cohere

Original: `BD0738` en el acta; `BD0748` en el molde global.

1. `BD0748` · coseno 1.00000000 · escogida: A la brusca luz de un relámpago me hallé a unos pasos de la verja.

2. `BD0722` · coseno 0.50776719: El portón de la verja estaba cerrado y unos barrotes retorcidos.

3. `BD0709` · coseno 0.49156591: A unas cien varas de la quinta, vi algo.

4. `BD0754` · coseno 0.49048971: Una racha de lluvia me azotó la cara y entré.

5. `BD0789` · coseno 0.45240850: Dejé la luz prendida y acometí cautelosamente el descenso.


Escogida: `BD0748`. Ventana: `BD0746`, `BD0747`, `BD0748`, `BD0749`, `BD0750`.

Conservo el centro: viento, agua, relámpago y portón componen la entrada. La ventana posterior de la lluvia ya presupone esa entrada; ésta la muestra suceder.

> Primero el viento sur y después el agua a raudales. Erré buscando un árbol. A la brusca luz de un relámpago me hallé a unos pasos de la verja. No sé si con temor o con esperanza probé el portón. Inesperadamente, cedió.

### 5. La Secta de los Treinta

#### Nemotron

Original: `BD0807` en el acta; `BD0818` en el molde global.

1. `BD0818` · coseno 1.00000000 · escogida: Alguna quiere que nos dé la cifra a que están reducidos los fieles, lo cual es irrisorio pero profético, porque la Secta, dada su perversa doctrina, está predestinada a la muerte.

2. `BD0800` · coseno 0.50669621: La Secta nunca fue numerosa y ahora son parcos sus prosélitos.

3. `BD0842` · coseno 0.43353265: La Secta los venera por igual y absuelve a los otros.

4. `BD0816` · coseno 0.42290574: »La Secta elude las iglesias; sus doctores predican al aire libre, desde un cerro o un muro o a veces desde un bote en la orilla.

5. `BD0817` · coseno 0.39214261: »El nombre de la Secta ha suscitado tenaces conjeturas.


Escogida: `BD0818`. Ventana: `BD0816`, `BD0817`, `BD0818`, `BD0819`, `BD0820`.

Conservo el centro: las conjeturas sobre el nombre se acumulan y el cronista las derriba. Las otras ventanas o abren una cita incompleta o adelantan el secreto que sirve el segundo pasaje.

> »La Secta elude las iglesias; sus doctores predican al aire libre, desde un cerro o un muro o a veces desde un bote en la orilla. »El nombre de la Secta ha suscitado tenaces conjeturas. Alguna quiere que nos dé la cifra a que están reducidos los fieles, lo cual es irrisorio pero profético, porque la Secta, dada su perversa doctrina, está predestinada a la muerte. Otra lo deriva de la altura del arca, que era de treinta codos; otra, que falsea la astronomía, del número de noches, que son la suma de cada mes lunar; otra, del bautismo del Salvador; otra, de los años de Adán, cuando surgió del polvo rojo. Todas son igualmente falsas.

#### Cohere

Original: `BD0818` en el acta; `BD0829` en el molde global.

1. `BD0829` · coseno 1.00000000: Nació del vientre de una mujer del pueblo elegido no sólo para predicar el Amor, sino para sufrir el martirio.

2. `BD0828` · coseno 0.47050348: »El Verbo se hizo carne para ser hombre entre los hombres, que lo darían a la cruz y serían redimidos por Él.

3. `BD0839` · coseno 0.45221745 · escogida: Voluntarios sólo hubo dos: El Redentor y Judas.

4. `BD0843` · coseno 0.42544448: »No hay un solo culpable; no hay uno que no sea un ejecutor, a sabiendas o no, del plan que trazó la Sabiduría.

5. `BD0813` · coseno 0.39236227: »El dictamen Quien mira una mujer para codiciarla, ya adulteró con ella en su corazón es un consejo inequívoco de pureza.


Escogida: `BD0839`. Ventana: `BD0837`, `BD0838`, `BD0839`, `BD0840`, `BD0841`.

La enumeración de los involuntarios desemboca en los dos voluntarios y en las monedas de Judas. Se ve la torsión de la doctrina, no sólo el relato común de la Pasión.

> En la tragedia de la Cruz —lo escribo con debida reverencia— hubo actores voluntarios e involuntarios, todos imprescindibles, todos fatales. Involuntarios fueron los sacerdotes que entregaron los dineros de plata, involuntaria fue la plebe que eligió a Barrabás, involuntario fue el procurador de Judea, involuntarios fueron los romanos que erigieron la Cruz de Su martirio y clavaron los clavos y echaron suertes. Voluntarios sólo hubo dos: El Redentor y Judas. Éste arrojó las treinta piezas que eran el precio de la salvación de las almas e inmediatamente se ahorcó. A la sazón contaba treinta y tres años, como el Hijo del Hombre.

### 6. La noche de los dones

#### Nemotron

Original: `BD0940` en el acta; `BD0952` en el molde global.

1. `BD0952` · coseno 1.00000000 · escogida: Se rió y me dijo: »—A lo que veo, sos de los que madrugan temprano.

2. `BD0906` · coseno 0.36024448: A la madrugada ocurrió.

3. `BD0963` · coseno 0.35948197: Rufino dijo riéndose: »—A este compadre ya se le acabaron los cortes.

4. `BD0964` · coseno 0.34770119: »Yo iba de grupo en grupo, contándole a la gente lo que había visto.

5. `BD0893` · coseno 0.34103840: Nos dijo así: »—Cuando me trajeron de Catamarca yo era muy chica.


Escogida: `BD0952`. Ventana: `BD0950`, `BD0951`, `BD0952`, `BD0953`, `BD0954`.

Conservo el centro: luna, bayoneta, broma y un hombre que baja por la pared componen una escena entera y suspendida antes de la muerte.

> La noche era de luna. Un sargento de policía, con rifle y bayoneta calada, estaba vigilando la tapia. Se rió y me dijo: »—A lo que veo, sos de los que madrugan temprano. »Algo debí de contestar, pero no me hizo caso. Por la tapia un hombre se descolgaba.

#### Cohere

Original: `BD0908` en el acta; `BD0920` en el molde global.

1. `BD0920` · coseno 1.00000000 · escogida: Un empellón y estaban en la sala y fue como si entraran a caballo, en las piezas de un sueño.

2. `BD0867` · coseno 0.45953815: Rufino se había empilchado como quien va a una fiesta y lucía un puñal de plata; yo me fui sin mi cuchillito, por temor a las bromas.

3. `BD0902` · coseno 0.45509745: De puro cavilar, yo casi tenía ganas que se vinieran y sabía mirar para el rumbo que el sol se pone.

4. `BD0923` · coseno 0.44027839: El que venía en punta le asestó un codazo a Rufino, que estaba cerca de la puerta.

5. `BD0882` · coseno 0.43816220: Para despistar o para que vieran que yo era un chico, me puse a jugar con el perro, en la punta de un banco.


Escogida: `BD0920`. Ventana: `BD0918`, `BD0919`, `BD0920`, `BD0921`, `BD0922`.

Conservo el centro: la voz de la Cautiva se mezcla con los gritos de la calle y los intrusos parecen salir de un sueño. Las otras ventanas explican mejor a Moreira, pero pierden ese cruce.

> En Santa Irene había unas armas largas, que no sirvieron más que para aturdir y para que juntaran más rabia. »Hablaba la Cautiva como quien dice una oración, de memoria, pero yo oí en la calle los indios del desierto y los gritos. Un empellón y estaban en la sala y fue como si entraran a caballo, en las piezas de un sueño. Eran orilleros borrachos. Ahora, en la memoria, los veo muy altos.

### 7. El espejo y la máscara

#### Nemotron

Original: `BD0969` en el acta; `BD0982` en el molde global.

1. `BD0982` · coseno 1.00000000: —Sí, Rey —dijo el poeta—.

2. `BD1057` · coseno 0.70241998: —Sí —dijo tristemente el poeta—.

3. `BD1062` · coseno 0.61530579 · escogida: El poeta dijo el poema.

4. `BD1056` · coseno 0.58727012: —preguntó el Rey.

5. `BD1047` · coseno 0.53380102: —Doy gracias y he entendido —dijo el poeta.


Escogida: `BD1062`. Ventana: `BD1060`, `BD1061`, `BD1062`, `BD1063`, `BD1064`.

La línea no se transcribe: vemos su efecto en quienes la pronuncian. La ventana deja actuar el silencio y la prohibición, en vez de servir un simple sí.

> —No me atrevo. —Yo te doy el valor que te hace falta —declaró el Rey. El poeta dijo el poema. Era una sola línea. Sin animarse a pronunciarla en voz alta, el poeta y su Rey la paladearon, como si fuera una plegaria secreta o una blasfemia.

#### Cohere

Original: `BD1018` en el acta; `BD1031` en el molde global.

1. `BD1031` · coseno 1.00000000 · escogida: No era una descripción de la batalla, era la batalla.

2. `BD1013` · coseno 0.48521926: La guerra es el hermoso tejido de hombres y el agua de la espada es la sangre.

3. `BD1023` · coseno 0.47509695: Nadie profirió un grito de batalla, nadie opuso el pecho a los vikings.

4. `BD1051` · coseno 0.46396548: Algo, que no era el tiempo, había surcado y transformado sus rasgos.

5. `BD1065` · coseno 0.46287418: El Rey no estaba menos maravillado y menos maltrecho que el otro.


Escogida: `BD1031`. Ventana: `BD1029`, `BD1030`, `BD1031`, `BD1032`, `BD1033`.

Conservo el centro: la inseguridad al leer y la batalla que ocupa la página permiten sentir el salto de una poesía a otra. La tercera oda tendrá su propio pasaje.

> No lo repitió de memoria; lo leyó con visible inseguridad, omitiendo ciertos pasajes, como si él mismo no los entendiera del todo o no quisiera profanarlos. La página era extraña. No era una descripción de la batalla, era la batalla. En su desorden bélico se agitaban el Dios que es Tres y es Uno, los númenes paganos de Irlanda y los que guerrearían, centenares de años después, en el principio de la Edda Mayor. La forma no era menos curiosa.

### 8. Undr

#### Nemotron

Original: `BD1093` en el acta; `BD1107` en el molde global.

1. `BD1107` · coseno 1.00000000 · escogida: Era de noche; advertí que los hombres que se cruzaban en mi camino me miraban curiosamente y una que otra pedrada me alcanzó.

2. `BD1109` · coseno 0.43868354: »El herrero me ofreció albergue para la noche.

3. `BD1195` · coseno 0.39420518: Ya era de noche.

4. `BD1154` · coseno 0.36338402: »Caminé unos pasos.

5. `BD1116` · coseno 0.35705429: Apenas la aprendí de memoria vinieron a buscarme dos hombres.


Escogida: `BD1107`. Ventana: `BD1105`, `BD1106`, `BD1107`, `BD1108`, `BD1109`.

Conservo el centro: el propósito del viaje, las piedras y la herrería dan al lector un recorrido visible. La ventana del regreso exige más historia previa.

> El hombre dijo: »—Soy de estirpe de skalds; me bastó saber que la poesía de los urnos consta de una sola palabra para emprender su busca y el derrotero que me conduciría a su tierra. No sin fatigas y trabajos llegué al cabo de un año. Era de noche; advertí que los hombres que se cruzaban en mi camino me miraban curiosamente y una que otra pedrada me alcanzó. Vi el resplandor de una herrería y entré. »El herrero me ofreció albergue para la noche.

#### Cohere

Original: `BD1076` en el acta; `BD1090` en el molde global.

1. `BD1090` · coseno 1.00000000: La incierta o fabulosa información de los mercaderes, lo azaroso del rumbo y las depredaciones de los nómadas, nunca me permitieron arribar a su territorio.

2. `BD1094` · coseno 0.43790746: Debido a la inclemencia de las guerras casi no aran la tierra.

3. `BD1107` · coseno 0.42987421: Era de noche; advertí que los hombres que se cruzaban en mi camino me miraban curiosamente y una que otra pedrada me alcanzó.

4. `BD1172` · coseno 0.42506206 · escogida: No referiré sus azares ni trataré de recordar el orden cabal de sus inconstancias.

5. `BD1093` · coseno 0.42141316: Son pastores, barqueros, hechiceros, forjadores de espadas y trenzadores.


Escogida: `BD1172`. Ventana: `BD1170`, `BD1171`, `BD1172`, `BD1173`, `BD1174`.

Los oficios, la esclavitud y los inviernos hacen de la búsqueda una vida. Evito repetir la llegada a la herrería, candidata de ambos motores y ya escogida en Nemotron.

> Si el viento es favorable, navegarás mañana hacia el Sur. »Así tuvo principio la aventura que duraría tantos inviernos. No referiré sus azares ni trataré de recordar el orden cabal de sus inconstancias. Fui remero, mercader de esclavos, esclavo, leñador, salteador de caravanas, cantor, catador de aguas hondas y de metales. Padecí cautiverio durante un año en las minas de azogue, que aflojan los dientes.

### 9. Utopía de un hombre que está cansado

#### Nemotron

Original: `BD1290` en el acta; `BD1306` en el molde global.

1. `BD1306` · coseno 1.00000000: En el ayer que me tocó, la gente era ingenua; creía que una mercadería era buena porque así lo afirmaba y lo repetía su propio fabricante.

2. `BD1296` · coseno 0.34401438 · escogida: —En mi curioso ayer —contesté—, prevalecía la superstición de que entre cada tarde y cada mañana ocurren hechos que es una vergüenza ignorar.

3. `BD1251` · coseno 0.25394054: Comprendí que advertía mi zozobra y dije que sí.

4. `BD1246` · coseno 0.25178940: —Por la ropa —me dijo—, veo que llegas de otro siglo.

5. `BD1310` · coseno 0.24470861: Ya no hay quien adolezca de pobreza, que habrá sido insufrible, ni de riqueza, que habrá sido la forma más incómoda de la vulgaridad.


Escogida: `BD1296`. Ventana: `BD1294`, `BD1295`, `BD1296`, `BD1297`, `BD1298`.

La imprenta abolida y la obligación de enterarse de todo chocan en cinco frases. Es una conversación entre épocas y una sátira con más recorrido que la publicidad sola.

> Además no importa leer, sino releer. La imprenta, ahora abolida, ha sido uno de los peores males del hombre, ya que tendió a multiplicar hasta el vértigo textos innecesarios. —En mi curioso ayer —contesté—, prevalecía la superstición de que entre cada tarde y cada mañana ocurren hechos que es una vergüenza ignorar. El planeta estaba poblado de espectros colectivos, el Canadá, el Brasil, el Congo Suizo y el Mercado Común. Casi nadie sabía la historia previa de esos entes platónicos, pero sí los más ínfimos pormenores del último congreso de pedagogos, la inminente ruptura de relaciones y los mensajes que los presidentes mandaban, elaborados por el secretario del secretario con la prudente imprecisión que era propia del género.

#### Cohere

Original: `BD1351` en el acta; `BD1367` en el molde global.

1. `BD1367` · coseno 1.00000000: Encendió una lámpara, que también pendía del cielo raso.

2. `BD1239` · coseno 0.72758656: Pendía del cielo raso una lámpara de luz amarillenta.

3. `BD1377` · coseno 0.44612136 · escogida: Las delicadas manos tañeron las cuerdas del arpa y apenas percibí uno que otro sonido.

4. `BD1231` · coseno 0.44593708: Empezó a caer la lluvia.

5. `BD1348` · coseno 0.43702041: Afuera, la llanura estaba blanca de silenciosa nieve y de luna.


Escogida: `BD1377`. Ventana: `BD1375`, `BD1376`, `BD1377`, `BD1378`, `BD1379`.

Los colores invisibles y el arpa casi inaudible hacen perceptible la distancia entre las épocas. Los golpes traen además a los visitantes que conducirán al final.

> No diré que estaban en blanco, pero sí casi en blanco. —Están pintadas con colores que tus antiguos ojos no pueden ver. Las delicadas manos tañeron las cuerdas del arpa y apenas percibí uno que otro sonido. Fue entonces cuando se oyeron los golpes. Una alta mujer y tres o cuatro hombres entraron en la casa.

### 10. El soborno

#### Nemotron

Original: `BD1438` en el acta; `BD1455` en el molde global.

1. `BD1455` · coseno 1.00000000: Winthrop quería ser justo y no podía permitir que el escrito de Einarsson, ya releído y comentado por muchos, influyera en su decisión.

2. `BD1440` · coseno 0.56856966: Einarsson era harto más joven; su petulancia le granjeaba la aversión general, sin excluir la de Winthrop.

3. `BD1519` · coseno 0.50006605: —En la mía hubo muchos —contestó Winthrop—.

4. `BD1457` · coseno 0.49447931 · escogida: Cierta mañana, Winthrop conversó con su jefe; esa misma tarde Einarsson recibió el encargo oficial de viajar a Wisconsin.

5. `BD1458` · coseno 0.48947690: La víspera del diecinueve de marzo, día de la partida, Einarsson se presentó en el despacho de Ezra Winthrop.


Escogida: `BD1457`. Ventana: `BD1455`, `BD1456`, `BD1457`, `BD1458`, `BD1459`.

La ventana reúne el deseo de justicia, la elección y la visita del beneficiado. No corta en el trabajo de decidir; abre la puerta a la confesión.

> Winthrop quería ser justo y no podía permitir que el escrito de Einarsson, ya releído y comentado por muchos, influyera en su decisión. Ésta le dio no poco trabajo. Cierta mañana, Winthrop conversó con su jefe; esa misma tarde Einarsson recibió el encargo oficial de viajar a Wisconsin. La víspera del diecinueve de marzo, día de la partida, Einarsson se presentó en el despacho de Ezra Winthrop. Venía a despedirse y a agradecerle.

#### Cohere

Original: `BD1480` en el acta; `BD1497` en el molde global.

1. `BD1497` · coseno 1.00000000 · escogida: Precisamente por ser hombre del Norte, trató de comprender y justificar la causa del Sur.

2. `BD1490` · coseno 0.49697157: Como buen europeo, yo siempre había presupuesto que la Guerra Civil fue una cruzada contra los esclavistas; usted argumentó que el Sur estaba en su derecho al querer separarse de la Unión y mantener sus instituciones.

3. `BD1412` · coseno 0.47336868: De vieja raíz puritana, oriundo de Boston, le había costado hacerse a los hábitos y prejuicios del Sur.

4. `BD1491` · coseno 0.46839933: Para dar mayor fuerza a lo que afirmaba, me dijo que usted era del Norte y que uno de sus mayores había militado en las filas de Henry Halleck.

5. `BD1413` · coseno 0.45687667: Extrañaba la nieve, pero he observado que a la gente del Norte le enseñan a precaverse del frío, como a nosotros del calor.


Escogida: `BD1497`. Ventana: `BD1495`, `BD1496`, `BD1497`, `BD1498`, `BD1499`.

Conservo el centro: Einarsson nombra la imparcialidad, explica cómo la descubrió y revela cómo la usó. Las otras ventanas describen antecedentes sin cerrar el cálculo.

> Comprendí, mi querido Winthrop, que a usted lo rige la curiosa pasión americana de la imparcialidad. Quiere, ante todo, ser fairminded. Precisamente por ser hombre del Norte, trató de comprender y justificar la causa del Sur. En cuanto supe que mi viaje a Wisconsin dependía de unas palabras suyas a Rosenthal, resolví aprovechar mi pequeño descubrimiento. Comprendí que impugnar la metodología que usted siempre observa en la cátedra era el medio más eficaz de obtener su voto.

### 11. Avelino Arredondo

#### Nemotron

Original: `BD1557` en el acta; `BD1575` en el molde global.

1. `BD1575` · coseno 1.00000000: La parda no lo conocía; Arredondo nunca supo quién era.

2. `BD1610` · coseno 0.57931173: Arredondo no desobedeció.

3. `BD1608` · coseno 0.52143742: Arredondo guardó silencio.

4. `BD1606` · coseno 0.50623487: Arredondo se había quedado escuchando.

5. `BD1547` · coseno 0.50520116 · escogida: Arredondo vivía en las afueras.


Escogida: `BD1547`. Ventana: `BD1545`, `BD1546`, `BD1547`, `BD1548`, `BD1549`.

La casa y la orden de negar su presencia vuelven visible el encierro. Evito servir dos veces el episodio de los soldados, que también aparece entre las candidatas de este motor.

> Clara, que no tenía costumbre de escribir, aceptó el agregado sin protestar. Los dos se querían mucho. Arredondo vivía en las afueras. Lo atendía una parda que llevaba el mismo apellido porque sus mayores habían sido esclavos de la familia en tiempo de la Guerra Grande. Era una mujer de toda confianza; le ordenó que dijera a cualquier persona que lo buscara que él estaba en el campo.

#### Cohere

Original: `BD1590` en el acta; `BD1608` en el molde global.

1. `BD1608` · coseno 1.00000000: Arredondo guardó silencio.

2. `BD1606` · coseno 0.74452488: Arredondo se había quedado escuchando.

3. `BD1610` · coseno 0.65743118: Arredondo no desobedeció.

4. `BD1547` · coseno 0.60059034: Arredondo vivía en las afueras.

5. `BD1632` · coseno 0.59741629 · escogida: Arredondo, que no sentía miedo, sintió una suerte de respeto.


Escogida: `BD1632`. Ventana: `BD1630`, `BD1631`, `BD1632`, `BD1633`, `BD1634`.

Las gradas del templo, las ropas y el respeto suspenden el instante antes del disparo. Evito duplicar el encierro y la burla de los soldados; el segundo pasaje lleva al acto.

> El Te Deum ya había concluido; un grupo de caballeros, de militares y de prelados, bajaba por las lentas gradas del templo. A primera vista, los sombreros de copa, algunos aún en la mano, los uniformes, los entorchados, las armas y las túnicas, podían crear la ilusión de que eran muchos; en realidad, no pasarían de una treintena. Arredondo, que no sentía miedo, sintió una suerte de respeto. Preguntó cuál era el presidente. Le contestaron: -Ése que va al lado del arzobispo con la mitra y el báculo.

### 12. El disco

#### Nemotron

Original: `BD1676` en el acta; `BD1695` en el molde global.

1. `BD1695` · coseno 1.00000000: Dijo, mirándome con fijeza: —Puedes tocarlo.

2. `BD1696` · coseno 0.37761650 · escogida: Ya con algún recelo puse la punta de los dedos sobre la palma.

3. `BD1657` · coseno 0.31986129: Mis ojos ya no ven.

4. `BD1649` · coseno 0.31338221: No sé; nunca lo he visto.

5. `BD1715` · coseno 0.30619277: —Entonces —dije— puedes proseguir tu camino.


Escogida: `BD1696`. Ventana: `BD1694`, `BD1695`, `BD1696`, `BD1697`, `BD1698`.

La ventana pasa del recelo al frío y al brillo, y termina con la mano cerrada. El objeto imposible se siente antes de explicarse.

> Fue sólo entonces que advertí que siempre la había tenido cerrada. Dijo, mirándome con fijeza: —Puedes tocarlo. Ya con algún recelo puse la punta de los dedos sobre la palma. Sentí una cosa fría y vi un brillo. La mano se cerró bruscamente.

#### Cohere

Original: `BD1641` en el acta; `BD1660` en el molde global.

1. `BD1660` · coseno 1.00000000: Una tarde oí pasos trabajosos y luego un golpe.

2. `BD1661` · coseno 0.48464795 · escogida: Abrí y entró un desconocido.

3. `BD1697` · coseno 0.48051226: Sentí una cosa fría y vi un brillo.

4. `BD1720` · coseno 0.44617476: Al volver a mi casa busqué el disco.

5. `BD1717` · coseno 0.43466243: Un hachazo en la nuca bastó y sobró para que vacilara y cayera, pero al caer abrió la mano y en el aire vi el brillo.


Escogida: `BD1661`. Ventana: `BD1659`, `BD1660`, `BD1661`, `BD1662`, `BD1663`.

La puerta y la aparición del desconocido tienen contorno: manta, vejez y cicatriz. Desplazar una frase el centro elimina la explicación previa de la avaricia y deja entrar al visitante.

> Cierro la puerta de mi casa con una piedra para que la nieve no entre. Una tarde oí pasos trabajosos y luego un golpe. Abrí y entró un desconocido. Era un hombre alto y viejo, envuelto en una manta raída. Le cruzaba la cara una cicatriz.

### 13. El libro de arena

#### Nemotron

Original: `BD1764` en el acta; `BD1785` en el molde global.

1. `BD1785` · coseno 1.00000000 · escogida: Siempre en voz baja el vendedor de biblias me dijo: —No puede ser, pero es.

2. `BD1741` · coseno 0.62562023: —Vendo biblias —me dijo.

3. `BD1746` · coseno 0.60360445: —No sólo vendo biblias.

4. `BD1774` · coseno 0.44027697: Luego bajó la voz como para confiarme un secreto: —Lo adquirí en un pueblo de la llanura, a cambio de unas rupias y de la Biblia.

5. `BD1744` · coseno 0.43574482: Como usted ve, no son precisamente biblias lo que me falta.


Escogida: `BD1785`. Ventana: `BD1783`, `BD1784`, `BD1785`, `BD1786`, `BD1787`.

Conservo el centro: el intento fallido, la réplica y la infinitud forman un pequeño arco completo. Las otras candidatas aún pertenecen a la compraventa.

> —Ahora busque el final. También fracasé; apenas logré balbucear con una voz que no era la mía: —Esto no puede ser. Siempre en voz baja el vendedor de biblias me dijo: —No puede ser, pero es. El número de páginas de este libro es exactamente infinito. Ninguna es la primera; ninguna, la última.

#### Cohere

Original: `BD1804` en el acta; `BD1825` en el molde global.

1. `BD1825` · coseno 1.00000000: Busqué el libro imposible, y volví las hojas.

2. `BD1814` · coseno 0.57037178: Volvió las hojas y estudió la carátula con fervor de bibliófilo.

3. `BD1838` · coseno 0.53066690 · escogida: Declinaba el verano, y comprendí que el libro era monstruoso.

4. `BD1771` · coseno 0.50619472: En vano busqué la figura del ancla, hoja tras hoja.

5. `BD1813` · coseno 0.50608934: Fui a mi dormitorio y le traje el dinero y el libro.


Escogida: `BD1838`. Ventana: `BD1836`, `BD1837`, `BD1838`, `BD1839`, `BD1840`.

El insomnio desemboca en una comprensión que también vuelve monstruoso al lector. Es el paso de poseer el libro a tener que librarse de él, con más fuerza que volver sus hojas.

> Nunca se repitieron. De noche, en los escasos intervalos que me concedía el insomnio, soñaba con el libro. Declinaba el verano, y comprendí que el libro era monstruoso. De nada me sirvió considerar que no menos monstruoso era yo, que lo percibía con ojos y lo palpaba con diez dedos con uñas. Sentí que era un objeto de pesadilla, una cosa obscena que infamaba y corrompía la realidad.

## Para llevar

La distancia encuentra parecidos. La lectura encuentra un sitio donde esos parecidos pueden respirar. No hicimos un collar con cinco frases dispersas: abrimos una ventana en el cuento.

Osmancito, con la asistencia de Instinct
