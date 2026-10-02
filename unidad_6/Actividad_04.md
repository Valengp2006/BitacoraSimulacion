[Enlace repositorio del proyecto](https://github.com/Valengp2006/contemplar-lo-infinito)

Nota: Bitácora completa y evidencias en el repositorio del proyecto

## Autoevaluación (Actividad 04)

> Puntajes decididos por la autora; se sustentan durante la presentación. Los ensayos con la
> música están en la tabla "Registro de ensayos" de la [bitácora](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/bitacora.md).
>
> **Ensayos:** el 1 de octubre se hicieron 4 ensayos en vivo de la pieza completa, con todos los
> controles, y funcionaron bien. Hay dos videos:
> - [uno de esos cuatro ensayos (Google Drive)](https://drive.google.com/file/d/1hiOvklknYdQwIyDW1IOgFxDub6h1l9Py/view?usp=drive_web), antes del ajuste de los cuerpos;
> - [un ensayo completo posterior](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/ensayo-2026-10-01.mp4), con los cuerpos ya
>   ajustados.

| Criterio | Puntaje | Resumen |
|---|---|---|
| 1. Cumplimiento del encargo | 25 / 25 | Web, tiempo real (120 fps con 200.000 agentes), publicado; la pieza completa se interpretó en vivo en 4 ensayos |
| 2. Comprensión y verificación | 25 / 25 | Sistema documentado agente por agente; cinco predicciones verificadas con mediciones |
| 3. Diseño e intención | 25 / 25 | Cada algoritmo tiene un papel ligado a la música; las decisiones se ajustaron comparando el resultado con la intención |
| 4. Interpretación humana | 25 / 25 | Score por sección y controles continuos y puntuales; 4 ensayos en vivo; el instrumento se ajustó según lo observado al tocar |
| **Total** | **100 / 100** | |

### 1. Cumplimiento del encargo — 25 / 25

*Mi instrumento utiliza tecnología web, funciona en tiempo real y permite interpretar la pieza
musical elegida.*

- **Tecnología web.** Three.js 0.185.1 con WebGPU, en el navegador. Está publicado en GitHub
  Pages y se despliega solo con cada cambio en `main`. El sitio en vivo usa el mismo archivo de
  build que la versión actual del código.
- **Tiempo real.**
  - En la Mac de la autora corre a 120 fps, el tope de la pantalla, incluso con 200.000
    agentes (medido con el contador de fps del modo desarrollo).
  - En el banco de pruebas, la simulación de 200.000 agentes con huella, cuerpos y pulsos
    toma ~1,8 ms por paso, menos del 15 % del tiempo disponible a 60 fps.
- **Interpreta la pieza.**
  - La autora tocó la pieza completa en vivo en **4 ensayos** (1 de octubre), con todos los
    controles, y el sistema funcionó bien ([registro de ensayos](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/bitacora.md)).
  - La música suena de fondo desde el clic de inicio.
  - El recorrido emocional de la obra está traducido en niveles y controles (ver el [score](https://github.com/Valengp2006/contemplar-lo-infinito#score-de-interpretación)).
  - El sistema nunca analiza el audio: la intérprete escucha y decide.
- **Evidencias:** [`05-nivel4-nebulosa.jpg`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/05-nivel4-nebulosa.jpg),
  [`04-modo-desarrollo.jpg`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/04-modo-desarrollo.jpg) (métricas a 120 fps).
- **Por qué 25:** se cumplen las tres condiciones del encargo, con evidencia de cada una. El
  único defecto conocido, en los bordes, es pequeño y en los ensayos se integró en la
  interpretación sin afectarla (ver [Limitaciones conocidas](https://github.com/Valengp2006/contemplar-lo-infinito#limitaciones-conocidas)).

### 2. Comprensión y verificación — 25 / 25

*Puedo explicar cómo está construido el sistema, qué perciben los agentes y cómo calculan sus
acciones. Puedo predecir y verificar los cambios al modificar un parámetro.*

- Lo que percibe cada agente y cómo calcula su acción está descrito en la sección
  [Cómo funciona](https://github.com/Valengp2006/contemplar-lo-infinito#cómo-funciona) del README.
- **Predicciones verificadas con el banco de pruebas**, que ejecuta los mismos shaders del
  navegador y mide velocidad, valores inválidos y acumulación en los bordes:

| Cambio | Predicción | Resultado medido |
|---|---|---|
| Apagar la cohesión | Los agentes irán más rápido, porque la cohesión los frenaba en los grupos | La velocidad media sube de 0,0089 a 0,0125 (+40 %) |
| Dejar solo el flow field | Los agentes se acumularán en los bordes, porque las corrientes no empalman | 18,5 % de los agentes en los bordes (lo esperado es ~4 %) — [`11`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/11-prueba-bordes-solo-flow.png) |
| Apiñamiento relativo a la densidad media | El flocking se comportará igual con cualquier cantidad de agentes | Velocidad media de 0,0082 a 0,0085 con 5k, 20k, 80k y 200k; desaparecen las líneas de la rejilla — [`02`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/02-saturacion-antes-despues.png) |
| Medir la huella respecto a una memoria fija | Con memoria larga la huella se acumulará y brillará más | Memoria baja: solo polvo; alta: bruma violeta y azul — [`08`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/08-memoria-baja-media-alta.png) |
| Cuerpos más lentos que los agentes | La materia podrá seguir a los cuerpos y el sistema será visible | Con velocidad 0,015 (por debajo del 0,035 de los agentes) se ven tres núcleos que se orbitan — [`10`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/10-sistema-de-cuerpos.jpg) |

- El panel del modo desarrollo permite cambiar cualquier parámetro en vivo y observar el
  efecto.
- **Por qué 25:**
  - cada cambio importante se hizo prediciendo su efecto y midiéndolo antes de aceptarlo;
  - las decisiones técnicas están justificadas por escrito, incluido el flocking por campos en
    lugar de vecinos individuales (ver la "Decisión técnica" en [Cómo funciona](https://github.com/Valengp2006/contemplar-lo-infinito#cómo-funciona) y la [bitácora](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/bitacora.md)).

### 3. Diseño e intención — 25 / 25

*Puedo justificar la selección y combinación de comportamientos y relacionarlos con mi
interpretación musical.*

**Cada algoritmo tiene un papel conceptual:**

| Algoritmo | Papel |
|---|---|
| Flow field | El rumbo del universo; viaje y corrientes invisibles |
| Flocking | La conexión y la pertenencia |
| Steering | Las decisiones individuales, la búsqueda (atracción) y la incertidumbre (wander) |
| Physarum | La memoria y la nostalgia: huellas que persisten |

**El arco de la música se traduce en estados visuales:**

| Música | Imagen |
|---|---|
| Calma | Pocas presencias |
| Curiosidad | Grupos |
| Asombro | Corrientes |
| Nostalgia | Huellas persistentes |
| Clímax | Inmensidad, color y resplandor |
| Final | Un único punto, como al inicio |

Evidencia: [`07-revelacion-niveles.png`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/07-revelacion-niveles.png).

**Decisiones de diseño que salieron de mirar el resultado y compararlo con la intención:**
- *"Debe sentirse como un espacio exterior vivo que respira"* → se eliminó la saturación
  ([`01`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/01-saturacion-200k-antes.jpg) →
  [`03`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/03-calibracion-progresion.png)).
- *"Se ve biológico, no como el espacio"* → profundidad, escala, filamentos y color por
  comportamiento.
- *Cuerpos celestes* → núcleos que emergen de los agentes, no dibujados, para respetar la
  regla de no literalidad ([`09`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/09-cuerpos.png)).

**El color depende del comportamiento:**
- violeta en los agentes rápidos;
- magenta en las concentraciones;
- dorado solo en el clímax.

La paleta no cambia de colores a lo largo de la pieza: cambia la **cantidad** de color.

**Por qué 25:**
- la combinación de comportamientos forma una sola cadena con sentido musical;
- cada cambio visual se decidió comparando el resultado con la intención de la obra;
- en los ensayos, la calibración de color funcionó bien.

### 4. Interpretación humana — 25 / 25

*Mi score y mis controles permiten conducir el sistema en vivo y responder a su
comportamiento.*

- **[Score](https://github.com/Valengp2006/contemplar-lo-infinito#score-de-interpretación):** una tabla por sección musical con el nivel y las acciones.
- **Controles:**
  - **Continuos:** RUMBO, ATRACCIÓN y MEMORIA, para responder a lo que hace el sistema en
    cada momento.
  - **Puntuales:** PULSO, REVELACIÓN, CUERPO, SISTEMA, DISOLVER y FINAL, para los momentos
    clave de la música.
- **Todo cambio es suave:**
  - la revelación tarda ~15 s;
  - la atracción crece y se libera;
  - los cuerpos se forman y se disuelven.

  Así se puede intervenir en vivo sin saltos bruscos.
- **El sistema sigue vivo sin tocarlo.** RUMBO y ATRACCIÓN vuelven solos a neutro, y la
  intérprete reacciona a lo que emerge.
- **El modo performance deja la pantalla limpia.** Sin cursor ni paneles; solo el nombre del
  control, tenue, durante unos segundos.
- **Evidencias:** [`06-pulso-reorganizacion.jpg`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/06-pulso-reorganizacion.jpg)
  (efecto del pulso) y [`10-sistema-de-cuerpos.jpg`](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/10-sistema-de-cuerpos.jpg).
- **Ensayos:** 4 ensayos en vivo de la pieza completa (1 de octubre), con todos los controles.
  El sistema respondió bien y la calibración de color funcionó. Los pequeños defectos de los
  bordes se integraron en la interpretación. Uno de ellos está grabado:
  [video en Google Drive](https://drive.google.com/file/d/1hiOvklknYdQwIyDW1IOgFxDub6h1l9Py/view?usp=drive_web).
- **Respuesta a lo observado al tocar:** tras los ensayos, la autora pidió que los cuerpos
  se formaran más rápido y fueran más grandes, y que la dispersión fuera más impactante. El
  instrumento se ajustó en consecuencia
  ([evidencia](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/12-cuerpo-formacion-y-estallido.png)).
- **Por qué 25:** el score y los controles permitieron conducir la pieza completa en vivo en
  4 ensayos, y el instrumento evolucionó a partir de lo que la intérprete observó al tocar.
- **Ensayo grabado:** la pieza completa con la música, después del ajuste de los cuerpos
  ([video, 6:39](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/ensayo-2026-10-01.mp4);
  [fotograma del clímax](https://github.com/Valengp2006/contemplar-lo-infinito/blob/main/docs/evidencias/13-ensayo-climax.jpg)). Entre 5:00 y 5:05 aparece por
  accidente el menú de emojis de macOS; es un error de la grabación, no del instrumento.
