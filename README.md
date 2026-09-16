# Bitácora de Simulación y Computación Visual
**Universidad Pontificia Bolivariana — Escuela de Ingenierías y Diseño**  
**Facultad de Diseño y Creación Digital**  
**Estudiante:** Valentina Garzón Pérez  
**Semestre:** 2026-1 | **Docente:** Juan Camilo Gómez  

---

## Índice General de Navegación

Esta bitácora compila el proceso experimental, analítico y proyectual desarrollado durante el curso de **Simulación**. Cada unidad aborda modelos matemáticos, leyes físicas, algoritmos probabilísticos y sistemas generativos aplicados a la creación visual interactiva en tiempo real.

| Unidad | Eje Temático | Actividades y Proyectos | Enlace Documental |
| :--- | :--- | :--- | :--- |
| **Unidad 1** | **Azar, Probabilidad y Caminatas Aleatorias** | • Actividad 02: *Caminatas Aleatorias (Random Walkers)*<br>• Actividad 03: *Distribuciones de Probabilidad y Sesgos*<br>• Actividad 04: *Distribución Normal (Gaussiana)*<br>• Actividad 05: *Distribución Personalizada: Lévy Flight*<br>• Actividad 06: *Ruido Perlin y Coherencia Temporal*<br>• Actividad 07: *Proyecto — Navegar la Incertidumbre* | [Ver Unidad 1](unidad_1/Actividad_07.md) |
| **Unidad 2** | **Vida Artificial y Sistemas Complejos** | • Actividad 05: *Cicatrices — Memoria emergente en Particle Life (Contradicción en Movimiento)* | [Ver Unidad 2](unidad_2/Actividad_05.md) |
| **Unidad 3** | **Fuerzas, Gravitación y Dinámicas Singulares** | • Actividad 04: *Proyecto Singularidad — Instrumento orbital con modos Lab y Performance* | [Ver Unidad 3](unidad_3/Actividad_04.md) |
| **Unidad 4** | **Osciladores y Sincronización Colectiva** | • Actividad 02: *Instalación Ecosistema Abisal — Modelo de Kuramoto y Medusas Bioluminiscentes* | [Ver Unidad 4](unidad_4/Actividad_02.md) |
| **Unidad 5** | **Sistemas Autónomos y Narrativas Generativas** | • Actividad 01: *Concepto de diseño y gramática de transición continua sin reset*<br>• **Proyecto Activo:** *Relevo Generacional: la ventaja que nadie está aprovechando* | [Ver Unidad 5](unidad_5/Actividad_01.md) |

---

## Proyecto Activo: Relevo Generacional
### *"La ventaja que nadie está aprovechando"*

> **Centro de Eventos Fórum UPB × Future Leaders Forum Fortaleza 2026**  
> Charla inspiracional / Keynote interactiva a cargo de Alma López (Directora Fórum UPB).  
> **Lugar y Fecha:** Centro de Eventos do Ceará — Fortaleza, Brasil (30 de junio – 1 de julio de 2026).

* **Repositorio de Código Fuente:** [github.com/Valengp2006/relevo-generacional-upb](https://github.com/Valengp2006/relevo-generacional-upb)
* **Demostración Interactiva en Vivo (GitHub Pages):** [valengp2006.github.io/relevo-generacional-upb](https://valengp2006.github.io/relevo-generacional-upb/)

---

### 1. Marco Conceptual y Reto de Diseño

El encargo propone diseñar un instrumento visual generativo en tiempo real (desarrollado en JavaScript con **p5.js**, resolución adaptativa y ejecución a pantalla completa) para acompañar la conferencia magistral de 13 diapositivas sobre el relevo generacional en el sector de la industria de eventos y reuniones (MICE).

A diferencia de un pase de diapositivas estático (PPT/Keynote) o de un sistema de partículas como mero fondo decorativo, en esta obra **las partículas encarnan el discurso**:
1. **Identidad persistente:** Las partículas forman directamente las palabras clave de cada diapositiva y, ante la intervención del orador o el paso discursivo, se reconfiguran cinemáticamente para modelar **esculturas geométricas conceptuales**.
2. **Relevo, no reemplazo:** La simulación matemática nunca se reinicia (`no reset`). Las partículas no se destruyen para dar paso a otras nuevas, sino que fluyen e interpolan sus vectores hacia nuevas coordenadas, formalizando físicamente la tesis de que el relevo generacional es transmisión, herencia viva y co-creación, jamás sustitución.
3. **Respiración y convivencia documental:** El sistema se integra con una capa documental de archivo fotográfico (90 años de la UPB y el Fórum). Cuando una diapositiva exhibe evidencia documental, el enjambre se retrae lateralmente, reduce su opacidad y enmarca la memoria sin obstruirla.

```
       [ ESTADO TEXTO ]                        [ ESTADO ESCULTURA ]
 (Rasterizado tipográfico offscreen)       (Modelado geométrico analítico)
             ▲                                            ▲
             │                                            │
             └─────────── Toggle Manual [Tecla T] ────────┘
                                    │
                                    ▼
                     [ Pool Continuo de 1,800 Nodos ]
                                    │
                     Física Cinemática Seek & Arrive
                     Micro-movimiento Browniano (Perlin)
                     Retracción adaptativa ante fotografía
```

---

### 2. Fundamentos Matemáticos y Modelo Físico

El motor generativo corre a $60\text{ FPS}$ estables bajo un presupuesto fijo de **$N = 1{,}800$ agentes cinemáticos autónomos**.

#### A. Comportamiento de Llegada Suave (*Seek & Arrive*)
Cada partícula $i \in \{1, \dots, N\}$ busca activamente su posición destino $\vec{x}_{\text{target}}$ gobernada por la formulación de dirección autónoma de Craig Reynolds:

$$\vec{r} = \vec{x}_{\text{target}} - \vec{x}_i, \quad d = \|\vec{r}\|$$

El cálculo del vector de velocidad deseada $\vec{v}_{\text{deseada}}$ implementa una desaceleración proporcional dentro de un radio de frenado $R_{\text{arrive}} = 70\text{ px}$:

$$\vec{v}_{\text{deseada}} = \begin{cases} 
v_{\text{max}} \cdot \dfrac{\vec{r}}{d}, & \text{si } d \ge R_{\text{arrive}} \\[8pt]
\left(v_{\text{min}} + \dfrac{d}{R_{\text{arrive}}}(v_{\text{max}} - v_{\text{min}})\right) \cdot \dfrac{\vec{r}}{d}, & \text{si } d < R_{\text{arrive}}
\end{cases}$$

Donde $v_{\text{max}} = 14.0\text{ px/frame}$ y $v_{\text{min}} = 0.4\text{ px/frame}$. La fuerza de timonera resultante $\vec{F}_{\text{steer}}$ se limita por una aceleración máxima $F_{\text{max}} = 0.65$:

$$\vec{F}_{\text{steer}} = \operatorname{clamp}\left(\vec{v}_{\text{deseada}} - \vec{v}_i, \; F_{\text{max}}\right)$$

#### B. Micro-movimiento Orgánico Browniano (Ruido Perlin)
Para evitar que los nodos adquieran una rigidez cristalina estática una vez alcanzado el objetivo, se inyecta continuamente un vector de perturbación biológica dependiente del tiempo y de un desplazamiento de fase individual $\Delta_i = i \cdot 0.17$:

$$\theta_i(t) = 2\pi \cdot \operatorname{noise}\left(x_i \cdot s + \Delta_i, \; t \cdot \omega\right)$$
$$\vec{F}_{\text{idle}} = F_0 \cdot \begin{pmatrix} \cos \theta_i(t) \\ \sin \theta_i(t) \end{pmatrix}$$

Con escala espacial $s = 0.006$, frecuencia temporal $\omega = 0.008$ y fuerza máxima $F_0 = 0.35$.

#### C. Integración Temporal y Amortiguamiento
El estado mecánico se actualiza en cada frame mediante integración de Euler amortiguada:

$$\vec{a}_i(t) = \vec{F}_{\text{steer}} + \vec{F}_{\text{idle}}$$
$$\vec{v}_i(t + \Delta t) = \left(\vec{v}_i(t) + \vec{a}_i(t)\right) \cdot \mu$$
$$\vec{x}_i(t + \Delta t) = \vec{x}_i(t) + \vec{v}_i(t + \Delta t)$$

Con factor de amortiguamiento viscoso $\mu = 0.92$.

---

### 3. Muestreo Tipográfico y Geometría en 4 Actos

#### Muestreo Tipográfico Offscreen (*TargetSampler*)
Cuando la presentación se encuentra en modo **Texto**, los caracteres se rasterizan en un búfer gráfico secundario (`p5.Graphics`) utilizando la tipografía *Inter Bold*. Se recorre la cuadrícula de píxeles luminosos ($R > 128$) con paso adaptable:

$$\text{Paso de muestreo } S = \max\left(3, \; \left\lfloor \sqrt{\frac{W \cdot H}{N_{\text{target}} \cdot 45}} \right\rfloor \right)$$

A cada coordenada válida se le suma un leve desplazamiento estocástico subpíxel para evitar artefactos de aliasing mecánico.

#### Las Esculturas Paramétricas de los 4 Actos
Cuando se conmuta al modo **Escultura** (o durante las transiciones narrativas), las posiciones meta $\{\vec{x}_{\text{target}}\}$ son computadas por funciones analíticas que mapean el sentido del discurso a lo largo de 13 diapositivas:

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                               ARCO NARRATIVO                                 │
├─────────────────────┬──────────────────────────┬──────────────┬──────────────┤
│ Acto 1: Origen      │ Acto 2: Comunidad        │ Acto 3:      │ Acto 4:      │
│ (Slides 1 a 5)      │ (Slides 6 a 9)           │ Relevo       │ Apertura     │
│                     │                          │ (10 a 12)    │ (Slide 13)   │
├─────────────────────┼──────────────────────────┼──────────────┼──────────────┤
│ • Monolito denso    │ • Clústeres orgánicos    │ • Doble      │ • Portal     │
│ • Esfera concentrada│ • Espesamiento de aristas│   hélice     │   perspectivo│
│ • Tríada gravitante │ • Puente en catenaria    │ • Vórtice /  │ • Grilla     │
│   (Academia,        │   entre dos horizontes   │   toroide    │   estructural│
│    Industria,       │                          │   entrelazado│   hacia QR   │
│    Ciudad)          │                          │              │              │
└─────────────────────┴──────────────────────────┴──────────────┴──────────────┘
```

1. **Acto 1 — Origen (`monolith_core`, `concentrated_sphere`, `triad_nodes`):**
   - Un solo nodo compacto que representa la institución y el auditorio.
   - En los slides 3 al 5, el núcleo experimenta una fisión armónica hacia tres atractores: **Academia**, **Industria** y **Ciudad**, estableciendo puentes elásticos de tensión.
2. **Acto 2 — Comunidad y Confianza (`organic_clusters`, `thickening_mesh`, `bridge_tension`):**
   - Agrupaciones micelares donde las aristas entre nodos vecinos aumentan su grosor ($w = 1.6\text{ px}$) y opacidad ($\alpha = 0.28$).
   - Culmina en un puente catenario de tensión que conecta los extremos del escenario.
3. **Acto 3 — Relevo e Hibridación (`double_helix`, `intertwined_vortex`):**
   - Las partículas se diferencian cromáticamente en dos especies generacionales: **Especie A** (Generación Pionera / Magenta `#E0218A`) y **Especie B** (Generación Emergente / Azul Eléctrico `#00B4D8`), cruzadas por travesaños dorados (`#FFB81C`).
   - Se trenzan en una doble hélice y un toroide dinámico continuo sin perder su individualidad.
4. **Acto 4 — Apertura y Futuro (`portal_grid`):**
   - La nube orgánica transmuta hacia un portal ortogonal y líneas de fuga en perspectiva cónica que encuadran el centro de la pantalla, guiando la atención del público hacia el código QR de cierre y los compromisos del auditorio.

---

### 4. Retracción Espacial Adaptativa (Capa Documental)

En los slides con registro documental (Slides **02, 04, 05, 08, 12 y 13**), el sistema activa el modo de retracción mediante una transformación afín suave:

$$\vec{x}_{\text{final}} = \mathbf{S} \cdot (\vec{x}_{\text{target}} - \vec{c}) + \vec{c} + \vec{\Delta}_{\text{offset}}$$

* **Factor de Escala:** $\mathbf{S} = 0.75$ (reducción del volumen del enjambre).
* **Desplazamiento Lateral:** $\vec{\Delta}_{\text{offset}} = (-0.22 \cdot W, \; 0)$ desplazando la escultura hacia la izquierda para despejar la zona áurea de la fotografía.
* **Atenuación Lumínica:** $\alpha_{\text{target}} = 140$ (en escala $0-255$), transformando el grafo en un marco atmosférico que acompaña la evidencia sin competir con ella.

---

### 5. Guía de Interacción y Atajos de Teclado

La interfaz web ha sido desarrollada con capacidades híbridas (online / offline) y controles accesibles tanto desde teclado para el orador como desde dispositivos táctiles o mandos de presentación:

| Entrada / Tecla | Elemento HUD | Función Operativa |
| :---: | :---: | :--- |
| <kbd>→</kbd> / <kbd>Espacio</kbd> | Botón `›` | **Avanzar Diapositiva:** interpola suavemente hacia el siguiente slide conservando la inercia de los nodos. |
| <kbd>←</kbd> | Botón `‹` | **Retroceder Diapositiva:** revierte los objetivos de atracción manteniendo la coherencia física continua. |
| <kbd>T</kbd> | Botón `✦ / 🔤` | **Alternar Modo (Toggle):** conmuta en caliente entre el estado **Texto Tipográfico** y el estado **Escultura Geométrica**. |
| <kbd>F</kbd> | Botón `⛶` | **Pantalla Completa (Fullscreen):** ajusta el canvas al viewport del auditorio sin distorsión de relación de aspecto. |
| <kbd>L</kbd> | Selector `PT/ES/EN` | **Conmutación Trilingüe:** cambia instantáneamente la narrativa entre Portugués (idioma oficial del evento), Español e Inglés. |

---

### 6. Estructura del Repositorio de la Bitácora

```
bitacora-clase/
├── README.md               # Documentación general y seguimiento del proyecto activo
├── unidad_1/               # Modelos estocásticos, probabilidad y caminatas aleatorias
│   ├── Actividad_02.md
│   ├── Actividad_03.md
│   ├── Actividad_04.md
│   ├── Actividad_05.md
│   ├── Actividad_06.md
│   └── Actividad_07.md
├── unidad_2/               # Sistemas complejos y vida artificial
│   └── Actividad_05.md
├── unidad_3/               # Fuerzas gravitacionales y singularidades
│   └── Actividad_04.md
├── unidad_4/               # Osciladores acoplados y sincronización colectiva
│   └── Actividad_02.md
└── unidad_5/               # Sistemas autónomos y proyectos integradores
    └── Actividad_01.md
```
