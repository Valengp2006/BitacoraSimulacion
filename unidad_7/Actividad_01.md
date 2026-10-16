# Bitácora del proyecto: Hechizos

**Unidad 7 · Sistema tipográfico jugable con DISNEY**

**Repositorio:** https://github.com/Valengp2006/hechizos-disney 

**Sitio publicado:** https://valengp2006.github.io/hechizos-disney/ 

## 0. Resumen

| Aspecto | Decisión |
| --- | --- |
| Organización | Disney (entretenimiento y narración; público familiar e intergeneracional) |
| Misión | Hacer feliz a la gente: fomentar la felicidad y el bienestar de niños y familias |
| Atributo | **Magia y fantasía**, al servicio de esa misión |
| Verbo central | *Encantar* (hechizar y también deleitar) |
| Efecto buscado | Asombro, alegría y calidez |
| Contexto de uso | Pantalla interactiva en un evento o exhibición |
| Entrada | Mouse (dejé la entrada por mano prevista y pospuesta) |
| Duración de una partida | De 3 a 4 minutos como máximo (probado) |
| Stack | Vite, three.js, opentype.js y Web Audio; sin otras dependencias |
| Tipografía | Cinzel Bold (licencia OFL), local en `public/fonts/` |

**Mi idea en una frase.** Una pantalla casi oscura y un punto de luz que sigue al cursor. Las letras no se ven: cada una guarda un hechizo que un gesto abre, un minijuego despierta y que la convierte en un objeto de cuento. Cuando las seis despiertan, convergen en la palabra y de sus astas crece un castillo genérico.

**Regla de oro del encargo, que respeté.** Jugable es explorar y descubrir: sin puntuación, niveles ni condición de victoria. El castillo es un cierre, no una meta.

## 1. Concepto

### 1.1 El atributo como concepto: magia y fantasía

Para mí, la **magia y la fantasía** son la manera en que Disney cumple su misión de hacer feliz a la gente: convierte lo cotidiano en un lugar donde lo que se sueña puede ocurrir. La **fantasía** es el mundo que se imagina; la **magia** es lo que lo hace posible y lo que la persona siente al verlo pasar. Juntas no son un adorno: son el medio por el que la marca invita a soñar en grande y a sentirse bienvenida.

**En qué me baso**
- **Misión (fuente primaria).** Compromiso Disney, sección Institucional: la compañía busca fomentar la felicidad y el bienestar de niños y familias, e invitar a soñar en grande.
- **Magia y fantasía como identidad (fuente secundaria).** Oropeza, C. (21/04/2023), *La magia detrás del branding de Disney*, We Build It: presenta la misión como "hacer a la gente feliz en todo el mundo", el castillo como magia, fantasía y el sueño de un lugar donde todos pueden ser felices, y el polvo de hadas como elemento visual de la marca.

**Cómo lo interpreto.** La magia y la fantasía no se *explican*, se *descubren provocándolas*. Mi pieza no muestra la magia hecha: deja que la persona la desencadene con un gesto y reciba una respuesta cálida que transforma la letra.

### 1.2 Evolución del concepto

| Etapa | Concepto | Por qué cambió |
| --- | --- | --- |
| 1 | Dar vida a lo inanimado / cuidar | La mecánica se sentía de gestión y no mágica; yo buscaba asombro |
| 2 | Hacer posible lo imposible / conjurar | Lo imposible producía espectáculo, no calidez; la misión oficial de la marca es de afecto |
| 3 | Hacer feliz a la gente: magia y fantasía / encantar | Concepto vigente, apoyado en la fuente oficial |

Dos desvíos de diseño dentro de la etapa 3:
- **Descarté una propuesta de volumen 3D con iconos externos.** No me terminó de convencer: prefería el concepto anterior (la Y como árbol, la D como portal). Volví a los hechizos originales (portal, gravedad invertida, cinta, relámpago, faro, árbol), conservando la misión, el verbo *encantar* y una paleta cálida.
- **Retiré del código los hechizos "felices" intermedios** (campanada de luz, rebote ligero, cascada de chispas, amanecer, floración) tras probarlos.
 
## 2. Decisiones técnicas

| Decisión | Alternativas | Razón |
| --- | --- | --- |
| **three.js** con cámara ortográfica (1 unidad = 1 px) | p5.js (primera versión) | Decidí cambiar: más control de la luz aditiva, partículas, shaders y relleno. En píxeles, los umbrales de gestos significan lo mismo en pantalla |
| **Cinzel Bold** local, leída con **opentype.js** | Cormorant Garamond, Playfair Display | Astas rectas que se vuelven torres; licencia OFL; los contornos permiten rellenar, muestrear y repetir |
| Muestreo de puntos por **longitud de arco**, con temblor de mano determinista | Puntos al azar | Misma letra y mismos parámetros dan los mismos puntos |
| **Determinismo**: ningún resultado depende del azar | Aleatoriedad en los hechizos | Requisito del encargo; el azar solo decora, y sale de funciones fijas del índice |
| **Un solo `config.js`**, comentado | Constantes dispersas | Poder predecir y verificar el efecto de cambiar un parámetro |
| **Entrada unificada** `{x, y, vx, vy, grab, source, active}` | Mouse y mano por separado | El resto del sistema no sabe de dónde viene el punto; la mano se suma después |
| **Reconocedor de gestos puro** sobre trayectorias | Redes o plantillas | Determinista, depurable y sin dependencias; cada gesto tiene métricas y umbrales |
| Gestos evaluados en **varias ventanas** (0.3 a 2.4 s) con progreso | Una ventana fija de 1 s | Con una ventana fija el gesto dependía de la velocidad (hallazgo de la prueba) |
| **Seis estados por letra** | Booleano dormida o despierta | Cada estado tiene su respuesta perceptible; es el modelo que puedo explicar y verificar |
| **Minijuego entre el gesto y el hechizo** | Hechizo directo al acertar | Quise que descubrir cada letra fuera un minijuego |
| **Luz aditiva** y halos como sprites | Bloom en postproceso | Barato y suficiente; la luz se acumula donde se cruzan los trazos |
| **Fondo en shader** (cielo y niebla) | Imagen estática | Orgánico y reactivo al cursor |
| **Sonido sintetizado** con Web Audio, una nota por letra | Música en loop de archivo (apagada por ahora) | Sin archivos ni licencias; Re-Mi-Fa#-La-Si-Re forma la palabra al despertar en orden |
| **Pantalla de inicio con clic** | Bandera de Chrome para autoplay | El navegador exige un gesto para el audio; el clic lo enciende y da paso al cuento |
| **Modo performance y dev** (Tab, `?dev`) | Una sola vista | El público no ve depuración; en dev hay panel de gestos, FPS y tiempo de JS por frame |
| **Despliegue** con GitHub Actions a GitHub Pages | Subir `dist/` a mano | Se publica solo en cada push; HTTPS para la cámara futura |
| **`try/catch` en el ciclo de dibujo** | Dejar que un error lo detenga | Un error por frame congeló la versión publicada |

**Dos reglas técnicas que saqué del proceso:** no depender de nombres de funciones (el minificador de producción los cambia) y probar el build compilado con interacción real antes de cada entrega.

## 3. Proceso de diseño

### 3.1 Principios de partida

- Los elementos gráficos que construyen el significado salen de las letras.
- Jugable es explorar y descubrir: sin puntuación, niveles ni victoria.
- La persona juega **antes** de que se le explique la intención.
- Todo es determinista y todos los parámetros viven en un solo archivo.
- No reproduzco el logo, la caligrafía, la silueta del castillo ni personajes de Disney.

### 3.2 Las letras y su recorrido

| Letra | Gesto que la abre | Minijuego | Hechizo | Objeto |
| --- | --- | --- | --- | --- |
| D | círculo | hazla sonar (dar vueltas) | portal | campana |
| I | subir y bajar | enciende la vela | gravedad invertida | vela |
| S | barrido o frotar de lado a lado | sigue la luz | cinta | cinta |
| N | agitar | agita el cielo | relámpago | estrella |
| E | quedarse quieto | calma las cuerdas | faro | arpa |
| Y | mantener y soltar | riega la semilla | constelación-árbol | flor |

**Encadenamientos (la magia se contagia):** la cinta de la S, si va hacia un portal abierto de la D, es absorbida en espiral y sale dorada; si cruza la columna de la I, esta la levanta; la chispa del relámpago de la N pasa el relevo a la letra siguiente (N a E). Cuando una letra despierta, las ya despiertas parpadean juntas.

### 3.3 Letras que se vuelven objetos
- **Origen:** encontré un abecedario ilustrado donde cada letra es un objeto y aun así se lee como letra. Tomé solo la **idea**, no los dibujos.
- **Estilo que elegí:** objeto iluminado sobre la oscuridad (colores propios, recortado por la luz del cursor).
- **Objetos y alternativas que exploré:**
  - **I:** globo, pluma, llave y vela. Elegí la **vela** (conserva la silueta de la I, usa la luz y la cera gotea hacia arriba con la gravedad invertida).
  - **E:** sol (descartado por venir de un hechizo anterior), faro (descartado por poco lógico), arpa y banderines. Elegí la **arpa**, porque los banderines repetían los mástiles del castillo.
- **Implementación:** el objeto es el **relleno de la propia letra** más pocos detalles geométricos (asa, llama, rayos, flor).

### 3.4 Descubrir sin que se lo expliquen
- **Pistas en el polvo:** al acercarse, el polvo de la letra insinúa su gesto (gira, sube, se mece, vibra, respira, se recoge).
- **Letra que se entreabre** en proporción al avance del gesto, incluso si es lento.
- **Luz-invitación:** si nadie juega durante unos segundos, una luz tenue pasea sola.
- **Guía siempre visible** (decisión mía tras ver que los controles no eran claros): barra con seis fichas, el paso actual con su gesto animado y la letra del paso que **late** en la oscuridad.
- **Sin spoilers:** las fichas usan un orden que no forma la palabra y muestran el símbolo del gesto con una interrogación; la letra y el objeto se revelan solo al despertar. La guía desaparece al completar la palabra.
- **La persona juega, la guía acompaña** (principio que me fijé): quité un cursor fantasma que jugaba solo y un empujoncito que completaba el juego. La ayuda ahora solo *facilita* el reto y la guía da indicaciones vivas ("vas bien", "¡casi!", "si paras, se frena").
- **Pista explícita:** tras 18 s sin avanzar, la barra da la instrucción paso a paso y el gesto se dibuja grande junto a la letra.

### 3.5 Narrativa y entrada
- **Pantalla de inicio** ("Una aventura de luz", botón *Comenzar*): el clic enciende el audio y da paso al cuento. Vuelve para cada visitante nuevo tras el reinicio por inactividad.
- **Cuento** escrito por un lápiz de luz con la propia tipografía: *Había una vez… / una palabra dormida en la oscuridad. / Esperaba a que alguien la hiciera sonreír.*, con una nota por línea.

### 3.6 Dirección de arte
- **Inicio:** negro casi liso con puntos y contornos punteados; lo vi demasiado artificial y busqué algo más orgánico y estilo Disney.
- **Fondo:** cielo de crepúsculo en shader, niebla en dos capas, estrellas que titilan y luces desenfocadas; reacciona al cursor (la niebla se aparta y las estrellas cercanas brillan).
- **Letras:** temblor de mano determinista, relleno con luz y sombra, grano de papel, brillo de borde y aura cálida.
- **Castillo:** siluetas rellenas con ventanas doradas, banderines, puerta de la D como arco iluminado y una capa lejana de colinas y torres pequeñas para dar profundidad.
- **Paleta azul:** tras la primera prueba con una persona, me recomendó usar tonos más azules, característicos de Disney. Cielo, castillo y capa lejana pasaron a azules reales con dorado como contraste; la cinta es azul real, la estrella azul hielo y la flor verde-azulada.

### 3.7 Sonido
- Capa sintetizada de celesta o caja de música con eco, sin archivos ni licencias.
- **Una nota por letra** en la pentatónica de Re mayor, en el orden de la palabra: despertar las letras en orden forma una escala ascendente.
- Eventos con sonido: nota por línea del cuento, letra sensible, apertura del juego, avance (33 % y 66 %), gesto equivocado (nota baja y suave), despertar (arpegio), contagio, convergencia y revelación del castillo; el silencio del final baja el colchón a cero.

### 3.8 Propiedad intelectual
Hice un castillo genérico (asimétrico, sin torre central ni techos cónicos, sin estela de polvo en arco), sin círculos de Mickey ni personajes. De las fuentes de marca tomo solo el lenguaje de luz, polvo, brillo y calidez.

## 4. Pruebas, errores y lecciones

### 4.1 Cómo probé
- **Pruebas sintéticas de gestos** con trayectorias generadas (círculo, subir, bajar, barrido, zigzag, quieto, agarrar, y casos negativos como el temblor de 3 px). Es un script de apoyo, no está incluido en el repositorio.
- **Navegador de pruebas** con eventos de puntero y capturas, usando el panel de dev (estados, gestos, FPS y tiempo de JS por frame).
- **Build de producción** servido con `vite preview` y probado con mouse y gestos, a raíz del error de producción.
- **Pruebas con una persona** y prueba de sonido y duración (ver sección 9).

### 4.2 Errores que encontré

| Hallazgo | Causa | Solución | Lección |
| --- | --- | --- | --- |
| La app no arrancaba | Una variable (`letters`) se usaba antes de declararse | La declaré antes del registro que la usa | Orden de inicialización |
| Un círculo disparaba dos veces | La trayectoria seguía acumulándose durante el enfriamiento | No acumular durante el enfriamiento | Consumir el gesto |
| Los gestos se asignaban a la letra equivocada | Medía el centro del trazo, contaminado por la aproximación | Medir el final del trazo y, luego, preferir la letra cuyo gesto coincide | El gesto pertenece a donde termina |
| El juego de la N nunca terminaba | La energía topaba en 1 y se le restaba el decaimiento (0.994) | Umbral con margen | Cuidar el orden tope-decaimiento |
| Los rellenos de las letras no se veían | Triángulos con la cara al revés (el eje y va hacia abajo) | `DoubleSide` | Sistemas de coordenadas |
| Las colinas lavaban las letras | three.js ordena primero por grupo y luego por objeto | Grupos con orden propio para fondo y castillo | Orden de dibujo |
| **Escena congelada en producción** | Indexé una tabla con `fn.name` y el minificador renombra funciones | Claves explícitas y `try/catch` de seguridad | No depender de nombres; probar el build compilado |
| El error seguía viéndose tras corregirlo | El navegador usaba el HTML antiguo en caché | Recarga forzada o ventana limpia | Caché de Pages (10 min) |
| `npm install` fallaba | ml5 ejecutaba `patch-package` en `postinstall` | Quité ml5 | Dependencias pesadas y frágiles |

## 5. Pruebas con otras personas

### 5.1 Primera prueba

| Observación | Qué cambié |
| --- | --- |
| Movía la S de lado a lado y no pasaba nada; solo reaccionó al subir mucho la velocidad | El reconocimiento deja de depender de la velocidad y frotar de lado a lado abre la S |
| Intentó pasar a la I pero la guía seguía en la S | Un gesto junto a otra letra cierra el juego abierto y la guía sigue a la persona |
| La I solo se reconoció moviendo de arriba a abajo con más velocidad | Subir y bajar cuentan como el mismo gesto |
| La N era difícil de descubrir con el zigzag original | Pasó a "agitar el cursor" en cualquier eje |
| La guía mostraba la palabra en orden desde el inicio | Orden mezclado y letras reveladas solo al despertar |
| La guía tapaba las letras | Franja inferior reservada |
| Se recomendó usar tonos más azules, característicos de Disney | Paleta azul con dorado de contraste |

### 5.2 Prueba de sonido y duración
Hice la prueba con sonido: funciona bien y la experiencia completa dura de **3 a 4 minutos como máximo**.

## 6. Fuentes

| Fuente | Uso | Estado |
| --- | --- | --- |
| Compromiso Disney, sección Institucional (compromiso.disneylatino.com/institucional) | Misión y visión de la compañía | Verificada |
| Oropeza, C. (21/04/2023). *La magia detrás del branding de Disney*. We Build It | Magia y fantasía como identidad; castillo y polvo de hadas | Verificada (es un blog de marca: contexto, no respaldo académico) |
| ResearchGate: *Esquema de análisis de los atributos de la marca Disney y diversas producciones* | Posible respaldo académico de los atributos | **Sin verificar** (403) |
| Thomas, F. y Johnston, O., *The Illusion of Life* | Principios de animación (por ejemplo, *squash and stretch*) | Por verificar antes de citarla |
| Ji Lee, *Word as Image* | Las letras construyen significado | Referente de la actividad |
| Abecedario ilustrado de referencia | Idea de que la letra se vuelva objeto | Solo la idea, no sus dibujos |
| Cinzel (OFL), three.js, opentype.js, Vite | Tipografía y herramientas | Licencias libres |

## 7. Autoevaluación

**Nota:** 5
