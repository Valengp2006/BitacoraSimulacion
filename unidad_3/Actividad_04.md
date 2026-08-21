# Bitácora de Proyecto: Singularidad

### 1. Instrumento Funcional y Publicado

* **URL Pública:** `[https://valengp2006.github.io/Unidad_03_simulacion/]`
* **Modos implementados:**
  * **Modo LAB:** Un panel de diagnóstico que permite aislar las fuerzas mediante sliders interactivos y probar los 7 estados gravitacionales base para verificar la matemática del sistema.
  * **Modo PERFORMANCE:** Un lienzo puramente visual, donde se ocultan todos los elementos de la interfaz (textos, HUD, cursor). Se activa presionando `P`, cediendo el control total a las transiciones orgánicas operadas por el teclado.

### 2. Mapa del Sistema

* **Estado:** La simulación mantiene el estado de 131,072 partículas (posición y velocidad) alojadas en la memoria de la GPU usando `positionBuffer` y `velocityBuffer`. Archivo: `src/simulation/createSimulation.js`.
* **Fuerzas:** El comportamiento emerge del cálculo vectorial de fuerzas de gravedad (radial), rotación (vórtice), viento constante y fricción (drag) dentro de un Compute Shader. Archivo: `src/simulation/createSimulation.js`.
* **Integración:** Se utiliza el método semi-implícito de Euler. La aceleración modifica la velocidad ($v_{nueva} = v_{actual} + F \cdot dt$), limitando el vector según `maxSpeed`, y finalmente la velocidad actualiza la posición ($p_{nueva} = p_{actual} + v \cdot dt$). Archivo: `src/simulation/createSimulation.js`.
* **Render:** Renderización mediante `InstancedMesh` y `SpriteNodeMaterial`. Se programó directamente en el *shader* una termodinámica visual de 4 colores dependiente de la aceleración, y un "Horizonte de Eventos" mediante máscaras matemáticas de opacidad (las partículas desaparecen al acercarse al punto cero). Archivo: `src/simulation/createSimulation.js`.
* **Controles:** La orquestación en vivo (teclas 1-7), la interpolación de estados asintótica (`lerp`) y la inmovilización del atractor residen en el flujo principal. Archivo: `src/main.js`.

### 3. Ficha de Fuerzas

* **Fuerza Central:** Fuerza Radial Extrema (Singularidad / Supernova).
* **Ecuación/Descripción Direccional:** Se calcula un vector direccional normalizado desde la partícula hacia el atractor, el cual se divide por la distancia al cuadrado (imitando la ley de la gravitación universal) y se multiplica por la intensidad de la fuerza.

$$F_{radial} = \left( \frac{\vec{d}_{normalizada}}{distancia^2} \right) \cdot radialStrength$$

* **Parámetros vinculados:** `radialStrength` (Atracción/Repulsión), `vortexStrength` (Momento angular) y `dragCoefficient` (Fricción espacial).
* **Decisiones de Diseño:** Para mantener la integridad de un "Agujero Negro", se decidió fijar el atractor en las coordenadas origen $(0,0,0)$ durante el modo PERFORMANCE. Se anuló la influencia del mouse para que el comportamiento visual surja puramente de las matemáticas y no de dibujar trayectorias a mano.

### 4. Registro de Pruebas

* **Pruebas de Estados (Modo LAB):**
Se evaluaron los 7 estados que componen la obra desde el panel de control para comprobar los balances de fricción y atracción. Al presionar los botones del panel, los sliders actualizan sus valores revelando las tensiones de la materia (ej. *Disco de Acreción* opera con alta rotación y baja fricción).
* **Prueba Específica (El Clímax - Escena 7 Supernova):**
 * *Predicción inicial:* Al presionar la tecla 7, la interpolación asintótica (`lerp`) llevaría el valor de atracción (+15) a repulsión masiva (-40) progresivamente, creando una explosión expansiva.
 * *Análisis del resultado:* La interpolación matemática arruinó el efecto. Al bajar lentamente de manera progresiva (pasando de 15 a 10, a 5...), la gravedad seguía atrayendo y el temporizador cortaba la escena antes de cruzar hacia la repulsión negativa.
 * *Modificación:* Se rompió deliberadamente la interpolación en el código exclusivamente para la Escena 7. Se programó un *bypass* que asigna $-40.0$ al `radialStrength` y $0.0$ al `dragCoefficient` en un solo frame, logrando un estallido masivo y violento comprobable en tiempo real.


### 5. Score Visual (Interpretación de *LesAlpx* de Floating Points)

El instrumento no reacciona automáticamente al audio; las fuerzas son conducidas manualmente estructurando una curva de tensión de 7 fases:

* **0:00 - 0:44 (Materia oscura y corrientes):** La percusión sutil arranca. Altísima fricción, velocidad lenta. Las partículas giran lentamente revelando colores fríos.
* **0:44 - 1:52 (Espiral y Disco de Acreción):** Entra el bajo y el *groove* principal. Se baja la fricción y aumenta radicalmente la rotación, formando el anillo incandescente.
* **1:52 - 2:15 (Órbita Crítica y Colapso):** Tensión máxima. Se anula por completo la rotación. Se aplica succión masiva hacia el centro; las partículas desaparecen en el horizonte de eventos.
* **2:15 (El Clímax Rítmico):** ¡SUPERNOVA! Explosión e interrupción de la gravedad (repulsión instantánea) coincidiendo con la ruptura sonora.
* **Segunda mitad de la pista:** El sistema decae automáticamente. La interpretación se vuelve libre, alternando entre las escenas 3, 4 y 5 para crear pulsos de materia según las variaciones de los sintetizadores.

### 6. Bitácora de IA

* **Prompts Relevantes:** "Quiero que se vea más similar al referente... que parezca más un agujero negro", "Las etapas de la 5 a la 7 se ven mal, no tienen lógica, además supernova sigue sin funcionar", "Recuerda que finalmente quedaron 7 estados, debe verse tanto en el modo lab como performance, y en performance debe eliminarse el texto".
* **Cambios Aceptados & Correcciones:**
 * Se diseñó una termodinámica visual de 4 umbrales de color y se integraron transiciones asintóticas para 7 escenas.
 * Se corrigieron errores de despliegue (build fallido) en *GitHub Actions* al detectar la ausencia de funciones matemáticas como `smoothstep` en las importaciones de TSL.

* **Decisiones de Rechazo (Criterio Propio):** La IA sugirió una funcionalidad donde la paleta de color y el campo gravitacional seguían el movimiento y las coordenadas del cursor del mouse.
 * *Decisión:* Se rechazó la propuesta ejecutando un *rollback* de los archivos.
 * *Justificación:* Esta interacción desvirtuaba la obra, acercándola de nuevo al ejercicio genérico base de la clase y destruyendo el concepto gravitacional de la Singularidad centralizada. El comportamiento debe emerger de la propia dinámica, no de "pintar" arrastrando el mouse.

### 7. Autoevaluación Ponderada

| Criterio | Peso | Valoración | Evidencia concreta |
| --- | --- | --- | --- |
| **Trazabilidad y comprensión del sistema** | 25 | 100 | (Código documentado: lógica de modos en `main.js` y shaders en `createSimulation.js)[https://github.com/Valengp2006/Unidad_03_simulacion] |
| **Verificación del algoritmo de fuerzas** | 25 | 100 | (Video modo LAB)[https://youtu.be/E5AmwCKiFI8] |
| **Diseño de fuerzas e intención** | 20 | 100 | Aplicación del horizonte de eventos y la manipulación de rotación cero / gravedad masiva en la escena 6.|
| **Instrumento, score e interpretación** | 15 | 100 | (Video modo performance)[https://youtu.be/fxjNcKm8FrQ] |
| **Experimentación y criterio frente a la IA** | 10 | 100 | Documentado en la sección 6. |
| **Entrega técnica y documentación** | 5 | 100 | (Documentación)[https://github.com/Valengp2006/BitacoraSimulacion/tree/main] |
| **Total Puntos** | **100** | **100** |  |
