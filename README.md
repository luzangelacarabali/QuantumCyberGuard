# QuantumCyberGuard

**QuantumCyberGuard** es un sistema híbrido de detección de amenazas cibernéticas que combina técnicas clásicas de *Machine Learning* con simulación de computación cuántica para el análisis de anomalías y la evaluación de ataques por fuerza bruta.

El proyecto integra modelos supervisados y no supervisados junto con el algoritmo de Grover implementado en Qiskit, permitiendo tanto la detección predictiva como el análisis teórico de seguridad frente a escenarios cuánticos.

---

## Descripción General

La ciberseguridad moderna requiere no solo detectar anomalías con precisión, sino también anticipar amenazas emergentes. Este proyecto aborda ambos aspectos:

* Detección de eventos anómalos en datos de ciberseguridad
* Comparación entre enfoques supervisados y no supervisados
* Simulación de ataques de fuerza bruta con algoritmos cuánticos
* Evaluación de la viabilidad real de ataques cuánticos

---

## Dataset

* **Nombre:** Global Cybersecurity Threats (2015–2024)
* **Fuente:** Kaggle
* **Descripción:**
  Dataset estructurado que incluye:

  * Tipos de ataque
  * Industrias objetivo
  * Vulnerabilidades
  * Pérdidas financieras
  * Tiempos de resolución

---

## Arquitectura del Sistema

El sistema está compuesto por cuatro capas principales:

1. **Capa de Procesamiento de Datos**

   * Limpieza y codificación
   * Ingeniería de características
   * Generación de la variable objetivo (`IsAnomaly`)

2. **Capa de Modelado**

   * Random Forest (supervisado)
   * Isolation Forest (no supervisado)
   * Autoencoders (denso y LSTM)

3. **Capa de Visualización**

   * Proyección con PCA
   * Importancia de variables
   * Análisis de error de reconstrucción

4. **Capa de Simulación Cuántica**

   * Algoritmo de Grover (Qiskit)
   * Estimación de tiempos de ataque
   * Análisis de complejidad

---

## Modelos Implementados

### Aprendizaje Supervisado

**Random Forest**

* Manejo de desbalance de clases con SMOTE
* Validación cruzada (10 folds)
* Análisis de importancia de variables

---

### Aprendizaje No Supervisado

**LSTM Autoencoder**

* Detección de anomalías en secuencias
* Captura dependencias temporales
* Umbral basado en percentiles del error

**Autoencoder Denso**

* Alternativa más eficiente computacionalmente
* Adecuado para datos no secuenciales

**Isolation Forest + PCA**

* Detección de outliers sin etiquetas
* Visualización en 2D mediante PCA

---

## Componente Cuántico

**Algoritmo de Grover (Qiskit)**

* Simulación de búsqueda en espacios de claves
* Uso de Qiskit Aer (simulación clásica)
* Estimación del tiempo de ataque mediante:

[
T \approx \frac{\pi}{4} \cdot \sqrt{N}
]

* Extrapolación a tamaños de clave reales (por ejemplo, 128 bits)

**Conclusión clave:**
Incluso bajo supuestos optimistas, los ataques de fuerza bruta con algoritmos cuánticos siguen siendo computacionalmente inviables para claves de gran tamaño.

---

## Instalación

```bash
pip install qiskit qiskit-aer imbalanced-learn tensorflow scikit-learn pandas matplotlib seaborn
```

---

## Uso

1. Abrir el notebook:

   ```
   QuantumCyberGuard_mejorado.ipynb
   ```

2. Ejecutar en:

   * Google Colab
   * Jupyter Notebook

3. Cargar el dataset:

   ```
   Global_Cybersecurity_Threats_2015-2024.csv
   ```

4. Ejecutar todas las celdas en orden

---

## Flujo de Trabajo

1. Carga de datos
2. Análisis exploratorio (EDA)
3. Preprocesamiento e ingeniería de variables
4. Entrenamiento de modelos
5. Evaluación y comparación
6. Simulación cuántica (Grover)
7. Consolidación de métricas

---

## Resultados

* Random Forest proporciona una base sólida para clasificación
* LSTM Autoencoder captura patrones temporales complejos
* Isolation Forest es eficiente para detección no supervisada
* La simulación cuántica evidencia límites prácticos del algoritmo de Grover

---

## Tecnologías Utilizadas

* Python
* Scikit-learn
* TensorFlow / Keras
* Qiskit
* Pandas / NumPy
* Matplotlib / Seaborn

---

## Limitaciones

* La simulación cuántica se realiza sobre hardware clásico
* El dataset no es en tiempo real
* El desempeño del LSTM depende de la construcción de secuencias

---

## Trabajo Futuro

* Integración con streaming de datos (Kafka)
* Despliegue como API o dashboard
* Uso de hardware cuántico real
* Modelos basados en Transformers
* Implementación de MLOps

---

## Estructura del Repositorio

```
QuantumCyberGuard/
│
├── QuantumCyberGuard_mejorado.ipynb
├── data/
│   └── dataset.csv
├── src/
│   ├── preprocessing.py
│   ├── models.py
│   └── quantum.py
├── results/
├── README.md
└── requirements.txt
```

---

## Autor

Proyecto desarrollado como iniciativa avanzada en Inteligencia Artificial, Ciberseguridad y Computación Cuántica.

---

## Licencia

Este proyecto está destinado a fines académicos y de investigación.

---


