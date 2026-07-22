# Actividad 4: Distribución Normal

## 1. Código ejemplo analizado:

```jsx
// The Nature of Code
// Daniel Shiffman
// Ejemplo de una distribución normal (gaussiana).

// Se ejecuta una sola vez al iniciar el programa.
function setup() {

  // Crea un lienzo de 640 x 240 píxeles.
  createCanvas(640, 240);

  // Pinta el fondo de blanco.
  // Solo se ejecuta una vez, por lo que los círculos
  // permanecen dibujados y se van acumulando.
  background(255);
}

// Se ejecuta continuamente (aprox. 60 veces por segundo).
function draw() {

  // Genera un número aleatorio con distribución normal.
  // La media (centro) es 320 y la desviación estándar es 60.
  // La mayoría de los valores estarán cerca de 320,
  // mientras que pocos aparecerán en los extremos.
  let x = randomGaussian(320, 60);

  // Elimina el borde del círculo.
  noStroke();

  // Color negro con baja opacidad.
  // La transparencia permite ver en qué zonas
  // se acumulan más círculos.
  fill(0, 10);

  // Dibuja un círculo.
  // La posición en X cambia según la distribución normal.
  // La posición en Y permanece fija en 120.
  // El diámetro del círculo es de 16 píxeles.
  circle(x, 120, 16);
}
```

## 2. Distribución normal representada con líneas verticales

```jsx
// Distribución normal representada con líneas verticales

function setup() {
  createCanvas(640, 240);
  background(255);
}

function draw() {

  // Genera un número con distribución normal.
  // El centro de la distribución es la mitad del canvas.
  let x = randomGaussian(width / 2, 60);

  // Color negro con transparencia.
  stroke(0, 20);

  // Dibuja una línea vertical en la posición generada.
  line(x, 0, x, height);
}
```
