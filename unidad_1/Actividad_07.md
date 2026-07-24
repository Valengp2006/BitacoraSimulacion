# Actividad 07 — Navegar la incertidumbre

## Idea inicial

El objetivo del ejercicio era representar la incertidumbre sin ilustrarla de manera literal.

En lugar de utilizar elementos reconocibles, decidí trabajar con un lenguaje visual completamente geométrico, inspirado en composiciones abstractas, donde pequeñas figuras simples se organizan progresivamente hasta formar estructuras mayores.

La intención fue que el visitante percibiera cómo distintas reglas probabilísticas producen organizaciones diferentes dentro del mismo sistema visual.

## Referentes

Inicialmente exploré sistemas relacionados con el espacio y la formación de galaxias.

Después de varias pruebas observé que la narrativa terminaba siendo demasiado literal y el comportamiento probabilístico pasaba a un segundo plano.

Por esta razón decidí cambiar completamente la propuesta hacia una composición abstracta basada en módulos geométricos.

Los referentes principales fueron:

* Patrones geométricos modulares
* Arte generativo
* Composiciones constructivistas
* Diseños editoriales abstractos

La intención fue trabajar únicamente con relaciones entre formas, orientación, densidad y agrupación.

## Evolución del proyecto

### Versión 1

La primera versión consistía únicamente en una retícula.

Cada celda elegía aleatoriamente una figura entre cuatro posibilidades.

Todas las decisiones eran completamente independientes.

**Resultado:**

* Demasiado uniforme
  sin lectura visual
* No existía sensación de organización

**Lo que aprendí:**

La aleatoriedad uniforme produce ruido visual, pero no genera estructuras reconocibles.

#### Imagen primer versión:

<img width="301" height="536" alt="Captura de pantalla 2026-07-23 a la(s) 10 40 22 a m" src="https://github.com/user-attachments/assets/7bb5481f-73df-4a65-93d2-903b0f7a5040" />

### Versión 2

La segunda versión comenzó a utilizar ruido Perlin.

En lugar de elegir completamente al azar, las figuras empezaron a compartir cierta orientación con las vecinas.

Esto generó regiones donde aparecían pequeñas tendencias.

**Resultado:**

* Aparecieron zonas similares
* Las transiciones fueron más suaves
* Comenzó a sentirse un patrón

**Problema encontrado:**

Todavía no existían composiciones claramente identificables.

#### Video segunda versión:

<img width="390" height="690" alt="Grabación de pantalla 2026-07-23 a la(s) 10 45 48 a" src="https://github.com/user-attachments/assets/20b1f0a1-ad43-49ea-a5e6-ae1b1f6870c9" />

### Versión 3

Se incorporó un segundo nivel de organización.

Además de las figuras individuales comenzaron a aparecer composiciones geométricas grandes.

Cada composición modifica temporalmente las reglas de las celdas que contiene.

En lugar de dibujar una figura grande, el sistema reorganiza cientos de módulos pequeños.

Esto permitió obtener imágenes similares a composiciones editoriales abstractas.

#### Video tercera versión:

<img width="388" height="692" alt="Sin título (1080 x 1920 px) (3)" src="https://github.com/user-attachments/assets/671256f4-0254-4ffc-b31b-4b98b96bbc08" />

### Versión final

La versión final integra todos los conceptos en un mismo sistema.

Las composiciones aparecen siguiendo distintas distribuciones probabilísticas mientras las figuras continúan reorganizándose continuamente.

El visitante nunca dibuja directamente.

Su presencia modifica las probabilidades del sistema y visualmente hay un aumento de tamaño y color.

[Enlace a la aplicación en p5.js](https://editor.p5js.org/Valengp2006/sketches/8bOUuDEUu)

#### Video versión final:

<img width="388" height="692" alt="Sin título (1080 x 1920 px) (4)" src="https://github.com/user-attachments/assets/ece3bac0-1950-41e1-81e0-0993279887e4" />

> [!NOTE]
> El enunciado original define cuatro etapas continuas, donde la última agrupa "Excepción e influencia". Aquí se documentan como dos momentos separados (4 y 5) para explicar cada mecanismo con claridad, pero en el sketch ambos ocurren dentro de la misma fase final, sin corte entre ellos.

### 1. Posibilidad

Al comenzar todas las figuras tienen la misma probabilidad de aparecer.

No existen regiones dominantes.

Cada módulo toma decisiones independientes.

Visualmente se percibe un campo caótico.

### 2. Tendencia

Se genera un campo de ruido Perlin de baja frecuencia sobre la retícula. A diferencia de un valor aleatorio independiente por celda, el ruido Perlin varía suavemente en el espacio, por lo que celdas vecinas obtienen valores parecidos y terminan compartiendo orientación.

Este es el mecanismo **estructural** de la etapa: no se usa aquí de forma decorativa, sino para producir la correlación espacial que agrupa los módulos. El uso "orgánico" del ruido (respiración de brillo, escala, rotación) es un efecto adicional que se mantiene activo en todas las etapas, sin afectar la posición de ningún elemento.

**Concepto utilizado:**

- Ruido Perlin (campo de correlación espacial).

### 3. Normalidad

Las composiciones principales aparecen utilizando una distribución normal.

La mayoría se concentra alrededor del centro del lienzo.

Esto produce una organización claramente reconocible donde la mayor parte de los eventos ocurre cerca de la media.

**Concepto utilizado:**

* Distribución normal (randomGaussian()).

### 4. Excepción

Aparecen eventos poco frecuentes utilizando un Lévy Flight.

A diferencia de la distribución normal, algunos saltos recorren grandes distancias y generan nuevas composiciones lejos de las zonas habituales.

Estas excepciones transforman progresivamente el equilibrio visual.

**Concepto utilizado:**

* Lévy Flight.

### 5. Influencia

El visitante nunca dibuja sobre la pantalla.

La interacción actúa en dos niveles:

- **Local:** cada módulo calcula su distancia al cursor. Los que están a menos de 140px crecen ligeramente y aumentan su brillo, con una intensidad que decae con la distancia.
- **Global:** la cercanía del cursor al centro del lienzo modula las probabilidades del sistema — aumenta la probabilidad de aparición de nuevas composiciones, acelera su crecimiento y empuja levemente la orientación dominante hacia el ángulo del cursor.

En ningún caso el visitante controla directamente una figura: solo altera las probabilidades y la intensidad con la que el sistema responde. Cuando deja de interactuar, el sistema continúa funcionando con sus valores base.

## Conceptos de simulación utilizados

La propuesta integra cuatro conceptos de la unidad:

- **Caminata aleatoria** — presente en el Lévy Flight: cada nueva composición de la Etapa de Excepción nace a partir de un paso aleatorio calculado desde la posición de la composición anterior, no de una posición completamente nueva.
- **Ruido Perlin** — genera un campo de correlación espacial de baja frecuencia que hace que celdas cercanas compartan orientación (Etapa de Tendencia). De forma secundaria también anima brillo, escala y rotación de cada módulo para dar sensación de vida orgánica, sin controlar nunca su posición.
- **Distribución normal** — determina dónde nacen las composiciones principales (`randomGaussian()`), concentrándolas cerca del centro del lienzo.
- **Lévy Flight** — genera saltos poco frecuentes con distribución de cola pesada: la mayoría de los pasos son cortos, pero ocasionalmente aparece uno muy largo que crea una composición lejos de las zonas habituales.

Todos estos mecanismos conviven dentro de un único sistema.

La influencia del visitante combina un efecto local (proximidad del cursor a cada módulo) con uno global (proximidad del cursor al centro del lienzo, que regula el sistema completo).

## Dificultades

Durante el desarrollo aparecieron varios problemas.

* La primera propuesta basada en galaxias resultaba demasiado narrativa y desviaba la atención de los conceptos probabilísticos.
* Las composiciones aparecían demasiado rápido y generaban saturación visual.
* Fue necesario ajustar las probabilidades para que cada momento se percibiera de forma gradual.
* Encontrar una interacción significativa fue más complejo que simplemente modificar colores o tamaños.

## Uso de IA

La IA fue utilizada como apoyo, con las siguientes modificaciones concretas sobre sus propuestas:

- Propuso un cambio de etapas por bloques de tiempo fijos, lo reemplacé por pesos continuos mezclados con `smoothstep`, para que la transición entre momentos no se sintiera como un corte.
- Sugirió partículas independientes para las composiciones, en su lugar implementé el sistema de dos niveles (celdas + composiciones) para que las formas grandes se construyeran a partir de módulos pequeños, como pedía el enunciado.
- Propuso aplicar ruido Perlin también a la posición de las composiciones, lo descarté y lo limité a orientación, brillo y escala, respetando la restricción del enunciado de no usar Perlin para posición.
- Ajusté manualmente las probabilidades de aparición de composiciones (spawn rate), que en la propuesta inicial generaban saturación visual demasiado rápido.

## Autoevaluación

| Criterio                  |                          Cumplo                         | Evidencia                                                                                                                   |
| ------------------------- | :-----------------------------------------------------: | --------------------------------------------------------------------------------------------------------------------------- |
| Encargo completo          |                            ✅                            | Los cinco momentos están representados dentro del mismo sistema mediante cambios de comportamiento, no de escenas.          |
| Simulación con intención  |                            ✅                            | Se utilizan caminata aleatoria, ruido Perlin, distribución normal y Lévy Flight.                                            |
| Interacción significativa |                            ✅                            | El visitante modifica probabilidades, orientación, crecimiento y brillo, pero el sistema sigue funcionando sin interacción. |
| Prototipo funcional       |                            ✅                            | El sketch corre en tiempo real, formato 9:16 y sin errores que impidan comprender la experiencia.                           |
| Proceso documentado       | ✅                  | Versiones intermedias, decisiones, dificultades, uso de IA y enlace al prototipo.                                           |
