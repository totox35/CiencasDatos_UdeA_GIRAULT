# CiencasDatos_UdeA_GIRAULT

This repository contains my work for the course "Ciencas de Datos" at the University of Antioquia.

## Project: Hospital Length of Stay Prediction

### Context and Motivation

Anticipating the duration of hospital stays is a major challenge for healthcare management, especially for optimizing bed availability and resource allocation. This project aims to predict the number of days a patient will remain hospitalized based on clinical and demographic variables, using real-world hospital data.

### Data Sources

- Main dataset: [Hospital Length of Stay Dataset (Microsoft, Kaggle)](https://www.kaggle.com/datasets/aayushchou/hospital-length-of-stay-dataset-microsoft)
- Variables include: comorbidities (ICD-9), biological indicators (BMI, creatinine, BUN, respiration), gender, number of readmissions, and secondary diagnoses.

### Methodology

- **Variable selection** guided by medical literature and data exploration.
- **Data cleaning** to handle outliers and missing values.
- **Descriptive analysis**: distributions, boxplots, and correlation matrices to understand variable behavior.
- **Principal Component Analysis (PCA)** to reduce dimensionality and identify latent clinical axes.
- **Clustering (K-means)** to reveal patient profiles based on clinical complexity.

### First Results

- **Comorbidities and readmissions** are the main drivers of longer hospital stays. Patients with more diagnoses or frequent readmissions tend to stay longer.
- **Biological variables alone** (BMI, creatinine, BUN, respiration) do not sufficiently explain length of stay; multivariable approaches are necessary.
- **PCA** shows that five principal components explain 88% of the variance, highlighting the multidimensional nature of hospital data (clinical load, renal function, respiration, secondary diagnoses, BMI).
- **K-means clustering** (k=2) identifies two clear patient profiles: short, frequent stays vs. long, complex stays. More clusters do not add interpretability.
- **Outliers** (especially in BUN and respiration) are often clinically relevant and should not be discarded without medical review.

### Next Steps

- Enrich the dataset with additional variables (age, admission type, treatment duration).
- Refine outlier management by combining statistical and clinical expertise.
- Develop and compare supervised predictive models (regression, decision trees, neural networks).
- Evaluate model performance and interpretability for practical hospital use.

---

This project lays the groundwork for robust predictive modeling in hospital management, combining statistical rigor and clinical insight to improve patient care and resource planning.