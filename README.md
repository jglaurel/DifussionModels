# Evaluación de Redes Neuronales para HAR en Condiciones de Vida Libre (Dataset HARTH) 🏃‍♂️📊

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-EE4C2C.svg)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-1.3+-F7931E.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

Este repositorio contiene el código fuente, los experimentos y el artículo final del proyecto de la materia Introducción a Deep Learning (Maestría en Data Science, Universidad Católica Boliviana San Pablo).

El objetivo principal es evaluar arquitecturas profundas temporales (CNN 1D, CNN+BiLSTM y CNN+GRU) frente a un baseline clásico de Machine Learning (SVM con 81 características temporales y espaciales) para el Reconocimiento de Actividades Humanas (HAR). Todo el modelado se evalúa bajo un protocolo estricto de validación **Leave-One-Subject-Out (LOSO)** utilizando el dataset HARTH.

## 👥 Integrantes
* **Israel Rosendo Salinas Ramirez**
* **Jose Gustavo Laurel Cossio**
* **Franz Erick Mollericona Patty**
* **Rodrigo R. Mercado Mercado**

---

## 📑 Tabla de Contenidos
1. [Descripción del Proyecto](#descripción-del-proyecto)
2. [Cómo reproducir el proyecto](#cómo-reproducir-el-proyecto)

---

## Descripción del Proyecto
El reconocimiento de actividades en condiciones de "vida libre" presenta desafíos como el desbalance severo de clases y la variabilidad inter-sujeto. En este proyecto:
- Se procesan señales inerciales crudas (acelerómetros a 50Hz en muslo y espalda baja).
- Se implementan funciones de pérdida robustas (Focal Loss) para manejar el desbalance.
- Se demuestra que las redes neuronales híbridas (CNN+RNN) superan a la SVM en la clasificación de actividades dinámicas minoritarias (ej. subir o bajar gradas).

---

## Cómo reproducir el proyecto
**1. Bajar el dataset**
Dado que el dataset que se uso es muy pesado se debe descargar desde la siguiente URL (https://archive.ics.uci.edu/dataset/779/harth) y ponerlo en una carpeta llamada data en formato zip 

**2. Clonar el repositorio**
```bash
git clone [https://github.com/jglaurel/ProyectoRD.git](https://github.com/jglaurel/DifussionModels.git)
```

**3. Abrir el proyecto en Visual Studio Code**
Abre la carpeta del proyecto recién clonada en VS Code.

**4. Extensiones necesarias en VS Code**
Asegúrate de tener instaladas las siguientes extensiones desde la sección de extensiones (`Ctrl+Shift+X`):
* **Dev Containers**
* **Containers Tool** (Remote - Containers)

**5. Instalar y ejecutar Docker**
* Instala Docker Desktop si no lo tienes en tu sistema.
* Inicia Docker Desktop y asegúrate de que el motor (engine) esté en ejecución.

**6. Crear y esperar el contenedor en VS Code**
* Al abrir la carpeta del proyecto, VS Code detectará la configuración y te sugerirá reabrir la carpeta en un contenedor (gracias al archivo `devcontainer.json`).
* Haz clic en **"Reopen in Container"** (Reabrir en contenedor).
* *Nota:* Este proceso puede tardar varios minutos la primera vez, ya que descargará la imagen base (con soporte para PyTorch/GPU) y configurará el entorno. VS Code mostrará el progreso; espera hasta que indique que el contenedor está listo y la terminal integrada esté conectada.

---

## ⚙️ Ejecución de los Experimentos

Este proyecto no sigue un flujo secuencial único, sino que está estructurado en tres scripts de entrenamiento independientes. **Cada script contiene el flujo completo** de inicio a fin (carga de datos, preprocesamiento específico, validación LOSO y evaluación final):

* 📄 `entrenamiento_1.py`: Flujo completo para la configuración experimental 1 (Segmentación base de 3s y etiquetado por moda).
* 📄 `entrenamiento_2.py`: Flujo completo para la configuración experimental 2 (Segmentación de 2s, escalado Min-Max y etiquetado central).
* 📄 `entrenamiento_3.py`: Flujo completo para la configuración experimental 3 (Baseline SVM con extracción de 81 características temporales y de correlación cruzada).

Para reproducir los resultados, simplemente abre el script deseado dentro del entorno del contenedor y ejecútalo. Se recomienda verificar las versiones y dependencias en el entorno (`requirements.txt`) antes de la ejecución para garantizar la reproducibilidad total.