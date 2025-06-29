# Detección y Análisis de Árboles con DeepForest  
**Autor: Sebastian Mindiola**

Este proyecto aplica un modelo preentrenado de DeepForest para detectar árboles en imágenes aéreas, calcular métricas relevantes y realizar visualizaciones que permitan un análisis cuantitativo y visual de la vegetación.

## Requisitos

- Python ≥ 3.7  
- Conda  
- DeepForest v1.5.0  
- Bibliotecas utilizadas: `matplotlib`, `pandas`, `numpy`, `cv2`, `skimage`

Instalación recomendada mediante entorno Conda siguiendo:  
🔗 https://deepforest.readthedocs.io/en/v1.5.0/getting_started/install.html

---

## Flujo de trabajo

### 1. Carga y predicción

- Se carga una imagen RGB de alta resolución.
- Se utiliza el modelo preentrenado de DeepForest para detectar árboles.

### 2. Visualización

- Se muestran las cajas delimitadoras de árboles sobre la imagen original.
- Se asigna un identificador único a cada árbol detectado.

### 3. Cálculo de áreas

- Se calcula el área en píxeles de cada caja delimitadora (`(xmax - xmin) * (ymax - ymin)`).
- Se almacena en un dataframe con columnas:  
  `id_arbol`, `xmin`, `ymin`, `xmax`, `ymax`, `area_px`.

### 4. Índices de vegetación

- Se calcula para cada caja:
  - **ExG**: `2*G - R - B`
  - **VARI**: `(G - R) / (G + R - B + ε)`
- Se añade al dataframe la media de cada índice: `ExG_mean`, `VARI_mean`.

### 5. Histogramas RGB

- Se generan histogramas para los canales R, G y B:
  - Comparación entre píxeles de árboles y fondo.

### 6. Diagramas de dispersión RGB

- Se calcula el promedio de R, G y B en regiones con y sin árboles.
- Se grafican combinaciones RGB: `R vs G`, `G vs B`, `R vs B`.

---

## Archivos generados

- `deepforest.ipynb`: Notebook con el desarrollo completo del análisis.
- `arboles_detectados.csv`: DataFrame con información de detección y métricas.
- Imágenes de visualización y gráficos embebidos o exportados.

---

## Recursos

- Documentación: https://deepforest.readthedocs.io/en/v1.5.0/
- Tutorial utilizado: https://deepforest.readthedocs.io/en/v1.5.0/getting_started/intro_tutorials/03_use_pretrained_model.html
- Repositorio oficial: https://github.com/weecology/DeepForest
