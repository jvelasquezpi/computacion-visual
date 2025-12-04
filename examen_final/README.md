# Examen Final - Punto 1: Procesamiento Básico de Imágenes

Este módulo del examen final se enfoca en la implementación de técnicas fundamentales de visión artificial utilizando **Python** y **OpenCV**. El objetivo es manipular la estructura de color y morfología de una imagen base para analizar diferentes efectos de procesamiento.

## 🛠️ Tecnologías Utilizadas
* **Lenguaje:** Python
* **Librería Principal:** OpenCV (`cv2`)
* **Recurso:** Imagen de prueba `guacamaya_roja.jpg`

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

![Proceso de transformación de imagen](path/to/your/summary_gif.gif)