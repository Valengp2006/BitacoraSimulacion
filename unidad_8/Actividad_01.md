# Bitácora — Unidad 8: Why Bother? ¿Para qué tomarte el trabajo?

**Obra:** *Cauce* 

**Repositorio:** https://github.com/Valengp2006/why-bother

**Versión publicada:** https://valengp2006.github.io/why-bother/

## 1. La obra en pocas líneas
*Cauce* es una pintura fluida en constante movimiento, hecha con simulación en tiempo real. El sistema pone el agua: corrientes, olas y pintura que fluyen solas. La persona pone la dirección: mueve el mouse, mantiene el clic para verter su propia pintura (dorada) y responde preguntas dentro de una narración corta. Cada respuesta cambia el mundo, y al final la obra queda como una imagen que se puede guardar.

## 2. Punto de partida
**Mi postura frente a la IA antes de empezar:** la veo como ayuda para agilizar lo técnico. Me deja imaginar sin quedar limitada a las herramientas que ya manejo, y me hace descubrir qué más puedo hacer. Lo que me deja dudas es que a veces la herramienta falla o interpreta distinto lo que busco.

**Hodgin:** propone que la IA vuelve el arte genérico y que lo que a él le tomó años la IA lo logra en semanas. No lo veo así: la IA me permitió llegar a resultados que antes no habrían sido posibles en este tiempo. 

**Referentes visuales:** arte fluido (acrylic pouring): azules profundos sobre oscuro, blancos y turquesas, venas finas, vetas doradas. Más adelante sumé una imagen de pintura densa con naranjas, dorados y celdas. 

<img width="165" height="195" alt="referente-06" src="https://github.com/user-attachments/assets/84a29bdb-d4af-40a3-9eaa-20ada44e9c26" />
<img width="194" height="258" alt="referente-05" src="https://github.com/user-attachments/assets/12629251-07d9-4bdf-9ec7-80bda56241c4" />
<img width="197" height="265" alt="referente-04" src="https://github.com/user-attachments/assets/815d658c-c691-4858-9919-3c5ab5a09f9a" />
<img width="177" height="406" alt="referente-03" src="https://github.com/user-attachments/assets/b1ebd8bb-63af-4698-8903-2da7aeff695c" />
<img width="215" height="264" alt="referente-02" src="https://github.com/user-attachments/assets/569235db-6873-4934-a33a-77c7b6724087" />
<img width="213" height="280" alt="referente-01" src="https://github.com/user-attachments/assets/268a2d6a-b7e4-4637-a00f-3c2a06c8a342" />

## 3. Cronología del proceso

### Día 1 — Diseño y primeros hitos

- **Interpretación inicial:** "¿Para qué tomarme el trabajo? Porque la automatización hace posible lo que imagino, pero no siempre lo interpreta como lo quise. Lo que me queda es la intención, el criterio para juzgar y la capacidad de entender lo suficiente para corregir."
- **Hipótesis inicial:** una intención clara produce más fidelidad, pero parte de lo que vale la pena conservar aparece en los desvíos.
- **Técnicas (todas del curso):** flow field, steering con wander, flocking, trazas tipo Physarum, partículas, sonificación con Tone.js.
- **Hitos 1 a 6:** esqueleto con Vite + p5 + Tone y despliegue en GitHub Pages; claridad de la intención medida desde el movimiento del mouse; agentes con fidelidad = claridad × susceptibilidad; flocking y clasificación (fiel, desvío, deriva); trazas de tres canales; conservar y soltar con el clic, con registro en JSON.

### Primeras correcciones mías

- Al probar el hito 3: "visualmente está lejos de lo que busco": color muy oscuro, trazos muy finos, movimiento robótico, no se siente como fluido. Se corrigió con las trazas (hito 5).
- Faltaba que se entendiera qué es cada cosa. Pedí una **capa narrativa** y elegí que apareciera de forma contextual.

### Cambio de interpretación

Después de probar la obra sentí que era **superficial en intención y en finalidad**: medía qué tan parejo movía la mano, no lo que quería decir. Volví a las preguntas de la Actividad 3 y la idea cambió:

> Una IA puede ejecutar lo que yo no sé hacer, pero lo que hace que la obra sea mía son las decisiones que tomo mientras se hace. Si distintas decisiones producen obras distintas, el esfuerzo de decidir sigue valiendo la pena.

De ahí salieron: una pintura que se mueve sola, una narración con preguntas cuyas opciones cambian el mundo, sonido de agua y viento, y una obra final guardable.

### Refinamientos posteriores
- **Textura:** la pintura espesa con crestas no me gustó. Pedí algo más fluido, "más cercano a olas". Elegí entre tres variantes y pedí líneas más anchas.
- **Gesto:** soltar con clic derecho me pareció "terrible" y conservar no tenía sentido dentro de la experiencia. Lo reemplazamos por **verter**: mantener el clic vierte pintura dorada, que es lo que pongo yo.
- **Tipografía y título:** elegí Cormorant Garamond. El título *Lo que quise decir* no me convencía; pedí uno más metafórico y elegí *Cauce*.
- **Puntero:** pedí ocultarlo como prueba, y un botón para volver a pantalla completa.
- **Dorado:** pedí que se explicara dentro de la narración qué es y para qué sirve.
- **Decisiones y cierre:** señalé que no veía diferencia entre elegir una opción u otra y que faltaba un cierre. Se rediseñaron los efectos con resultados opuestos y se agregó una secuencia de cierre.

## 4. Cómo funciona
- **Intención:** el mouse sin presionar deja un campo de direcciones; su alcance crece con la claridad.
- **Agentes:** cada uno tiene una susceptibilidad fija (con semilla). *Fidelidad = claridad × susceptibilidad.* Los poco fieles se desvían y divagan; los que tienen vecinos de rumbo parecido forman "desvíos" que fluyen en grupo.
- **Ambiente:** corrientes en forma de remolino (curl de ruido) que cambian con el tiempo, más fuentes que emiten pintura solas.
- **Pintura:** los colores se mezclan como pigmento y la superficie ondula como un mar (olas largas, brillo mojado, refracción).
- **Dorado:** lo que vierto yo. Dura más, atrae lo que pasa cerca y sigue su camino cuando suelto el clic.
- **Parámetros:** todos están en `src/config.js`, cada uno con un comentario de qué hace.
  
## 5. Qué decidí yo y qué delegué
| Decisión | Quién | Notas |
|---|---|---|
| Mi postura frente a la IA y el aspecto a explorar | Yo | |
| La tesis nueva y que la obra pueda refutarla | Yo | Si todas las obras terminan parecidas, Hodgin tiene razón |
| Referentes visuales, paleta y el dorado como lo mío | Yo | Elegí entre propuestas |
| Pedir narración, olas, verter, tipografía, título *Cauce*, puntero oculto, cierre | Yo | Criterio sobre cada resultado |
| Descartar la leyenda de colores; no mostrar las decisiones al final | Yo | |
| Código, valores iniciales de los parámetros, modelo de olas y de pintura | Delegué | |
| Borradores de preguntas, prólogo y epílogo | Delegué (borrador) | La versión final fue revisada y ajustada por mi |

Una limitación que reconozco: no entendía bien el código y cualquier cambio mínimo (un texto, un color) me costaba, aunque podría haberlo hecho manualmente. 

## 6. Cómo verifico la tesis
- El sistema registra cada decisión, cada vertido y cómo queda la obra final. Se descarga con la tecla `L`.
- **Pruebas con otras personas:** jugar sin explicar nada y comparar las obras finales.
- **Se sostiene si** decisiones distintas dan obras claramente distintas. **Se cae si** casi todas se parecen.
- Comprobación previa con el código real: dos recorridos opuestos (*guiarlo, dejarlo pasar, no* y *dejarlo ir, seguirlo, sí*) dieron imágenes claramente distintas: la primera, oscura, escasa y fría; la segunda, llena, cálida y agitada.


## 7. Qué aprendí realmente

Aprendí a usar nuevas herramientas, a diseñar a partir de requisitos y a descubrir posibilidades que no habría imaginado sin ellas. Si volviera a empezar, seguiría delegando lo técnico, pero dedicaría más tiempo a entender lo que estoy haciendo.

## 10. Qué sentido tuvo

Lo que más vale la pena hacer uno mismo es el diseño: buscar referentes, decidir qué hacer y qué emoción transmitir. Es tedioso, pero el resultado lo vale. *Cauce* resume mi postura: el sistema pone el agua y yo decido por dónde corre.

## Autoevaluación:

**Nota:** 5
