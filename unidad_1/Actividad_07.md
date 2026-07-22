# Actividad 07 – Reto de diseño: Navegar la incertidumbre

## Concepto de la experiencia

### Nombre

Nacimiento de una galaxia.

### Intención conceptual

La experiencia representa el nacimiento y evolución de una galaxia mediante un sistema generativo en tiempo real. En lugar de ilustrar literalmente los conceptos de posibilidad, tendencia o excepción, estos se traducen en comportamientos del universo.

La idea central es mostrar que, aunque el comportamiento de las partículas parece caótico, existen reglas probabilísticas que permiten la aparición de estructuras complejas. El visitante no controla el sistema, sino que modifica las probabilidades que gobiernan su evolución, demostrando que pequeñas influencias pueden transformar el resultado sin determinarlo completamente.

## Dirección artística

La propuesta toma como referencia fotografías astronómicas del telescopio Hubble y del James Webb, buscando una estética cercana al espacio profundo.

### Paleta visual

* Fondo negro con ligeros degradados azul oscuro y violeta.
* Polvo cósmico formado por pequeñas partículas.
* Estrellas con halo luminoso (glow suave).
* Diferentes tamaños para generar sensación de profundidad.
* Colores inspirados en estrellas reales:

  * Blanco
  * Azul
  * Celeste
  * Amarillo
  * Naranja
  * Rosa
  * Violeta

La galaxia nunca permanece estática; siempre continúa evolucionando.

## Traducción de los conceptos del reto

### Posibilidad

La experiencia comienza con una nube de polvo cósmico formada por miles de partículas.

Cada partícula realiza una caminata aleatoria, por lo que inicialmente todas las direcciones parecen igualmente posibles y aún no existe ninguna estructura reconocible.

**Concepto utilizado**

* Caminata aleatoria.

### Tendencia

A medida que el sistema evoluciona, pequeñas preferencias de movimiento hacen que algunas regiones comiencen a concentrar mayor cantidad de partículas.

Estas pequeñas diferencias acumuladas generan lentamente los primeros brazos de la galaxia.

**Concepto utilizado**

* Distribuciones no uniformes.

### Normalidad

Cuando nacen nuevas estrellas, la mayoría aparece cerca del núcleo galáctico.

Esto genera una concentración natural de materia en el centro y una disminución progresiva hacia los extremos.

**Concepto utilizado**

* Distribución normal (Gaussiana).

### Excepción

De manera ocasional ocurre un evento poco probable.

Una estrella realiza un gran desplazamiento atravesando gran parte del espacio.

Ese salto permite iniciar la formación de nuevos cúmulos en regiones antes vacías.

**Concepto utilizado**

* Lévy Flight.

### Influencia

La presencia del visitante modifica las probabilidades del sistema sin controlar directamente las partículas.

Su interacción representa una perturbación gravitacional que cambia la forma en que el universo evoluciona.

El sistema continúa funcionando incluso cuando no existe interacción.

**Conceptos utilizados**

* Modificación dinámica de probabilidades.
* Ruido Perlin.
* Distribuciones de probabilidad.

## Evolución del sistema

La experiencia no comienza con una galaxia formada.

El proceso completo representa su nacimiento.

### Etapa 1 — Polvo cósmico

El universo está compuesto únicamente por pequeñas partículas con un brillo muy tenue.

Estas representan gas y polvo interestelar.

### Etapa 2 — Agrupación

Las partículas comienzan a concentrarse lentamente debido a las reglas probabilísticas del sistema.

Empiezan a aparecer regiones con mayor densidad.

### Etapa 3 — Nacimiento de estrellas

Cuando una región alcanza suficiente concentración, algunas partículas comienzan a transformarse.

La transición ocurre gradualmente:

```
Polvo cósmico
        ↓
Partícula brillante
        ↓
Estrella joven
        ↓
Estrella con halo luminoso
```

Las estrellas no aparecen instantáneamente; evolucionan visualmente conforme aumenta su energía.

### Etapa 4 — Formación de la galaxia

Con el paso del tiempo aparecen:

* Núcleo brillante.
* Brazos espirales.
* Regiones de mayor concentración.
* Nuevos cúmulos generados por eventos excepcionales.

La galaxia nunca deja de transformarse.

### Uso del ruido Perlin

El ruido Perlin se utilizará para representar procesos continuos del universo.

No controlará la posición principal de las partículas, sino aspectos orgánicos como:

* Movimiento suave del gas.
* Variación del brillo de las estrellas.
* Oscilaciones lentas de las nebulosas.
* Sensación de respiración del sistema.

Esto permitirá evitar movimientos bruscos y generar una sensación más natural.

## Interacción

El cursor representará una masa gravitacional temporal.

Su presencia no moverá directamente las estrellas.

En cambio modificará probabilidades relacionadas con:

* Atracción entre partículas.
* Formación de nuevas estrellas.
* Intensidad del movimiento.
* Frecuencia de eventos extraordinarios.

El usuario influye en el sistema, pero nunca determina exactamente lo que ocurrirá.

# Resultado esperado

Se espera obtener una experiencia donde cada ejecución produzca una galaxia diferente, pero manteniendo siempre la misma identidad visual y conceptual.

El visitante observará cómo estructuras complejas emergen gradualmente a partir de reglas simples y probabilísticas, comprendiendo que el azar puede generar orden cuando existen patrones que gobiernan el sistema.
