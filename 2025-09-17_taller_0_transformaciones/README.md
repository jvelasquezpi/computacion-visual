# Taller 0 - Transformaciones Básicas en Computación Visual

## Fecha
`2025-09-17` – Fecha de entrega o realización

---

## Objetivo del Taller

Explora las transformaciones geométricas fundamentales —traslación, rotación y escala— aplicadas en distintos entornos visuales (Python, Unity, Three.js y Processing), mediante la creación de figuras u objetos básicos con animaciones dependientes del tiempo.

---

## Conceptos Aprendidos

Lista los principales conceptos aplicados:

- [x] Transformaciones geométricas (escala, rotación, traslación)
- [ ] Segmentación de imágenes
- [ ] Shaders y efectos visuales
- [ ] Entrenamiento de modelos IA
- [ ] Comunicación por gestos o voz
- [ ] Otro: _______________________

---

## Herramientas y Entornos

- Python (matplotlib, numpy, imageio)
- Unity (versión LTS, XR Toolkit, Shader Graph)
- Three.js / React Three Fiber
- Jupyter / Google Colab
- Processing (2D o 3D)



---

## Estructura del Proyecto

```
2025-09-17_taller_0_transformaciones/
├── python/
├── threejs/
├── processing/
├── README.md

```

---

## Implementación  

El proceso consistió en crear una figura o escena básica en cada entorno, aplicar transformaciones geométricas (traslación, rotación y escala), animar los cambios en función del tiempo y finalmente visualizar o guardar los resultados según las herramientas disponibles.  

### Etapas realizadas  
1. **Preparación de datos o escena:** definición de las figuras geométricas y configuración inicial del entorno.  
2. **Aplicación de modelo o algoritmo:** implementación de las transformaciones usando matrices o funciones propias de cada plataforma.  
3. **Visualización o interacción:** generación de animaciones y representación de las transformaciones a lo largo del tiempo.  
4. **Guardado de resultados:** exportación de animaciones como GIF en Python o visualización directa en Unity, Three.js y Processing.  


---

## Resultados Visuales

Python

Se genera una animación 2D de una figura (triángulo) que se transforma en el tiempo aplicando escala, rotación y traslación, utilizando matrices de transformación homogéneas. La animación se exporta como un archivo GIF utilizando la librería imageio.

Herramientas utilizadas

- numpy: para manejo de matrices y vectores

- matplotlib: para dibujar y guardar cada frame

- imageio: para crear el GIF animado


Transformaciones aplicadas: Escalado proporcional, Rotación alrededor del origen, Traslación en el plano XY

Las transformaciones se aplican en el siguiente orden:
M = Traslación × Rotación × Escala

Cada punto de la figura se transforma usando matrices 3x3 en coordenadas homogéneas.

Resultado

Se genera un archivo llamado transformacion.gif que muestra la evolución continua de la figura a lo largo del tiempo.

![transformacion](https://github.com/user-attachments/assets/96f12f06-c28d-443f-9a58-57eb229b6902)

---

## Prompts Usados

Enumera los prompts utilizados:

```text
“Cómo generar una animación en Python de una figura que rota y se traslada en el tiempo, y exportarla a GIF con imageio.”
“Cómo usar useFrame en React Three Fiber para animar una esfera con rotación y escala dinámica.”
“Explica cómo usar pushMatrix() y popMatrix() en Processing para aislar transformaciones.”
```

---

## Reflexión Final

Con este taller reforcé el uso de transformaciones geométricas básicas como traslación, rotación y escala, entendiendo mejor cómo se representan con matrices y cómo se aplican en distintos entornos.

Lo más interesante fue animar las figuras en función del tiempo, ya que permitió visualizar de forma dinámica los cambios. La parte más compleja fue adaptarse a las diferencias entre Python, Unity, Three.js y Processing.

En futuros proyectos mejoraría la organización del código y aplicaría estas transformaciones en escenas más completas, explorando interactividad y modelos más avanzados.

---

---

## Checklist de Entrega

- [x] Carpeta `YYYY-MM-DD_nombre_taller`
- [x] Código limpio y funcional
- [x] GIF incluido con nombre descriptivo (si el taller lo requiere)
- [x] Visualizaciones o métricas exportadas
- [x] README completo y claro
- [x] Commits descriptivos en inglés



