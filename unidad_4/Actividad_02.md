# Concepto de diseño

[URL proyecto](https://editor.p5js.org/Valengp2006/sketches/dYepW5VNu)

## 1. Declaración Conceptual (El Porqué)

La obra es una instalación audiovisual generativa e interactiva que utiliza la metáfora de un ecosistema marino abisal para explorar los límites entre el caos individual y el orden colectivo. Inspirada en los principios de sincronización espontánea y gobernada matemáticamente por la Ecuación de Kuramoto, la experiencia sitúa al espectador frente a un cardumen de 8 medusas bioluminiscentes artificiales.

En la naturaleza, la sincronización es una herramienta de supervivencia; en esta pieza, se convierte en un lenguaje poético. La obra plantea una pregunta al participante: ¿Somos observadores pasivos de las corrientes o agentes capaces de alterar la armonía del ecosistema?

## 2. Estética Visual y Personalidades Orgánicas

Se abandona la rigidez de los gráficos de laboratorio para adoptar un diseño biomórfico y minimalista. El lienzo simula agua profunda mediante un efecto de arrastre acumulativo (*motion blur*), dejando estelas de luz que representan la memoria del movimiento.

Para cumplir con el requisito de diversidad, los 8 agentes se dividen en 4 Personalidades Audiovisuales (2 agentes por categoría), cuyas morfologías y dinámicas internas se asocian directamente a su comportamiento:

1. **Aurelia Neón (Cian):** Medusas con frecuencias altas y nerviosas ($\omega = 0.07$), configuradas para liderar los pulsos rápidos del sistema.
2. **Batisfera Coral (Magenta):** Criaturas densas de gran escala y frecuencia lenta ($\omega = 0.02$), que actúan como los anclajes rítmicos del cardumen.
3. **Cianea Eléctrica (Amarillo Áureo):** Organismos de velocidad intermedia ($\omega = 0.05$) con una bioluminiscencia nítida.
4. **Velella Violeta (Verde Esmeralda/Violeta):** Entidades de comportamiento flotante equilibrado ($\omega = 0.03$).

## 3. Paisaje Sonoro Subacuático (Comportamiento Vinculado)

El audio no es decorativo; está anclado matemáticamente a la fase de cada agente mediante la síntesis polifónica de Tone.js. Cada vez que una medusa completa un ciclo físico de contracción (detectado por su cruce de fase), dispara un pulso tonal limpio.

* **Escala Pentatónica Menor de La:** Las frecuencias se distribuyen armónicamente para que, incluso en estados de desorden total, el resultado funcione como una textura ambiental texturizada que muta orgánicamente hacia un pulso minimalista y unísono durante la sincronización.
* **Estabilidad Polifónica:** Se integra un umbral de seguridad (*debounce*) y control de polifonía para asegurar que la interacción en vivo mantenga la claridad acústica sin saturar las voces del sistema.

## 4. Matriz de Interacción Performativa y Perturbación

| Dimensión | Tipo de Interacción | Mecanismo Técnico | Impacto en la Experiencia (Narrativa) |
| --- | --- | --- | --- |
| Global (Tempo y Acoplamiento) | Movimiento del cursor en ejes X (Tempo/dt) e Y (Acoplamiento/K) con interpolación de inercia (`lerp`). | Modifica gradualmente la variable de acoplamiento $K$ y la escala temporal $dt$. Los cambios no son abruptos, permitiendo observar la transición orgánica del sistema. |  |
| Individual (Perturbación Lumínica) | Proximidad del cursor respecto a las coordenadas espaciales de cada agente. | El cursor actúa como una linterna de profundidad: al acercarse a una medusa, su bioluminiscencia (halo y núcleo) se intensifica de forma reactiva sin alterar violentamente su fase matemática. |  |
| Colectiva (Navegación Orgánica) | Desacoplamiento entre la fase interna de Kuramoto (impulso/velocidad) y vectores de ruido autónomo (Perlin Noise). | Permite que las medusas mantengan trayectorias de nado libres y naturales en el espacio toroidal, evitando que todas se muevan de forma idéntica al sincronizarse. |  |

## 5. Indicadores de Estado Colectivo (Comunicación Perceptible)

El espectador puede identificar la salud y cohesión del ecosistema mediante la retroalimentación visual en tiempo real y la interfaz de control en pantalla (HUD), reconociendo las transiciones entre:

1. **Corrientes Dispersas ($K \approx 0$):** Movimiento independiente y caótico de las medusas en el espacio, acompañado por una textura sonora dispersa.
2. **Marea Fluida (Organización Parcial):** Aparición progresiva de subgrupos que contraen sus cuerpos de forma coordinada gracias a la inercia del acoplamiento.
3. **Resonancia Abisal ($K \ge 2.0$):** El cardumen alinea sus pulsos y velocidades, generando un clímax sonoro armónico y un comportamiento unificado en la corriente.

### Moodboard:

<img width="392" height="782" alt="WhatsApp Image 2026-08-26 at 09 16 56" src="https://github.com/user-attachments/assets/9dc38c38-0caa-46ee-9b82-f7cd021b7048" />
<img width="394" height="824" alt="WhatsApp Image 2026-08-26 at 09 16 43" src="https://github.com/user-attachments/assets/a547e8b4-ae08-4d0e-851a-fabd24a412e4" />
<img width="390" height="556" alt="WhatsApp Image 2026-08-26 at 09 16 19" src="https://github.com/user-attachments/assets/292f2b70-1e46-4af0-bbb5-e6b6a7ef69f8" />
<img width="378" height="676" alt="WhatsApp Image 2026-08-26 at 09 16 08" src="https://github.com/user-attachments/assets/384d586d-f8a6-4835-9e4d-aa7bcb907ce4" />
<img width="384" height="702" alt="WhatsApp Image 2026-08-26 at 09 15 55" src="https://github.com/user-attachments/assets/36848936-2adf-4a61-ba2f-e331ce1cf99a" />
<img width="388" height="556" alt="WhatsApp Image 2026-08-26 at 09 15 44" src="https://github.com/user-attachments/assets/3196e1ae-9ed7-449d-bca5-ba836f936d7c" />


