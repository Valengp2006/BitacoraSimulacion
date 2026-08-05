# Actividad 05 — Una contradicción en movimiento

**Sistema:** *Cicatrices* — memoria emergente en Particle Life

[Enlace aplicación](https://editor.p5js.org/Valengp2006/sketches/5F-LRSGI7)

## 1. Intención

> Quiero explorar la tensión entre **la memoria** y **el olvido**, y cómo el colapso no es silencioso, sino contagioso.

La materia intenta conservar las huellas de estructuras que existieron, mientras fuerzas erosivas las obligan a reorganizarse. El sistema nunca reconstruye exactamente el pasado, pero tampoco parte de cero: cada colapso deja un rastro temporal (un vestigio) que sesga dónde y cómo vuelve a formarse la materia.

Con las recientes iteraciones, he profundizado en esta idea: el estrés de la materia ahora es **visible** (calentando su color antes de romperse) y el olvido genera **ondas de choque** (cuando una estructura colapsa, empuja y estresa a sus vecinas). La contradicción ya no es solo visual, es táctil; el usuario puede intervenir como una fuerza externa ("El Dedo del Destino") alterando el delicado equilibrio.

## 2. Tipos y cantidades

| Tipo | Rol | Cantidad inicial | Justificación |
| --- | --- | --- | --- |
| **A — Núcleos** | Semillas de nucleación | 5 | Seleccioné pocos núcleos porque quiero hacer perceptible que la memoria tiene focos limitados, no está en todas partes. Son el ancla del sistema. |
| **B — Constructoras** | Población mayoritaria, forma estructuras | 160 | Conforman el tejido conectivo (dibujan una red orgánica entre vecinas). Son el estado "por defecto" del sistema y la carne de cañón de la erosión. |
| **C — Erosivas** | Introducen fracturas locales | 24 | Seleccioné una minoría que deambula guiada por ruido de Perlin. Quiero hacer perceptible que el olvido es una fuerza constante, orgánica e impredecible. |
| **D — Vestigios** | Rastros de colapsos pasados | 0 al inicio (dinámico) | Nacen del colapso de B. Seleccioné que sean temporales: brillan, mantienen un halo de memoria, atraen nueva materia y eventualmente expiran, volviendo a ser B. |

## 3. Matriz de relaciones (Fuerza y Alcance)

`Fuerza(objetivo ← origen)`: valor `G` (+ atrae, − repele) y radio de alcance máximo `r` (px).
*Existe un núcleo de repulsión duro (`CORE_MIN = 9`) para evitar singularidades.*

| objetivo \ origen | A | B | C | D |
| --- | --- | --- | --- | --- |
| **A** | −0.25 (r 110) | +1.35 (r 230) | 0 | 0 |
| **B** | +0.30 (r 230) | +0.62 (r 80) | **−0.12 (r 95)** | +0.18 (r 190) |
| **C** | 0 | **−0.65 (r 135)** | −0.35 (r 95) | 0 |
| **D** | 0 | +0.55 (r 190) | 0 | −0.15 (r 65) |

**Relación asimétrica y de órbitas:** Las Erosivas (C) repelen fuertemente a las Constructoras (B) al acercarse, pero las B casi no afectan a las C, permitiendo que la erosión penetre las estructuras. Además, introduje un factor de **órbita tangencial** cuando B se acerca a A, creando remolinos en lugar de simples aglomeraciones estáticas.

**Interfaz de Matriz Viva:** Seleccioné exponer esta matriz en la UI no como números, sino como un **mapa de calor interactivo** (Azul = Atracción, Rojo = Repulsión). Esto permite alterar las leyes físicas del universo en tiempo real sin reiniciar el sistema, haciendo perceptible cómo pequeños cambios en la fuerza desatan comportamientos emergentes totalmente distintos.

## 4. Fricción y velocidad máxima

Todas las partículas móviles comparten un límite de velocidad (`MAX_SPEED = 2.3`) y una fricción global (`FRICTION = 0.90`), asegurando un movimiento fluido pero amortiguado.

* **Excepción (A):** Tienen un multiplicador de fricción severo (`0.6`). Seleccioné este valor porque quiero hacer perceptible que los núcleos son el "presente estable" inamovible frente a la tormenta geométrica de los demás tipos.

## 5. Distribución inicial

* **A:** Posiciones pseudoaleatorias, pero con una separación mínima garantizada matemáticamente para que compitan por territorio.
* **B:** Distribución híbrida: una parte se ubica siguiendo un mapa de ruido (creando clústeres orgánicos desde el frame 0) y el resto de forma uniforme aleatoria.
* **C:** Distribución uniforme aleatoria.
* **D:** Comienza vacío.

## 6. Mecanismo de Memoria, Estrés y Ondas de Choque (Regla central)

1. **Acumulación y Tensión Visual:** Cuando una partícula B tiene partículas C cerca, acumula estrés. Visualmente, su color cambia progresivamente de azul a rojo/naranja. *"El sistema avisa visualmente dónde va a ocurrir una ruptura".*
2. **El Colapso:** Al superar el umbral de estrés (`STRESS_THRESHOLD`), existe una probabilidad de colapso. Si ocurre, B emite un destello, se congela y se convierte en D (Vestigio).
3. **Efecto Dominó:** El colapso genera una onda de choque cinética. Las partículas conectadas a la red de la partícula colapsada son empujadas físicamente y reciben una transferencia directa de estrés. *"El olvido es traumático y contagioso; un colapso suele desencadenar otros".*
4. **Decaimiento temporal:** El vestigio (D) vive por un tiempo aleatorio. Durante su vida, su opacidad decae, atrayendo débilmente a nuevas B. Al expirar su contador, "sana" y vuelve a convertirse en una Constructora (B) expulsada en una dirección aleatoria.

## 7. Parámetros constantes vs. variables

**Constantes (Identidad del sistema):**

* Comportamientos de red (hilos entre B y D) y dinámica de halos por densidad.
* La mecánica de ondas de choque y contagio de estrés.
* Interacción de usuario: "El Dedo del Destino" (hacer clic atrae B y repele violentamente C).

**Variables (Cambian la narrativa entre sesiones):**

* La semilla (`seed`) que dicta el ruido de fondo y las posiciones.
* Los valores de la Matriz `M` ajustables por el usuario mediante los sliders de color, que transforman las reglas fundamentales del tejido en vivo.

## 8. Apariencia e interacción

* Fondo muy oscuro con una estela de movimiento sutil (`alpha 28`).
* Partículas dinámicas: dibujan una red conectiva si están a menos de `24px`.
* **Termodinámica visual:** Las B se "calientan" (cambian de color) bajo presión.
* **Clic del mouse (Dedo del destino):** Dibuja un sutil anillo fantasma de 150px. Funciona como una fuerza magnética masiva que acorrala a las Constructoras e intimida/dispersa a las Erosivas, permitiendo al usuario "proteger" memorias o forzar colapsos.

## 9. Autoevaluación

| Criterio | Peso | Valoración | Aporte |
| --- | --- | --- | --- |
| La intención es clara y perceptible en el comportamiento. | 20% | 100% | 20% |
| Los tipos, cantidades, matriz y parámetros están justificados desde la intención. | 25% | 100% | 25% |
| Comprendo y puedo modificar el funcionamiento técnico del sistema. | 20% | 100% | 20% |
| El sistema produce variaciones con una identidad reconocible. | 15% | 100% | 15% |
| Experimenté, comparé, seleccioné y descarté con criterios claros. | 10% | 100% | 10% |
| Puedo distinguir y sustentar lo diseñado y lo emergente. | 10% | 100% | 10% |
| **Total** | **100%** |  | **100%** |
