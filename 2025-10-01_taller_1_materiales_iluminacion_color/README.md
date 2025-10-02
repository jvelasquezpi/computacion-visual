# Taller - Materiales, Iluminación y Color

## Fecha
`2025-10-01` – Fecha de entrega

---

## Objetivo del Taller

Aplicar y demostrar el conocimiento sobre materiales PBR (Physically Based Rendering), esquemas de iluminación y modelos de color para construir una escena 3D cohesiva y estilizada, controlando aspectos como texturas, shaders, y la percepción visual del ambiente.

---

## Conceptos Aprendidos

- [x] Iluminación (Key, Fill, Rim, HDRI)
- [x] Materiales y texturas PBR (Roughness, Metalness)
- [x] Shaders y efectos visuales
- [x] Cámaras (Perspectiva y Ortográfica)
- [x] Animaciones (de cámara, luces u objetos)
- [x] Modelo de color (RGB/HSV, CIELAB)

---

## Herramientas y Entornos

- Three.js Editor

---

## Estructura del Proyecto

2025-10-01_taller_1_materiales_iluminacion_color/

```
├── threejs/
├── glb_models/
├── textures/
├── renders/
├── README.md
```
---

## Implementación

El proceso se centró en la configuración progresiva de la escena, desde la importación de los modelos hasta la definición de la atmósfera final mediante luces y materiales.

### Etapas realizadas
1. **Preparación de la Escena:** Se importaron los tres modelos (`Cow.glb`, `House.glb`, `Tractor.glb`) al entorno de Three.js Editor. Se realizaron las transformaciones iniciales de escala y rotación para componer la escena de la granja.
2. **Aplicación de Algoritmos y Materiales:** Se implementó el esquema de iluminación completo (Hemisférica, Key, Fill, Rim). Se ajustaron los parámetros PBR (metalness, roughness) de la casa y el tractor. Se desarrolló y aplicó un shader procedural de suciedad basado en ruido FBM al modelo de la vaca.
3. **Visualización e Interacción:** Se configuraron dos cámaras: una perspectiva para la vista cinematográfica principal y una ortográfica para una vista técnica superior. Se programaron las animaciones de rotación orbital de la escena y el ciclo dinámico de día/noche.
4. **Guardado de Resultados:** Se realizaron capturas de pantalla desde ambas cámaras para documentar los resultados estáticos y se grabó un video para mostrar las animaciones y los efectos dinámicos.

### Código relevante

Este código implementa el movimiento de la cámara dentro de la escena, lo cual es fundamental porque permite al usuario explorar el entorno 3D desde diferentes perspectivas, mejorando la comprensión espacial y la interacción con los objetos renderizados.

```glsl
var scaleSpeed = 0.0001; // Velocidad de alejamiento

function update() {
    // Rotar la escena
    this.rotation.y += 0.0008;
    
    // Reducir la escala gradualmente (alejar)
    this.scale.x -= scaleSpeed;
    this.scale.y -= scaleSpeed;
    this.scale.z -= scaleSpeed;
    
    // Evitar que se haga demasiado pequeña
    if (this.scale.x < 0.5) {
        this.scale.set(0.5, 0.5, 0.5);
  
    }
}
```
---

## Imagen de la Animación

Capturas de pantalla obligatorias de la escena.

[Enlace a tu video en YouTube, Vimeo, etc.](URL_DE_TU_VIDEO)
---

## 🎬 Video de la Animación

El siguiente video muestra la escena en movimiento, destacando la rotación de la cámara, la alternancia entre vistas y el efecto de los shaders y la iluminación dinámica.

[Video ](URL_DE_TU_VIDEO)

---
## Modelos GLB Usados

Se utilizaron los siguientes modelos 3D, todos obtenidos de la plataforma **Poly Pizza**.

* **Cow.glb**
    * **Fuente:** [Poly Pizza](https://poly.pizza/)
    * **Modificaciones:** Se aplicó una escala de `0.8`. El material base fue reemplazado por un shader procedural que simula suciedad mediante ruido FBM (Fractal Brownian Motion), con parámetros PBR de `metalness: 0` y `roughness: 1`.

* **House.glb**
    * **Fuente:** [Poly Pizza](https://poly.pizza/)
    * **Modificaciones:** Se escaló el modelo a `11.45` y se aplicó una rotación de `-20` grados en el eje Y. Los parámetros PBR del material se ajustaron a `metalness: 0` y `roughness: 0.5`.

* **Tractor.glb**
    * **Fuente:** [Poly Pizza](https://poly.pizza/)
    * **Modificaciones:** Se mantuvo la escala en `1`, pero se aplicó una rotación de `-10` grados en el eje Y. El material se ajustó para simular una pintura de tractor con `metalness: 0.7` y `roughness: 0.35`.

---

## 💡 Iluminación

Se implementó un esquema de iluminación completo para dar volumen, color y realismo a la escena.

- **Luz Hemisférica (Ambiental):** Proporciona la iluminación base global y define el tono del ambiente.
  - **Color del Cielo:** `rgb(0, 170, 255)` (un azul celeste que simula la luz del día).
  - **Color del Suelo:** `rgb(126, 87, 1)` (un tono tierra que simula la luz rebotada desde el suelo).

- **Esquema de Tres Puntos:** Se utilizó para resaltar los modelos principales.
  - **Luz Principal (Key Light):** Una luz direccional fuerte que actúa como el sol.
    - **Intensidad:** `4.0`
    - **Color:** `rgb(232, 226, 91)` (amarillo cálido).
  - **Luz de Relleno (Fill Light):** Una luz suave para reducir las sombras duras de la luz principal.
    - **Intensidad:** `0.3`
    - **Color:** `rgb(169, 194, 244)` (azul frío para simular la luz del cielo).
  - **Luz de Contorno (Rim Light):** Una luz colocada detrás de los objetos para separarlos del fondo.
    - **Intensidad:** `0.5`
    - **Color:** `rgb(255, 255, 255)` (blanco puro).

---

## 🎨 Materiales y Shaders Procedurales

El enfoque principal fue la creación de un material procedural para simular desgaste y suciedad.

### Shader de Suciedad (Aplicado a la Vaca)
- **Tipo:** Se utilizó un `ShaderMaterial` personalizado.
- **Técnica:** El efecto de suciedad se generó mediante un **ruido procedural FBM (Fractal Brownian Motion)** de 5 octavas para lograr un patrón orgánico y detallado. Además, se aplicó un **gradiente vertical** para simular una acumulación más realista en la parte inferior del modelo.
- **Parámetros Clave:**
  - `dirtIntensity`: `0.5` (controla la cantidad de suciedad)
  - `dirtScale`: `5.0` (define el tamaño de las manchas)
  - `dirtColor`: `#4a3728` (color marrón lodo)

---

## 🎥 Cámaras y Animaciones

Se utilizaron dos tipos de cámaras para mostrar la escena desde diferentes puntos de vista, cada una con una intención específica.

- **Cámara Perspectiva:** Es la cámara principal, diseñada para ofrecer una vista natural y cinematográfica de la granja. Su uso permite apreciar la profundidad, la escala de los objetos y la composición general de la escena tal como la vería un observador.
  - **Campo de Visión (FOV):** `29.68°`
  - **Posición Inicial:** `(-43.688, 62.112, -26.254)`

- **Cámara Ortográfica:** Se configuró para ofrecer una **vista cenital (superior)** de la escena. Esta proyección elimina la distorsión de la perspectiva, lo que es ideal para mostrar la distribución y la disposición espacial de los objetos de manera técnica, similar a un plano o un mapa.

- **Movimientos Aplicados:**
  - **Rotación Orbital:** La escena completa rota continuamente a una velocidad de `0.005` radianes por frame para ofrecer una vista de 360°.
  - **Ciclo Día/Noche:** El color del cielo (fondo) transiciona suavemente entre dos tonos de azul a una velocidad de `0.0003`, simulando el paso del tiempo.

---

## 🌈 Modelo de Color

La paleta de colores fue seleccionada para crear un ambiente definido y asegurar un buen contraste visual.

### Cielo (Ciclo Día/Noche)
- **Día:** Azul claro - `RGB(77, 128, 230)` / `HSV(220°, 67%, 90%)`
- **Noche:** Azul oscuro - `RGB(51, 77, 102)` / `HSV(210°, 50%, 40%)`

### Materiales Procedurales
- **Suciedad (Lodo):** `RGB(74, 55, 40)` / `HSV(26°, 46%, 29%)`

---
## Prompts Usados


```text
"Cómo configurar un esquema de iluminación de tres puntos en Three.js editor"
"Como generar ruido FBM y simular suciedad en Three.js"
"Justificación para usar cámara perspectiva vs ortográfica en renderizado 3D"
"Calcular valores HSV a partir de un color RGB para un ciclo de día y noche"
```
---

## Reflexión Final

Con este taller, logré una comprensión más profunda de cómo la **interacción entre materiales PBR, iluminación y color** es fundamental para construir una atmósfera creíble. La parte más desafiante fue ajustar los parámetros del shader procedural para que la suciedad se viera natural y no repetitiva.

La implementación del ciclo día/noche y el esquema de tres luces fue especialmente interesante, ya que permitió observar cómo un mismo modelo puede transmitir sensaciones muy diferentes según la luz que recibe.

En futuros proyectos, me gustaría explorar la animación de los parámetros de los shaders en tiempo real para simular, por ejemplo, cómo la lluvia limpiaría la suciedad de los objetos o cómo los materiales se desgastan con el tiempo.

---

## Checklist de Entrega

- [x] Carpeta `2025-10-01_taller_1_materiales_iluminacion_color`
- [x] Código limpio y funcional
- [x] GIF incluido con nombre descriptivo (si el taller lo requiere)
- [x] Visualizaciones o métricas exportadas
- [x] README completo y claro
- [x] Commits descriptivos en inglés

---