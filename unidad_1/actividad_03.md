# Actividad 3: Distribuciones de probabilidad

## **1. Diferencia entre una distribución uniforme y una no uniforme**

- **Distribución uniforme:** Todos los resultados tienen la misma probabilidad de ocurrir. En la caminata aleatoria, el caminante tiene la misma posibilidad de moverse hacia la derecha, izquierda, arriba o abajo (25% cada una).
- **Distribución no uniforme:** Algunos resultados tienen más probabilidad de ocurrir que otros. En la caminata aleatoria, una dirección (por ejemplo, la derecha) puede tener mayor probabilidad, haciendo que el caminante tienda a desplazarse más hacia ese lado.

## 2. Código modificado favoreciendo el movimiento hacia la derecha

```jsx
let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
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
    // Genera un número entero entre 0 y 9
    const choice = floor(random(10));

    if (choice < 5) {
      // 50% de probabilidad (0,1,2,3,4)
      this.x++;
    } else if (choice < 7) {
      // 20% de probabilidad (5,6)
      this.x--;
    } else if (choice < 9) {
      // 20% de probabilidad (7,8)
      this.y++;
    } else {
      // 10% de probabilidad (9)
      this.y--;
    }
  }
}
```

## 3. ¿Qué cambió?

Se modificó el método `step()`:

- Antes: `floor(random(4))` → cuatro opciones con la misma probabilidad (**25%** cada una).
- Ahora: `floor(random(10))` → diez posibles números, donde:
    - **0–4 (50%)** → derecha.
    - **5–6 (20%)** → izquierda.
    - **7–8 (20%)** → abajo.
    - **9 (10%)** → arriba.
