# Predicción del Rendimiento Atlético: Maratón de Boston 2015

## 📋 Descripción General

Este proyecto aplica la metodología **KDD (Knowledge Discovery in Databases)** en extenso para modelar y predecir el tiempo oficial de llegada de los corredores en el **Maratón de Boston 2015**. 

A través de un enfoque de **Sports Analytics**, se transiciona de un análisis descriptivo a un modelo de regresión robusto capaz de mitigar problemas de multicolinealidad estructural.

---

## 🎯 Objetivo del Proyecto

Construir un sistema de analítica predictiva que estime el tiempo final de un corredor basándose en:
- Variables demográficas
- Métricas biomecánicas capturadas en puntos de control intermedios (5K, 10K, Half, 30K)

---

## 🛠️ Stack Tecnológico

**Lenguaje:** R

**Librerías principales:**
- **tidyverse** - Manipulación de datos y visualización con ggplot2
- **factoextra** - Visualización avanzada de Componentes Principales (PCA)
- **janitor** - Limpieza de metadatos y nombres de variables
- **lubridate** - Gestión de formatos temporales

---

## 📊 Metodología KDD (Fase 1)

### 1. Gestión de Datos y ETL

Se procesaron **26,391 registros** tras una limpieza exhaustiva. Los datos crudos en formato de texto (HH:MM:SS) fueron transformados a un espacio numérico continuo (minutos decimales) para permitir la optimización matemática por mínimos cuadrados.

### 2. Análisis Exploratorio (EDA) Profundo

#### Análisis Univariable
- Identificación de una distribución leptocúrtica en los tiempos de llegada
- Población predominantemente de entre 35-50 años

#### Diagnóstico de Outliers
- Detección de "outliers naturales" que representan agotamiento físico extremo tras el kilómetro 30
- Retenidos para mejorar la capacidad del modelo en escenarios de bajo rendimiento

#### Análisis de Multicolinealidad (PCA)
- El PC1 explica el **98.33% de la varianza**
- Revela redundancia extrema entre los tiempos de paso que inestabiliza los modelos lineales tradicionales

### 3. Torneo Algorítmico

Comparación de dos arquitecturas bajo esquema de validación **Hold-out (70/30)**:

| Modelo | Descripción | MAE (Test) | R² | Estado |
|--------|-------------|------------|-----|--------|
| **Baseline (Crudo)** | Todas las variables (Multicolinealidad) | 3.63 min | 97.6% | ❌ Coeficientes Ilógicos |
| **Optimizado (FE)** | Ingeniería de Características (ritmo_30k) | 4.69 min | 96.9% | ✅ **Ganador (Robusto)** |

**Nota Técnica:** El modelo optimizado restauró la lógica de dominio. Aunque el error absoluto subió ligeramente, se eliminó la significancia espuria de la edad y se modeló correctamente la fatiga acumulada.

---

## 🚀 Instalación y Uso

1. Clonar el repositorio
2. Asegurarse de tener instalado **R** y las librerías mencionadas
3. Ejecutar el notebook `Final_Project_Marathon_P1.ipynb` en VS Code o RStudio

---

## 📁 Estructura del Proyecto

```
.
├── Final_Project_Marathon_P1.ipynb    # Notebook principal con el análisis
├── marathon_results_2015.csv          # Dataset de resultados de Boston 2015
└── README.MD                          # Este archivo
```

---

## 👤 Autor

**Axel Tapia**
- Estudiante de Ingeniería en Ciencias de la Computación
- Benemérita Universidad Autónoma de Puebla (BUAP) s