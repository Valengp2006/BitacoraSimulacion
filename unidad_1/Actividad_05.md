# Actividad 05: Distribución personalizada: Lévy flight

La idea del **Lévy flight** es que la mayoría de los movimientos son cortos, pero **de vez en cuando ocurre un salto muy largo**. Esto hace que el recorrido explore zonas lejanas del espacio.

## Código

```javascript
// The Nature of Code
// Random Walker con Lévy Flight

let walker;

function setup() {
  createCanvas(640, 240);
  background(255);
  walker = new Walker();
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {

  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    stroke(0);
    point(this.x, this.y);
  }

  step() {

    // La mayoría de los pasos serán de 1 píxel.
    let paso = 1;

    // Con un 2% de probabilidad, el paso será mucho más largo.
    if (random(1) < 0.02) {
      paso = random(20, 80);
    }

    // Elegimos una dirección al azar.
    const choice = floor(random(4));

    if (choice == 0) {
      this.x += paso;
    } else if (choice == 1) {
      this.x -= paso;
    } else if (choice == 2) {
      this.y += paso;
    } else {
      this.y -= paso;
    }

    // Evita que el caminante salga del canvas.
    this.x = constrain(this.x, 0, width);
    this.y = constrain(this.y, 0, height);
  }
}
```

## Explicación

### ¿Por qué usé esta técnica?

Utilicé el **Lévy flight** porque permite que el caminante realice **muchos movimientos cortos y, ocasionalmente, un movimiento muy largo**. Esto hace que el recorrido sea más variado que una caminata aleatoria tradicional.

### ¿Qué resultados esperaba obtener?

Esperaba observar un recorrido donde el caminante permaneciera explorando una misma zona durante varios pasos y, de forma ocasional, diera un gran salto hacia otra parte del lienzo. Esto genera una exploración más amplia del espacio y un patrón de movimiento más parecido al que se observa en algunos animales cuando buscan alimento o en ciertos procesos naturales.
