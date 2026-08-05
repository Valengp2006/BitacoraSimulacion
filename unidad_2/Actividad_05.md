
# Actividad 05 — Una contradicción en movimiento

**Sistema:** *Cicatrices* — memoria emergente en Particle Life

## 1. Intención

> Quiero explorar la tensión entre **la memoria** y **el olvido**.

La materia intenta conservar las huellas de estructuras que existieron, mientras fuerzas erosivas las obligan a reorganizarse. El sistema nunca reconstruye exactamente el pasado, pero tampoco parte de cero: cada colapso deja un rastro que sesga dónde y cómo vuelve a formarse la materia. La memoria no está programada como dato — **emerge de que un tipo de partícula queda casi congelado en el lugar donde algo se rompió, y sigue atrayendo débilmente a las demás.**

La contradicción no depende de color ni de nombre: está en las reglas — quién se mueve, quién queda fijo, y qué tan rápido se "olvida" (decae) una atracción.

## 2. Tipos y cantidades

| Tipo | Rol | Cantidad inicial | Justificación |
|---|---|---|---|
| **A — Núcleos** | Semillas de nucleación | 4 | Seleccioné pocos núcleos porque quiero hacer perceptible que la memoria tiene focos limitados, no está en todas partes. Espero que produzca competencia visible entre polos de crecimiento. |
| **B — Constructoras** | Población mayoritaria, forma estructuras | 140 | Seleccioné una mayoría clara porque quiero hacer perceptible que la construcción es el estado "por defecto" del sistema. Espero que produzca agregados visibles alrededor de A y D. |
| **C — Erosivas** | Introducen fracturas locales | 25 | Seleccioné una minoría móvil y persistente porque quiero hacer perceptible que el olvido es un proceso continuo, no un evento raro. Espero que produzca desgaste gradual, no destrucción instantánea. |
| **D — Vestigios** | Rastros de colapsos pasados | 0 al inicio, hasta 60 (dinámico) | Seleccioné que D **no exista al inicio sino que nazca de B** porque quiero hacer perceptible que la memoria no es un dato precargado sino una consecuencia del colapso. Espero que produzca un ciclo visible: construcción → fractura → vestigio → nueva construcción cercana. |

## 3. Matriz de relaciones

`Fuerza(objetivo ← origen)`: valor `G` (+ atrae, − repele, 0 indiferente) y radio de interacción `r` (px). Núcleo de repulsión fijo `r_core = 8px` para todos los pares (evita colapso a un punto).

| objetivo \ origen | A | B | C | D |
|---|---|---|---|---|
| **A** | −0.6 (r 30) | 0 | 0 | 0 |
| **B** | **+1.2 (r 220)** | +0.35 (r 70) | **−1.5 (r 45)** | +0.5 × decay(t) (r 160) |
| **C** | 0 | **0** ← asimetría clave | −0.4 (r 40) | +0.25 (r 120) |
| **D** | 0 | 0 | 0 | −0.2 (r 25) |

**Relación asimétrica central (condición #5):** `B←C = −1.5` (fuerte repulsión) pero `C←B = 0` (indiferencia total). Las erosivas nunca "sienten" a las constructoras: deambulan libres mientras las estructuras sí las evitan. Esto evita que la erosión se vuelva un conflicto mutuo — es unidireccional, como el paso del tiempo.

Seleccioné esta matriz porque quiero hacer perceptible que atracción, repulsión e indiferencia coexisten en el mismo sistema sin jerarquía visual (ningún color "gana"). Espero que produzca ciclos de agregación-fractura-dispersión sin que ningún tipo domine permanentemente.

## 4. Fricción y velocidad máxima (por tipo)

| Tipo | Fricción | Vel. máx. | Justificación |
|---|---|---|---|
| A | 0.92 | 0.15 | Seleccioné valores extremos porque quiero hacer perceptible que los núcleos son casi inmóviles — son el "presente estable" contra el que todo lo demás se mueve. |
| B | 0.85 | 2.2 | Espero que produzca desplazamiento ágil, capaz de responder rápido a nuevos puntos de atracción (nucleación o vestigios). |
| C | 0.90 | 1.8 | Movimiento persistente pero no errático: erosiona por recorrido sostenido, no por explosión. |
| D | 0.97 | 0.25 | Seleccioné fricción muy alta porque quiero hacer perceptible que un vestigio "se queda" — es memoria porque no se mueve, no porque tenga un dato guardado. |

## 5. Distancias de interacción

Definidas en la tabla de la matriz (columna `r`). Principio de diseño: **la erosión (C→B) actúa a corto alcance (45px)** — el olvido es local y progresivo — mientras que **la memoria (D→B) actúa a alcance medio-largo (160px)** — un vestigio influye una zona más amplia que el punto exacto donde ocurrió. Esa asimetría de escala es intencional: el recuerdo se "difumina" espacialmente antes de desaparecer del todo.

## 6. Distribución inicial

- **A:** posiciones pseudoaleatorias con separación mínima garantizada (evita núcleos superpuestos).
- **B, C:** distribución uniforme aleatoria en todo el lienzo.
- **D:** vacío — se puebla únicamente por conversión de B.

Seleccioné distribución uniforme (no clusters predefinidos) porque quiero hacer perceptible que cualquier estructura visible es resultado del sistema, no de una composición inicial. Espero que produzca configuraciones distintas en cada semilla sin perder el mismo comportamiento general.

## 7. Mecanismo de memoria (regla central del sistema)

1. Cada partícula B acumula **estrés** cuando ≥2 partículas C están dentro de su radio de erosión (45px). El estrés decae si la presión cesa.
2. Al superar el umbral, B **se convierte en D**: velocidad a casi cero, `decayStrength = 1.0`.
3. `decayStrength` decae exponencialmente (×0.9985/frame) hasta un **piso de 0.12** — nunca llega a cero. *"El tiempo erosiona las formas, pero nunca consigue borrar completamente su recuerdo."*
4. La atracción D→B se multiplica por `decayStrength`: un vestigio reciente atrae con fuerza, uno antiguo casi no influye, pero jamás desaparece del todo.
5. Si la población de D supera el tope (60), el vestigio **más antiguo vuelve a ser B** — recicla el sistema y da lugar a "reconstrucción diferente" en vez de acumulación infinita.

Este mecanismo es lo que traduce "memoria vs. olvido" en reglas verificables, no en una metáfora visual suelta.

## 8. Parámetros constantes vs. variables

**Constantes (definen la identidad del sistema, condición #8):**
- Número de tipos (4) y su rol funcional.
- Forma (círculos con halo), paleta (fondo oscuro, A dorado, B azul pálido, C rojo cálido, D violeta grisáceo que se desvanece con `decayStrength`).
- Radio de núcleo de repulsión (8px) y tope de D (60).
- La regla de conversión y de decaimiento.

**Variables (cambian entre ejecuciones, condición #6):**
- Semilla aleatoria → posiciones iniciales de A, B, C.
- Cantidad inicial de A (3–6) → número de polos de memoria en competencia.
- Momento y ubicación de las conversiones B→D (siempre estocástico, nunca el mismo mapa dos veces).

## 9. Apariencia e interacción

- Fondo oscuro con leve estela (trail) para sugerir observación microscópica/lenta.
- Halo suave por partícula; opacidad de D ligada a `decayStrength` (memoria que se desvanece visualmente, no solo en la física).
- **Clic del mouse:** libera una ráfaga breve de partículas C cerca del cursor — permite al espectador inducir erosión y ver el ciclo de colapso→vestigio→reconstrucción a demanda.

## 10. Autoevaluación 


