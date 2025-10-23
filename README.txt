Predicción de Cancelación de Reservas (Notebook único)
=====================================================

Descripción
-----------
Este repositorio contiene **un único cuaderno** de Jupyter/Colab para predecir la **cancelación de reservas de un hotel**. El notebook incluye: limpieza y transformación de datos, análisis exploratorio (EDA), entrenamiento y comparación de modelos de clasificación y optimización del mejor modelo con ajuste de hiperparámetros.

Contenido del repo
------------------
- Predicción de Cancelación de Reservas.ipynb

Requisitos
----------
Opción A: **Google Colab** (recomendado) – no requiere instalación local.  
Opción B: **Local** con Python 3.10+ y las librerías:
- pandas, numpy
- scikit-learn
- matplotlib (y opcionalmente seaborn/xgboost/lightgbm)

Cómo usar
---------
**En Colab**
1. Sube el archivo `Predicción de Cancelación de Reservas.ipynb` a Colab.
2. Ejecuta las celdas en orden. En la sección de carga de datos, sube el CSV de reservas (por ejemplo `hotel_reservations.csv`).

**En local**
1. Crea y activa un entorno virtual:
   - Windows: `python -m venv .venv` y `.venv\Scripts\activate`
   - macOS/Linux: `python3 -m venv .venv` y `source .venv/bin/activate`
2. Instala dependencias mínimas:
   - `pip install pandas numpy scikit-learn matplotlib`
3. Abre el notebook:
   - `jupyter notebook "Predicción de Cancelación de Reservas.ipynb"`
4. En la celda de carga de datos, coloca la ruta al CSV (ej. `data/hotel_reservations.csv`).

Flujo del notebook
------------------
1. **Carga y preparación**: tratamiento de nulos, tipos de datos y codificación de variables.
2. **EDA**: visualizaciones y análisis de variables clave.
3. **Modelado**: comparación de clasificadores (p. ej., Regresión Logística, RandomForest, XGBoost*).
4. **Optimización**: búsqueda de hiperparámetros en el mejor modelo.
5. **Evaluación**: métricas en test (accuracy, precision, **recall** para detectar cancelaciones, F1, AUC).
6. **Exportación** (opcional): guardado del modelo entrenado con `joblib`.

Notas
-----
- El dataset no se incluye en el repositorio. Utiliza un CSV de **reservas de hotel** con columnas compatibles con lo indicado en el notebook.
- Ajusta rutas y nombres de columnas si tu archivo difiere.
- Marca tus resultados finales (métricas y gráficos) al final del notebook para facilitar la revisión.

Autoría
-------
Juan Tafur.
