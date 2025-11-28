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

### Fase 2: Refinamiento, Transformación y Estrategia de Modelado

En esta segunda etapa (Unidad 4), se evolucionó el proyecto desde un análisis descriptivo hacia una estrategia predictiva robusta, enfocada en la calidad del dato y la utilidad clínica.

#### 1. Ingeniería de Características y Transformación
Para mitigar el impacto de los valores atípicos (outliers) sin perder información clínica valiosa, se aplicaron transformaciones estadísticas avanzadas:
- **Yeo-Johnson:** Aplicado a variables sesgadas como `bloodureanitro` y diagnósticos secundarios.
- **RobustScaler:** Utilizado para `respiration`, garantizando que los valores extremos no distorsionen el modelo.
- **Categorización:** La variable objetivo (*Length of Stay*) se discretizó en tres niveles de riesgo operativo: *Corto* (0-2 días), *Medio* (3-7 días) y *Largo* (+8 días).

#### 2. Experimento de Manejo de Desbalance
Se diseñó un experimento comparativo utilizando **Regresión Logística** bajo cuatro estrategias para abordar el fuerte desequilibrio de clases:
1.  **Baseline:** Sin tratamiento.
2.  **Class Weight:** Ponderación de costos en la función de pérdida.
3.  **SMOTE:** Sobremuestreo sintético.
4.  **Random UnderSampling (RUS):** Submuestreo aleatorio.

#### 3. Resultados y Conclusión Ética
El análisis reveló una tensión crítica entre la métrica global y la utilidad real:
- El **Modelo Baseline** obtuvo el mejor *F1-Score* global (0.758), pero falló éticamente al ignorar a los pacientes de larga estancia (**Recall del 47%** en la clase "Largo").
- Las estrategias de **Class Weight** y **SMOTE** sacrificaron levemente la precisión global para **elevar la detección de estancias largas al 84%**.

**Decisión Final:** Desde una perspectiva de gestión hospitalaria responsable, se prioriza el modelo con **Class Weight**. Es preferible sobre-estimar la ocupación (falsos positivos) a no prever la falta de camas para pacientes críticos (falsos negativos).

### Informe Académico

El artículo completo que resume la metodología, el análisis detallado y las conclusiones de este estudio se encuentra disponible en el siguiente enlace:
👉 [**Informe Final (PDF)**](articulo/informe_final_Thomas_GIRAULT.pdf)

---

---

Este proyecto sienta las bases para una modelización predictiva robusta en la gestión hospitalaria, combinando rigor estadístico y visión clínica para mejorar la atención al paciente y la planificación de recursos.