# DeepForest

Realiza la configuración del ambiente de conda siguiendo las instrucciones en:  
🔗 https://deepforest.readthedocs.io/en/v1.5.0/getting_started/install.html

Usa un modelo preentrenado para contar árboles siguiendo el tutorial:  
🌲 https://deepforest.readthedocs.io/en/v1.5.0/getting_started/intro_tutorials/03_use_pretrained_model.html

# Recursos

- Documentación general de DeepForest: https://deepforest.readthedocs.io/en/v1.5.0/
- Repositorio oficial: https://github.com/weecology/DeepForest

---

# Tarea

## Objetivo
Aplicar un modelo preentrenado de DeepForest para detectar árboles en imágenes aéreas y realizar un análisis cuantitativo y visual a partir de los resultados obtenidos.

## Actividades

1. **Carga de imagen y predicción**
   - Carga una imagen RGB de alta resolución.
   - Aplica el modelo preentrenado para detectar árboles.

2. **Visualización con identificadores**
   - Muestra la imagen con las cajas detectadas y un identificador único para cada árbol.

3. **Cálculo de áreas y generación de un dataframe**
   - Calcula el área (en píxeles) de cada caja detectada.
   - Crea un dataframe con columnas como: `id_arbol`, `xmin`, `ymin`, `xmax`, `ymax`, `area_px`.

4. **Cálculo de índice de vegetación**
   - Calcula índices como:
     - ExG = `2*G - R - B`
     - VARI = `(G - R) / (G + R - B + ε)`
   - Calcula la media del índice dentro de cada caja y agrega columnas al dataframe: `ExG_mean`, `VARI_mean`.

5. **Histogramas RGB**
   - Genera histogramas para los canales R, G y B, comparando regiones detectadas como árboles vs. regiones no detectadas.

6. **Diagramas de dispersión RGB**
   - Calcula el promedio R, G, B de cada caja detectada y de muestras fuera de las cajas.
   - Grafica combinaciones (R vs G, G vs B, R vs B) usando colores distintos para árboles y no árboles.

## Entrega esperada

- Un notebook (recomendado: `analisis_arboles.ipynb`) que documente el flujo completo.
- El dataframe generado en CSV.
- Visualizaciones correspondientes (pueden estar embebidas en el notebook).
