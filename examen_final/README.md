# Examen Final - Punto 1: Procesamiento Básico de Imágenes

Este módulo del examen final se enfoca en la implementación de técnicas fundamentales de visión artificial utilizando **Python** y **OpenCV**. El objetivo es manipular la estructura de color y morfología de una imagen base para analizar diferentes efectos de procesamiento.

## 🛠️ Tecnologías Utilizadas
* **Lenguaje:** Python
* **Librería Principal:** OpenCV (`cv2`)
* **Recurso:** Imagen de prueba `guacamaya_roja.jpg`

---
## Instrucciones de Ejecución del Notebook

Para reproducir los resultados de este experimento, sigue estos pasos en tu entorno local o en la nube (Google Colab).

### 1. Instalación de Dependencias
Asegúrate de tener instaladas las librerías de procesamiento de imágenes y visualización:

```bash
pip install opencv-python matplotlib numpy
```
---

## 1. Separación de Canales de Color (RGB)
Se realizó la descomposición de la imagen original en sus tres componentes aditivos fundamentales.

* **Metodología:** Carga de la imagen y división de canales (Split).
* **Visualización:** Cada canal (Rojo, Verde, Azul) se representó en escala de grises para facilitar el análisis de la intensidad luminosa de cada color específico independiente de los otros.

---

## 2. Filtros de Procesamiento
Se aplicaron transformaciones para modificar las características de frecuencia de la imagen (suavizado y realce).

| Tipo de Filtro | Técnica | Efecto Visual Observado |
| :--- | :--- | :--- |
| **Suavizado** | Desenfoque Gaussiano (Kernel 5x5) | **Reducción de Ruido:** La imagen resultante adquiere un aspecto borroso. Se eliminan los detalles finos y el ruido de alta frecuencia mediante el promediado de píxeles vecinos. |
| **Realce** | Sharpening (Agudizamiento) | **Definición de Bordes:** Aumenta el contraste local en los bordes. La imagen se percibe más nítida, resaltando líneas, contornos y texturas. |

---

## 3. Operaciones Morfológicas
Estas operaciones se ejecutaron sobre la versión en **escala de grises** de la imagen, utilizando un elemento estructurante (kernel) de **5x5**.

### 📉 3.1. Erosión
* **Acción:** Elimina píxeles de los límites de los objetos.
* **Resultado:** Las regiones brillantes (blancas) se **reducen** o "adelgazan".
* **Utilidad:** Ideal para separar objetos que están ligeramente conectados o eliminar ruido puntual pequeño (puntos blancos sobre fondo oscuro).

### 📈 3.2. Dilatación
* **Acción:** Añade píxeles a los límites de los objetos.
* **Resultado:** Las regiones brillantes (blancas) se **expanden** o "engrosan".
* **Utilidad:** Sirve para rellenar pequeños agujeros dentro de objetos, unir elementos fragmentados o hacer más evidentes las características principales.

---

## Resumen Visual

A continuación se muestra la secuencia completa de transformaciones aplicadas a la imagen original:

![conmutacion_camaras](https://github.com/user-attachments/assets/6ad72b4c-e692-4605-ba74-be5efbfb8255)


---

# Punto 2: Escena Interactiva en Three.js

Este punto del examen consiste en la creación de una escena 3D compuesta y animada utilizando el editor gráfico de **Three.js**. El proyecto integra primitivas geométricas texturizadas, un sistema de iluminación variable y scripts personalizados para controlar la cámara y el entorno.

##  Contenido de la Escena

La composición incluye los siguientes elementos fundamentales:

### 1. Objetos Geométricos (Mesh)
Se han dispuesto tres figuras primitivas con texturas aplicadas para demostrar el mapeado UV y materiales:
* ** Cubo:** Elemento central con texturizado.
* **Esfera:** Objeto con superficie curva texturizada.
* **Cilindro:** Primitiva vertical con texturizado.

### 2. Iluminación y Cámaras
* **Luces:** Configuración de múltiples fuentes de luz para generar sombras y volumen en los objetos.
* **Cámaras:** Uso de `OrthographicCamera` y perspectivas.
* **Animación de Cámara:** Se incluye una lógica de movimiento que rota la escena y modifica el zoom progresivamente.

---

## ⚙️ Lógica y Scripts (Comportamiento)

El proyecto no es estático; incluye scripts embebidos en el archivo JSON que controlan la animación en tiempo real:

| Script | Funcionalidad |
| :--- | :--- |
| **MovementCamera** | Controla la transformación de la cámara. Realiza una **rotación** constante en el eje Y (`0.0008`) y un **alejamiento** progresivo (zoom out) reduciendo la escala hasta un límite de 0.5. |
| **Skye / Background** | Modifica dinámicamente el color de fondo (interpolación de azules) para dar ambiente a la escena. |
| **LightDayNight** | (Si aplica según configuración) Controla la intensidad o color de la luz para simular cambios ambientales. |

---

## 🚀 Instrucciones de Ejecución

Este proyecto se distribuye como un archivo de escena `.json` y debe ser ejecutado en el entorno web de Three.js.

### Pasos para visualizar:

1.  **Descargar el archivo:** Asegúrate de tener el archivo `exame_final.json` en tu equipo.
2.  **Abrir el Editor:** Ingresa a la web oficial del editor:
    > 🔗 **[https://threejs.org/editor/](https://threejs.org/editor/)**
3.  **Importar el Proyecto:**
    * En el menú superior, ve a `File` > `Import`.
    * Selecciona el archivo `exame_final.json`.
4.  **Reproducir:**
    * Una vez cargada la escena, pulsa el botón **Play** en la barra superior para iniciar los scripts de animación y movimiento de cámara.

---

## 🎞️ Demostración Visual

A continuación se observa la ejecución de la animación, mostrando la rotación de cámara y los objetos texturizados:

![conmutacion_camaras_threejs (1)](https://github.com/user-attachments/assets/e24bbed1-5286-4294-a890-43cca2d52dd4)


