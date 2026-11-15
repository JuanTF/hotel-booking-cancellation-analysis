# Notas técnicas y alcance de esta edición

## Cambios realizados

- README reescrito para presentar el notebook, el informe y el simulador.
- Archivos organizados con nombres sin espacios ni tildes.
- Rutas personales de Google Drive reemplazadas por `ARTIFACTS_DIR`, creado al inicio del notebook.
- Montajes de Drive reemplazados por comentarios, sin cambiar las transformaciones ni el entrenamiento.
- Bloques de GridSearch conservados como Markdown: sus distribuciones de SciPy no son válidas como parrilla de GridSearchCV. RandomizedSearchCV sigue siendo ejecutable.
- Salidas históricas conservadas en celdas no modificadas. Se borraron las salidas de las celdas editadas para evitar asociarlas al código nuevo.
- PBIX y captura conservados sin modificar su contenido.

## Evaluación

El código ajusta OneHotEncoder, OrdinalEncoder y MinMaxScaler sobre el conjunto completo antes de la separación de entrenamiento y prueba. La imputación también precede a esa separación. Se debe trasladar el ajuste de transformaciones a un pipeline entrenado solo con la partición de entrenamiento.

Se utilizan diferentes semillas de separación entre modelos (42 y 0), por lo que la comparación no usa siempre exactamente las mismas observaciones de prueba. La búsqueda aleatoria no fija `random_state`; sus resultados pueden cambiar.

La selección automática guardada incluye `assigned_room_type_E`, mientras que la lista manual de 36 variables para el ajuste final utiliza `assigned_room_type_F`. Conviene resolver esa diferencia antes de describir la selección como totalmente automática.

La salida inicial muestra 119 390 filas, mientras que una salida anterior a la eliminación explícita de duplicados ya muestra 87 409. Esto indica que las salidas guardadas no prueban por sí solas una ejecución limpia y secuencial. No se recalcularon los resultados en esta actualización.

Variables como habitación asignada o cambios de reserva deben revisarse según el momento en que se pretende predecir. Una evaluación temporal y la definición de ese momento son necesarias para aproximarse a un uso real.

## Relación con Hugging Face

El código público consultado el 15 de noviembre de 2026 aplica rangos manuales de escalado. En particular, el mes se escala con un rango de 1 a 12 en la aplicación; en el notebook se codifica con OrdinalEncoder (0 a 11) y no se incluye en MinMaxScaler. Existe, por tanto, una diferencia concreta entre ambos preprocesamientos.

El notebook exporta `modelo_XGBoost_hotel.pkl` antes de la optimización final. No demuestra que el archivo `modelo_xgboost.pkl` del Space sea el modelo final evaluado. No se descargó ni ejecutó ese pickle y no se comprobó una predicción interactiva.

La corrección recomendada es exportar juntos el modelo, los transformadores y el esquema de entrada, y verificar ambos recorridos con las mismas reservas. Esta edición organiza y documenta el repositorio; no modifica el Space.

## Power BI

El archivo contiene una página con 11 contenedores visuales y un modelo de datos incorporado. La captura tiene seleccionado 2016. Las cifras de la captura no deben presentarse como resultados de todo el dataset o del conjunto de prueba.

No se abrió el PBIX en Power BI Desktop ni se verificó su actualización. El símbolo $ del informe no confirma una moneda; tampoco se verificó la fórmula de la tarjeta de ingresos. Se mantiene el archivo original.

## Verificación realizada

Se comprobó la integridad del PBIX como archivo ZIP, la estructura JSON del notebook, la sintaxis de sus celdas de código y los enlaces locales del README. No se ejecutó el entrenamiento completo ni la búsqueda de hiperparámetros. Las dependencias son una base de instalación, no un entorno bloqueado y reproducido.
