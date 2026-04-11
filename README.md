# QuantumCyberGuard

**QuantumCyberGuard** es un sistema híbrido de detección de amenazas cibernéticas que combina técnicas clásicas de *Machine Learning* con simulación de computación cuántica para el análisis de anomalías y la evaluación de ataques por fuerza bruta.

El proyecto integra modelos supervisados y no supervisados junto con el algoritmo de Grover implementado en Qiskit, permitiendo tanto la detección predictiva como el análisis teórico de seguridad frente a escenarios cuánticos.

---

## Estructura del Repositorio

```
QuantumCyberGuard/
│
├── datos/
│   └── Amenazas_de_ciberseguridad_globales_2015-2024.csv
│
├── cuadernos/
│   ├── modelos/
│   │   ├── autoencoder_dense.keras
│   │   ├── aislamiento_bosque.joblib
│   │   ├── escalador_ae.joblib
│   │   └── escalador_iforest.joblib
│   │
│   ├── QuantumCyberGuard_mejorado.ipynb
│   ├── eda_overview.png
│   ├── análisis_grover.png
│   ├── grover_success_prob.png
│   ├── iforest_pca.png
│   ├── lstm_metrics.png
│   ├── rf_feature_importance.png
│   └── rf_metrics.png
│
└── 
```

---

## Descripción General

La ciberseguridad moderna requiere no solo detectar anomalías con precisión, sino también anticipar amenazas emergentes. Este proyecto aborda ambos aspectos:

- Detección de eventos anómalos en datos de ciberseguridad
- Comparación entre enfoques supervisados y no supervisados
- Simulación de ataques de fuerza bruta con algoritmos cuánticos
- Evaluación de la viabilidad real de ataques cuánticos

---

## Dataset

| Campo | Detalle |
|-------|---------|
| **Nombre** | Amenazas de Ciberseguridad Globales 2015–2024 |
| **Archivo** | `datos/Amenazas_de_ciberseguridad_globales_2015-2024.csv` |
| **Fuente** | Kaggle |

El dataset incluye: tipos de ataque, industrias objetivo, vulnerabilidades, pérdidas financieras y tiempos de resolución.

---

## Arquitectura del Sistema

El sistema está compuesto por cuatro capas principales:

### 1. Capa de Procesamiento de Datos
- Limpieza y codificación
- Ingeniería de características
- Generación de la variable objetivo (`IsAnomaly`)

### 2. Capa de Modelado
- **Random Forest** — supervisado
- **Isolation Forest** — no supervisado
- **Autoencoder Denso** — guardado en `modelos/autoencoder_dense.keras`
- **LSTM Autoencoder** — detección de anomalías en secuencias temporales

### 3. Capa de Visualización
Los resultados se guardan como imágenes en `cuadernos/`:

| Archivo | Contenido |
|---------|-----------|
| `eda_overview.png` | Análisis exploratorio de datos |
| `rf_metrics.png` | Métricas del Random Forest |
| `rf_feature_importance.png` | Importancia de variables |
| `iforest_pca.png` | Proyección PCA del Isolation Forest |
| `lstm_metrics.png` | Métricas del LSTM Autoencoder |
| `análisis_grover.png` | Análisis del algoritmo de Grover |
| `grover_success_prob.png` | Probabilidad de éxito cuántico |

### 4. Capa de Simulación Cuántica
- Algoritmo de Grover implementado en Qiskit
- Estimación de tiempos de ataque
- Análisis de complejidad cuántica

---

## Modelos Implementados

### Aprendizaje Supervisado — Random Forest
- Manejo de desbalance de clases con SMOTE
- Validación cruzada (10 folds)
- Análisis de importancia de variables
- Escalador guardado en: `modelos/escalador_iforest.joblib`

### Aprendizaje No Supervisado

**Isolation Forest**
- Detección de outliers sin etiquetas
- Visualización en 2D mediante PCA
- Modelo guardado en: `modelos/aislamiento_bosque.joblib`

**Autoencoder Denso**
- Alternativa eficiente computacionalmente
- Adecuado para datos no secuenciales
- Modelo guardado en: `modelos/autoencoder_dense.keras`
- Escalador guardado en: `modelos/escalador_ae.joblib`

**LSTM Autoencoder**
- Detección de anomalías en secuencias
- Captura dependencias temporales
- Umbral basado en percentiles del error de reconstrucción

---

## Componente Cuántico — Algoritmo de Grover (Qiskit)

- Simulación de búsqueda en espacios de claves usando Qiskit Aer
- Estimación del tiempo de ataque mediante:

```
T ≈ (π/4) · √N
```

- Extrapolación a tamaños de clave reales (128 bits)

**Conclusión clave:** Incluso bajo supuestos optimistas, los ataques de fuerza bruta con algoritmos cuánticos siguen siendo computacionalmente inviables para claves de gran tamaño.

---

## Instalación

```bash
pip install qiskit qiskit-aer imbalanced-learn tensorflow scikit-learn pandas matplotlib seaborn
```

---

## Uso

1. Abrir el notebook principal:
   ```
   cuadernos/QuantumCyberGuard_mejorado.ipynb
   ```

2. Ejecutar en Google Colab o Jupyter Notebook

3. Asegurarse de que el dataset esté en:
   ```
   datos/Amenazas_de_ciberseguridad_globales_2015-2024.csv
   ```

4. Ejecutar todas las celdas en orden

---

## Flujo de Trabajo

```
Carga de datos
     ↓
Análisis exploratorio (EDA)
     ↓
Preprocesamiento e ingeniería de variables
     ↓
Entrenamiento de modelos (RF · Isolation Forest · Autoencoders)
     ↓
Evaluación y comparación de métricas
     ↓
Simulación cuántica (Grover · Qiskit)
     ↓
Consolidación de resultados
```

---

## Resultados

- **Random Forest** proporciona una base sólida para clasificación supervisada
- **LSTM Autoencoder** captura patrones temporales complejos
- **Isolation Forest** es eficiente para detección no supervisada sin etiquetas
- **Simulación cuántica** evidencia los límites prácticos del algoritmo de Grover

---

## Tecnologías Utilizadas

| Categoría | Herramientas |
|-----------|-------------|
| Lenguaje | Python |
| ML clásico | Scikit-learn, imbalanced-learn |
| Deep Learning | TensorFlow / Keras |
| Computación cuántica | Qiskit, Qiskit Aer |
| Datos | Pandas, NumPy |
| Visualización | Matplotlib, Seaborn |

---

## Limitaciones

- La simulación cuántica se realiza sobre hardware clásico (Qiskit Aer)
- El dataset no es en tiempo real
- El desempeño del LSTM depende de la construcción de secuencias temporales

---

## Trabajo Futuro

- Integración con streaming de datos en tiempo real (Kafka)
- Despliegue como API o dashboard interactivo
- Uso de hardware cuántico real
- Modelos basados en Transformers
- Implementación de MLOps

---

## Autora

**Luz Angela Carabali Mulato e Isabella Perez Caviedes**  
Estudiante de Ingeniería de Datos e IA  
Proyecto desarrollado como iniciativa en Inteligencia Artificial, Ciberseguridad y Computación Cuántica.

---

## Licencia

Este proyecto está destinado a fines académicos y de investigación.
