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
└── 
```

---

## Descripción General
La ciberseguridad moderna requiere no solo detectar anomalías con precisión, sino también anticipar amenazas emergentes. Los ciberataques generan pérdidas superiores a 6 trillones de dólares anuales, y la llegada de la computación cuántica representa un riesgo adicional: algoritmos como RSA y Elliptic Curve Cryptography métodos de cifrado asimétrico ampliamente utilizados para proteger comunicaciones mediante claves públicas y privadas podrían ser vulnerados en segundos.

Este proyecto aborda ambos frentes:

- Detección de eventos anómalos en datos de ciberseguridad
- Comparación entre enfoques supervisados y no supervisados
- Simulación de ataques de fuerza bruta con el algoritmo de Grover's Algorithm
- Evaluación de la viabilidad real de ataques cuánticos

---

## Dataset

| Campo | Detalle |
|-------|---------|
| **Nombre** | Amenazas de Ciberseguridad Globales 2015–2024 |
| **Archivo** | `datos/Amenazas_de_ciberseguridad_globales_2015-2024.csv` |
| **Fuente** | Kaggle — Soundankar, A. (2025) |

El dataset incluye: tipos de ataque, industrias objetivo, vulnerabilidades, pérdidas financieras y tiempos de resolución.

---
## Metodología 

```
Carga de datos
     ↓
Análisis exploratorio (EDA) - limpieza, análisis descriptivo y visualización
     ↓
Preprocesamiento e ingeniería de variables
     ↓
Entrenamiento de modelos - (algoritmos supervisados (Random Forest, RNN) y no supervisados (Autoencoders, Isolation Forest))
     ↓
Simulación cuántica - (algoritmo de Grover en Qiskit para estimar tiempos de ataque por fuerza bruta)
     ↓
Evaluación y comparación de métricas de  rendimiento (accuracy, precision, recall, F1-score) y comparación clásico vs cuántico
     ↓
Consolidación de resultados
```

----

## Arquitectura del Sistema

El sistema está compuesto por cuatro capas principales:

### 1. Capa de Procesamiento de Datos
- Limpieza y codificación
- Ingeniería de características
- Generación de la variable objetivo (`IsAnomaly`)

### 2. Capa de Modelado
- **Random Forest** — supervisado
- **RNN / LSTM** Autoencoder — detección en secuencias temporales
- **Autoencoder Denso** — guardado en `modelos/autoencoder_dense.keras`
- **Isolation Forest** — no supervisado, sin etiquetas
  
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
- Algoritmo de Grover implementado con Qiskit Aer
- Estimación del tiempo de ataque: `T ≈ (π/4) · √N`

---
## Resultados

###  Mejor modelo: Random Forest

| Modelo | Resultado |
|--------|-----------|
| **Random Forest** | **85% accuracy**  |
| RNN Autoencoder | 71% accuracy |
| Isolation Forest | ~5% anomalías detectadas |

**Random Forest** fue el modelo con mejor desempeño con **85% de precisión**, usando SMOTE para manejo de desbalance y validación cruzada de 10 folds.

El **RNN Autoencoder** alcanzó 71% con margen de mejora en recall y precisión. El **Isolation Forest** complementó los modelos supervisados detectando ~5% de registros anómalos sin etiquetas.

###  Simulación Cuántica — Grover

| Tamaño de clave | Tiempo clásico | Tiempo cuántico (estimado) |
|----------------|---------------|---------------------------|
| 64 bits | Millones de años | Minutos |
| 128 bits | Computacionalmente inviable | Inviable aún con ventaja cuántica |

> **Conclusión:** Las claves de 128 bits siguen siendo seguras incluso con Grover, pero esto valida la migración preventiva hacia criptografía post-cuántica (PQC).

### Tendencia en ataques
- Incremento anual del **30% en ransomware** desde 2020
---
## Conclusiones

- La combinación de modelos supervisados y no supervisados mejora la robustez en detección de ciberataques.
- El análisis de Grover evidencia la necesidad de migrar hacia criptografía post-cuántica.
- QuantumCyberGuard propone un enfoque integral: **detección inteligente + simulación cuántica + transición a PQC**.


## Instalación

```bash
pip install qiskit qiskit-aer imbalanced-learn tensorflow scikit-learn pandas matplotlib seaborn
```

---

## Uso

1. Abrir el notebook: `cuadernos/QuantumCyberGuard_mejorado.ipynb`
2. Ejecutar en Google Colab o Jupyter Notebook
3. Dataset en: `datos/Amenazas_de_ciberseguridad_globales_2015-2024.csv`
4. Ejecutar todas las celdas en orden


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

- Integración con streaming en tiempo real (Kafka)
- Despliegue como API o dashboard
- Uso de hardware cuántico real
- Implementación de criptografía post-cuántica (PQC)
- Modelos basados en Transformers y MLOps

---
## Autoras

**Luz Angela Carabali Mulato e Isabella Perez Caviedes**  
Estudiantes de Ingeniería de Datos e IA  
Proyecto desarrollado como iniciativa en Inteligencia Artificial, Ciberseguridad y Computación Cuántica.

---

## Referencias

- Soundankar, A. (2025). *Global Cybersecurity Threats (2015–2024)*. Kaggle.
- Goodfellow, I., Bengio, Y., & Courville, A. (2016). *Deep Learning*. MIT Press.
- Nielsen, M. A., & Chuang, I. L. (2010). *Quantum Computation and Quantum Information*. Cambridge University Press.
- Bernstein, D. J., & Lange, T. (2017). Post-quantum cryptography. *Nature*, 549, 188–194.
- IBM Quantum. (2024). *Qiskit Documentation*. https://qiskit.org
- ENISA. (2022). *Post-Quantum Cryptography: Current state and quantum mitigation strategies*.

---

## Licencia

Este proyecto está destinado a fines académicos y de investigación.




