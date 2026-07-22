# Actividad 06: Ruido Perlin

## Código:

```javascript
// Visualización del ruido Perlin

let t = 0;

function setup() {
  createCanvas(640, 400);
}

function draw() {
  background(255);

  // Obtiene un valor de ruido entre 0 y 1
  let n = noise(t);

  // Convierte ese valor en un tamaño entre 20 y 200
  let tamaño = map(n, 0, 1, 20, 200);

  fill(100, 150, 255);
  noStroke();

  // Dibuja un círculo cuyo tamaño cambia suavemente
  circle(width / 2, height / 2, tamaño);

  // Avanza lentamente en el ruido
  t += 0.01;
}
```

## ¿Por qué lo visualicé de esa manera?

Elegí representar el ruido Perlin mediante el cambio de tamaño de un círculo porque permite observar fácilmente cómo los valores cambian de forma continua y sin saltos bruscos. El crecimiento y la disminución del círculo hacen evidente la suavidad característica del ruido Perlin.

## ¿Qué resultados esperaba obtener?

Esperaba que el círculo aumentara y disminuyera su tamaño de forma fluida, generando una animación suave y natural, a diferencia de una variación aleatoria que cambiaría de tamaño de manera repentina e impredecible.
