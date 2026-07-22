# Actividad 2: Caminatas Aleatorias

## 1. Código analizado:

```jsx
// The Nature of Code
// Daniel Shiffman
// Ejemplo de un "Random Walker" (caminante aleatorio).

// Variable que almacenará nuestro objeto Walker.
let walker;

// Se ejecuta una sola vez al iniciar el programa.
function setup() {

  // Crea un lienzo de 640x240 píxeles.
  createCanvas(640, 240);

  // Crea una nueva instancia (objeto) de la clase Walker.
  walker = new Walker();

  // Pinta el fondo de color blanco.
  // Solo ocurre una vez, por eso los puntos anteriores no se borran.
  background(255);
}

// Se ejecuta continuamente (aprox. 60 veces por segundo).
function draw() {

  // Hace que el caminante se mueva un paso.
  walker.step();

  // Dibuja la nueva posición del caminante.
  walker.show();
}

// Definición de la clase Walker.
class Walker {

  // El constructor se ejecuta cuando se crea el objeto.
  constructor() {

    // Posición inicial: centro horizontal del lienzo.
    this.x = width / 2;

    // Posición inicial: centro vertical del lienzo.
    this.y = height / 2;
  }

  // Método encargado de dibujar el caminante.
  show() {

    // Color negro para el punto.
    stroke(0);

    // Dibuja un punto en la posición actual.
    point(this.x, this.y);
  }

  // Método que decide hacia dónde moverse.
  step() {

    // random(4) genera un número entre 0 y 4 (sin incluir 4).
    // floor() elimina los decimales.
    // Resultado posible: 0, 1, 2 o 3.
    const choice = floor(random(4));

    // Dependiendo del número obtenido,
    // el caminante avanza una unidad en una dirección.

    if (choice == 0) {

      // Mover un píxel hacia la derecha.
      this.x++;

    } else if (choice == 1) {

      // Mover un píxel hacia la izquierda.
      this.x--;

    } else if (choice == 2) {

      // Mover un píxel hacia abajo.
      this.y++;

    } else {

      // Mover un píxel hacia arriba.
      this.y--;
    }
  }
}
```

## 2. ¿Qué está pasando en cada frame?

Cada vez que `draw()` se ejecuta ocurre este ciclo:

1. El caminante está en una posición `(x, y)`.
2. Se genera un número aleatorio entre **0 y 3**.
3. Según ese número, se mueve **1 píxel**:
    - `0` → derecha
    - `1` → izquierda
    - `2` → abajo
    - `3` → arriba
4. Se dibuja un punto en la nueva posición.
5. Como **el fondo nunca vuelve a pintarse**, todos los puntos permanecen visibles y se forma un camino aleatorio.

## 3. Conceptos importantes que aparecen en el código

- **`setup()`** → Se ejecuta una sola vez al iniciar el programa.
- **`draw()`** → Se ejecuta repetidamente para crear la animación.
- **Clase (`class`)** → Define cómo será un objeto (en este caso, un caminante).
- **Constructor (`constructor`)** → Inicializa las propiedades del objeto cuando se crea.
- **`this.x` y `this.y`** → Guardan la posición actual del caminante.
- **`random(4)`** → Genera un número aleatorio entre 0 y 4.
- **`floor()`** → Convierte ese número en un entero (0, 1, 2 o 3).
- **`point(x, y)`** → Dibuja un punto en las coordenadas indicadas.
- **`background(255)`** solo se ejecuta una vez, por eso el recorrido queda "dibujado". Si lo pusieras dentro de `draw()`, solo verías un único punto moviéndose porque el fondo se limpiaría en cada fotograma.
