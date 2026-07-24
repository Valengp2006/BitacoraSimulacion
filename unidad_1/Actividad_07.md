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

* patrones geométricos modulares
* arte generativo
* composiciones constructivistas
* diseños editoriales abstractos

La intención fue trabajar únicamente con relaciones entre formas, orientación, densidad y agrupación.

## Evolución del proyecto

### Versión 1

La primera versión consistía únicamente en una retícula.

Cada celda elegía aleatoriamente una figura entre cuatro posibilidades.

Todas las decisiones eran completamente independientes.

Resultado:

* demasiado uniforme
* sin lectura visual
* no existía sensación de organización

Lo que aprendí:

La aleatoriedad uniforme produce ruido visual, pero no genera estructuras reconocibles.

#### Imagen primer versión:

<img width="301" height="536" alt="Captura de pantalla 2026-07-23 a la(s) 10 40 22 a m" src="https://github.com/user-attachments/assets/7bb5481f-73df-4a65-93d2-903b0f7a5040" />

### Versión 2

La segunda versión comenzó a utilizar ruido Perlin.

En lugar de elegir completamente al azar, las figuras empezaron a compartir cierta orientación con las vecinas.

Esto generó regiones donde aparecían pequeñas tendencias.

Resultado:

* aparecieron zonas similares
* las transiciones fueron más suaves
* comenzó a sentirse un patrón

Problema encontrado:

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



### Versión final

La versión final integra todos los conceptos en un mismo sistema.

Las composiciones aparecen siguiendo distintas distribuciones probabilísticas mientras las figuras continúan reorganizándose continuamente.

El visitante nunca dibuja directamente.

Su presencia únicamente modifica las probabilidades del sistema.

#### Video versión final:



## Interpretación de los cinco momentos

### 1. Posibilidad

Al comenzar todas las figuras tienen la misma probabilidad de aparecer.

No existen regiones dominantes.

Cada módulo toma decisiones independientes.

Visualmente se percibe un campo caótico.

### 2. Tendencia

El ruido Perlin comienza a generar pequeñas correlaciones entre celdas cercanas.

Sin imponer un patrón fijo, algunas orientaciones empiezan a repetirse.

Las pequeñas preferencias terminan construyendo regiones similares.

Concepto utilizado:

* Ruido Perlin.

### 3. Normalidad

Las composiciones principales aparecen utilizando una distribución normal.

La mayoría se concentra alrededor del centro del lienzo.

Esto produce una organización claramente reconocible donde la mayor parte de los eventos ocurre cerca de la media.

Concepto utilizado:

* Distribución normal (randomGaussian()).

### 4. Excepción

Aparecen eventos poco frecuentes utilizando un Lévy Flight.

A diferencia de la distribución normal, algunos saltos recorren grandes distancias y generan nuevas composiciones lejos de las zonas habituales.

Estas excepciones transforman progresivamente el equilibrio visual.

Concepto utilizado:

* Lévy Flight.

### 5. Influencia

El visitante nunca dibuja sobre la pantalla.

Su posición modifica las probabilidades del sistema.

Cuando el cursor se aproxima:

* Aumenta el tamaño de las figuras cercanas
* Incrementa su brillo
* Acelera la aparición de nuevas composiciones
* Modifica ligeramente la orientación dominante

Cuando el visitante deja de interactuar, el sistema continúa funcionando por sí mismo.

## Conceptos de simulación utilizados

La propuesta integra cuatro conceptos de la unidad:

* Caminata aleatoria (decisiones iniciales de los módulos).
* Ruido Perlin (tendencias suaves entre regiones).
* Distribución normal (aparición de composiciones alrededor del centro).
* Lévy Flight (eventos excepcionales con grandes desplazamientos).

Todos estos mecanismos conviven dentro de un único sistema.

## Interacción

La interacción no consiste en dibujar.

El cursor únicamente altera las reglas del sistema.

Dependiendo de la cercanía del visitante:

* Aumenta la probabilidad de aparición de nuevas composiciones
* Modifica la orientación dominante
* Incrementa el tamaño de los módulos cercanos
* Aumenta su brillo

Esto hace que el sistema reaccione sin perder su autonomía.

## Dificultades

Durante el desarrollo aparecieron varios problemas.

* La primera propuesta basada en galaxias resultaba demasiado narrativa y desviaba la atención de los conceptos probabilísticos.
* Las composiciones aparecían demasiado rápido y generaban saturación visual.
* Fue necesario ajustar las probabilidades para que cada momento se percibiera de forma gradual.
* Encontrar una interacción significativa fue más complejo que simplemente modificar colores o tamaños.

# Uso de IA

La IA fue utilizada como apoyo para:

* Generar ideas iniciales
* Explorar alternativas visuales
* Resolver errores de programación
* Proponer estructuras de código
* Explicar conceptos matemáticos relacionados con las distribuciones

## Autoevaluación

| Criterio                  |                          Cumplo                         | Evidencia                                                                                                                   |
| ------------------------- | :-----------------------------------------------------: | --------------------------------------------------------------------------------------------------------------------------- |
| Encargo completo          |                            ✅                            | Los cinco momentos están representados dentro del mismo sistema mediante cambios de comportamiento, no de escenas.          |
| Simulación con intención  |                            ✅                            | Se utilizan caminata aleatoria, ruido Perlin, distribución normal y Lévy Flight.                                            |
| Interacción significativa |                            ✅                            | El visitante modifica probabilidades, orientación, crecimiento y brillo, pero el sistema sigue funcionando sin interacción. |
| Prototipo funcional       |                            ✅                            | El sketch corre en tiempo real, formato 9:16 y sin errores que impidan comprender la experiencia.                           |
| Proceso documentado       | ✅                  | Versiones intermedias, decisiones, dificultades, uso de IA y enlace al prototipo.                                           |
