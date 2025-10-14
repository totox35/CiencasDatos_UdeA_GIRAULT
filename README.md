# CiencasDatos_UdeA_GIRAULT

Este repositorio contiene mi trabajo para el curso "Ciencias de Datos" en la Universidad de Antioquia.

## Proyecto: Predicción de la duración de la estancia hospitalaria

### Contexto y motivación

Anticipar la duración de las estancias hospitalarias es un gran desafío para la gestión sanitaria, especialmente para optimizar la disponibilidad de camas y la asignación de recursos. Este proyecto busca predecir el número de días que un paciente permanecerá hospitalizado, utilizando variables clínicas y demográficas extraídas de datos hospitalarios reales.

### Fuentes de datos

- Conjunto de datos principal: [Hospital Length of Stay Dataset (Microsoft, Kaggle)](https://www.kaggle.com/datasets/aayushchou/hospital-length-of-stay-dataset-microsoft)
- Las variables incluyen: comorbilidades (ICD-9), indicadores biológicos (IMC, creatinina, BUN, respiración), género, número de readmisiones y diagnósticos secundarios.

### Metodología

- **Selección de variables** guiada por literatura médica y exploración de datos.
- **Limpieza de datos** para tratar valores atípicos y datos faltantes.
- **Filtrado y análisis de outliers**: Los valores atípicos se detectan mediante métodos estadísticos (IQR, Z-score) y luego se revisan por relevancia clínica antes de decidir su inclusión o exclusión.
- **Análisis descriptivo**: distribuciones, diagramas de caja y matrices de correlación para comprender el comportamiento de las variables.
- **Análisis de Componentes Principales (PCA)** para reducir la dimensionalidad e identificar ejes clínicos latentes.
- **Clustering (K-means)** para revelar perfiles de pacientes según la complejidad clínica.

### Primeros resultados

- **Comorbilidades y readmisiones** son los principales factores de estancias hospitalarias prolongadas. Los pacientes con más diagnósticos o readmisiones frecuentes tienden a permanecer más tiempo.
- **Las variables biológicas por sí solas** (IMC, creatinina, BUN, respiración) no explican suficientemente la duración de la estancia; se requieren enfoques multivariables.
- **PCA** muestra que cinco componentes principales explican el 88% de la varianza, destacando la naturaleza multidimensional de los datos hospitalarios (carga clínica, función renal, respiración, diagnósticos secundarios, IMC).
- **Clustering K-means** (k=2) identifica dos perfiles claros de pacientes: estancias cortas y frecuentes vs. estancias largas y complejas. Más clusters no aportan interpretabilidad.
- **Los outliers** (especialmente en BUN y respiración) suelen ser clínicamente relevantes y no deben descartarse sin revisión médica.

### Próximos pasos

- Refinar la gestión de outliers combinando experiencia estadística y clínica.
- Desarrollar y comparar modelos predictivos supervisados (regresión, árboles de decisión, redes neuronales).
- Evaluar el rendimiento y la interpretabilidad de los modelos para su uso práctico en hospitales.

---

Este proyecto sienta las bases para una modelización predictiva robusta en la gestión hospitalaria, combinando rigor estadístico y visión clínica para mejorar la atención al paciente y la planificación de recursos.