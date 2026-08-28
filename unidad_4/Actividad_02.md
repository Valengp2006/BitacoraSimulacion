# Concepto de diseño

## 1. Declaración Conceptual (El Porqué)

La obra es una instalación audiovisual generativa e interactiva que utiliza la metáfora de un ecosistema marino abisal para explorar los límites entre el caos individual y el orden colectivo. Inspirada en los principios de sincronización espontánea y gobernada matemáticamente por la Ecuación de Kuramoto, la experiencia sitúa al espectador frente a un cardumen de 8 medusas bioluminiscentes.

En la naturaleza, la sincronización es una herramienta de supervivencia; en esta pieza, se convierte en un lenguaje poético. La obra plantea una pregunta al participante: ¿Somos observadores pasivos de las corrientes o agentes capaces de alterar la armonía del ecosistema?

## 2. Estética Visual y Personalidades Orgánicas

Se abandona la rigidez de los gráficos de laboratorio para adoptar un diseño biomórfico y minimalista. El lienzo simula agua profunda mediante un efecto de arrastre acumulativo (motion blur), dejando estelas de luz que representan la memoria del movimiento.

Para cumplir con el requisito de diversidad, los 8 agentes se dividen en 4 Personalidades Audiovisuales (2 agentes por categoría), cuyas morfologías se asocian directamente a su comportamiento dinámico:

1. **Aurelia Neón (Cian):** Medusas esbeltas de nado ágil, con un paraguas translúcido y 6 tentáculos largos que ondulan rápidamente. Representan las frecuencias más altas y nerviosas del sistema.
2. **Batisfera Coral (Magenta):** Criaturas densas, de gran escala y 4 tentáculos gruesos. Su pulso es pesado, lento y profundo; actúan como los "anclajes" rítmicos del cardumen.
3. **Cianea Eléctrica (Amarillo Áureo):** Organismos pequeños y compactos con 8 tentáculos filamentosos. Su bioluminiscencia es nítida e incisiva, ideal para notar pequeños desfases.
4. **Velella Violeta (Verde Esmeralda/Violeta):** Entidades de tamaño medio con 5 tentáculos en espiral, caracterizadas por un patrón de nado flotante e impredecible.

## 3. Paisaje Sonoro Subacuático (Comportamiento Vinculado)

El audio no es decorativo; está anclado matemáticamente a la fase ($\theta_i$) de cada agente. Cada vez que una medusa completa un ciclo físico de contracción (cuando su fase cruza el origen 0), dispara un pulso sonoro.

- **Evitación de la Disonancia:** Para que la experiencia sea inmersiva incluso en el Caos, se utiliza una Escala Pentatónica Menor de La. En estado de desorden, suena como una textura ambiental texturizada (música ambient abstracta). Al sincronizarse, muta orgánicamente en un pulso rítmico minimalista y unísono.
- **Filtros Hidrodinámicos:** El audio pasa por un filtro de paso bajo (LowPass) que recorta los brillos excesivos, emulando la acústica amortiguada del fondo del océano.

## 4. Matriz de Interacción Performativa y Perturbación

| Dimensión | Tipo de Interacción | Mecanismo Técnico | Impacto en la Experiencia (Narrativa) |
|---|---|---|---|
| Global | Performática Invisible | Posición del cursor en el eje Y (Altura) y eje X (Marea). | Modifica en tiempo real la variable K (Acoplamiento): Llevar el cursor arriba intensifica las corrientes marinas, obligando a las medusas a sincronizarse. Llevarlo abajo las aísla en su propio ritmo. El eje X altera el tempo (dt). |
| Individual | Performática Focalizada | Clic directo o tap sobre la campana de una medusa específica. | Inyección de Perturbación: Rompe la fase del agente llevándola a un random y altera su posición en el espacio. El agente sufre un "choque eléctrico" temporal, acelerando su ritmo e iluminándose en blanco puro. |
| Colectiva | Respuesta del Sistema | Algoritmo de Kuramoto recalculando el parámetro de orden R. | El espectador observa cómo el colectivo reacciona a la perturbación individual: las demás medusas absorben el impacto, se desestabilizan levemente y, mediante sutiles ajustes, arrastran al "agente rebelde" de vuelta a la marea común. |

## 5. Indicadores de Estado Colectivo (Comunicación Perceptible)

El espectador puede identificar la salud y cohesión del ecosistema a través de tres niveles calculados mediante el parámetro de orden R (donde 0 es caos absoluto y 1 es sincronía perfecta):

1. **Corrientes Dispersas (Desorden - R < 0.35):** Las luces parpadean de forma caótica en distintas zonas del lienzo. El sonido es una textura aleatoria desarticulada. Evoca soledad y aislamiento.
2. **Marea Fluida (Organización Parcial - 0.35 ≤ R < 0.82):** Se empiezan a formar pequeños subgrupos de medusas que contraen sus cuerpos al mismo tiempo. El sonido empieza a ganar un sentido del compás reconocible.
3. **Resonancia Abisal (Organización Estable - R ≥ 0.82):** Todo el cardumen pulsa, brilla y canta exactamente al mismo compás. Para hacer este estado plenamente perceptible, todo el fondo del lienzo respira con un sutil resplandor cian reactivo, y el volumen armónico alcanza su punto máximo, envolviendo al usuario en una atmósfera hipnótica.

### Moodboard:

<img width="392" height="782" alt="WhatsApp Image 2026-08-26 at 09 16 56" src="https://github.com/user-attachments/assets/9dc38c38-0caa-46ee-9b82-f7cd021b7048" />
<img width="394" height="824" alt="WhatsApp Image 2026-08-26 at 09 16 43" src="https://github.com/user-attachments/assets/a547e8b4-ae08-4d0e-851a-fabd24a412e4" />
<img width="390" height="556" alt="WhatsApp Image 2026-08-26 at 09 16 19" src="https://github.com/user-attachments/assets/292f2b70-1e46-4af0-bbb5-e6b6a7ef69f8" />
<img width="378" height="676" alt="WhatsApp Image 2026-08-26 at 09 16 08" src="https://github.com/user-attachments/assets/384d586d-f8a6-4835-9e4d-aa7bcb907ce4" />
<img width="384" height="702" alt="WhatsApp Image 2026-08-26 at 09 15 55" src="https://github.com/user-attachments/assets/36848936-2adf-4a61-ba2f-e331ce1cf99a" />
<img width="388" height="556" alt="WhatsApp Image 2026-08-26 at 09 15 44" src="https://github.com/user-attachments/assets/3196e1ae-9ed7-449d-bca5-ba836f936d7c" />

