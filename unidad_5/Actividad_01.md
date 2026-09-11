# Concepto de diseño

## Principio transversal: nunca hay "reset", solo reinterpolación de parámetros

La decisión de fondo: el sistema es **una sola simulación continua** que corre de principio a fin de los 13 slides. Cada slide no dispara una animación nueva desde cero — define un **estado objetivo** (número de clusters, fuerzas de atracción, grosor/opacidad de aristas, posición de retiro si hay foto) y el motor de fuerzas interpola suavemente hacia ese estado cuando cambias de slide (adelante o atrás).

**Por qué:** si cada slide "reiniciara" el grafo, estaría ilustrando *reemplazo* (una generación borra a la anterior para dar paso a la siguiente), que es justo lo opuesto al concepto. Al interpolar sin romper la simulación, el sistema **recuerda** su estado anterior mientras muta — eso es "relevo": la generación nueva no borra a la vieja, la hereda y la transforma en tiempo real. Navegar hacia atrás no "rebobina" una animación, solo reapunta los parámetros al estado previo — mismo motor, sin necesidad de una lógica de reversa aparte.

## Acto 1 — Origen (1–5): fisión de un núcleo único

- **Slide 1** (sin foto): un solo núcleo denso, orbital — la universidad/auditorio como punto de origen indiferenciado.
- **1→2** (foto: auditorio de graduación): el núcleo se retrae a un marco/borde alrededor de la foto — el sistema cede el centro a la evidencia real de que ese "gran auditorio" ya existe y está lleno de gente.
- **2→3** (sin foto): reexpansión, y aquí ocurre la primera fisión — el núcleo empieza a partirse en tres subclusters (academia / industria / ciudad). Argumento narrativo: la pregunta retórica del slide 2 ("¿un auditorio solo para formaturas?") se responde visualmente — el espacio único se revela como tres fuerzas que ya convivían ahí sin saberlo.
- **4, 5** (foto): retiro/expansión alternado, pero la triada ya no vuelve a fusionarse — cada retiro conserva la separación en 3, cada vez más definida. El acto cierra con los tres clusters estables.

## Acto 2 — Comunidad y confianza (6–9): las aristas cargan el argumento

- Los nodos ya no cambian de cantidad ni de agrupación — lo que evoluciona es **grosor y opacidad de las conexiones** dentro de cada cluster y, hacia el final, las primeras conexiones tímidas *entre* clusters.
- **Por qué solo aristas y no posiciones:** la confianza no se ve como movimiento sino como densidad de vínculo — es el correlato visual más directo de "comunidad y confianza" sin inventar una metáfora nueva.
- **Slide 8** (foto): retiro habitual, pero el grosor/opacidad acumulado *no se resetea* al retraerse — la evidencia visual de que el progreso de confianza sigue "corriendo" aunque no esté en primer plano.
- **9→10** es la transición más importante del acto, ver abajo.

## Acto 3 — Relevo (10–12): recategorización, no solo reconexión

- Aquí hay un cambio de gramática más explícito: pasar de "3 clusters institucionales" a "2 especies generacionales". No puede ser solo un salto silencioso — la transición 9→10 debe mostrarse como una **recomposición visible**: los nodos existentes migran y se reetiquetan (cambio de tamaño/forma/temperatura de color) en vivo, no aparecen nodos nuevos de la nada.
- **Por qué:** si los nodos de la triada simplemente desaparecieran y aparecieran nodos "de relevo" nuevos, estarías narrando sustitución. Migrar los *mismos* nodos a una nueva clasificación argumenta que las mismas personas/instituciones que construyeron confianza en el Acto 2 son las que ahora se organizan en generaciones que se entretejen — continuidad de identidad, cambio de rol.
- **10, 11** (sin foto): máxima actividad — aristas cruzando entre especies, mayor protagonismo visual del grafo porque es el clímax conceptual de la charla.
- **12** (foto): retiro, pero el entretejido ya no se separa de nuevo — a diferencia de los actos 1–2, aquí el retiro conserva el cruce entre especies visible en el marco, porque ya no hay vuelta atrás a la separación.

## Acto 4 — Apertura (13): de orgánico a ordenado

- Única transición donde el grafo cambia de **lógica de fuerzas**, no solo de parámetros: pasa de fuerzas orgánicas (atracción/repulsión libre) a posiciones objetivo fijas tipo grilla/portal — los nodos hacen *lerp* hacia celdas ordenadas.
- **Por qué:** el cierre de la charla es un llamado a la acción concreto (el QR), no una idea abierta. Que el caos orgánico "resuelva" en orden visual argumenta que el relevo generacional, una vez tejido, produce estructura aprovechable — no solo conexión, sino sistema.

## Nota de ritmo

Duración de transición: 1.5–2.5s con easing (nunca instantáneo, nunca tan largo que compita con quien habla), y micro-movimiento idle constante incluso sin cambio de slide, para que el grafo se sienta vivo sin robar atención.
