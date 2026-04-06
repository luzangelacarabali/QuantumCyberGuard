# QuantumCyberGuard
QuantumCyberGuard es un sistema de detección de amenazas cibernéticas con IA que combina modelos clásicos de machine learning con simulación cuántica (algoritmo de Grover en Qiskit) para estimar tiempos de ataque por fuerza bruta.
Dataset: Global Cybersecurity Threats 2015-2024 (Kaggle)
Modelos implementados:

Random Forest (clasificación supervisada de anomalías)
LSTM Autoencoder (detección secuencial no supervisada)
Isolation Forest + PCA (detección y visualización no supervisada)
Autoencoder Denso (reconstrucción de anomalías)
Algoritmo de Grover en Qiskit (estimación cuántica de fuerza bruta)

Instalación:
bashpip install qiskit qiskit-aer imbalanced-learn tensorflow scikit-learn pandas matplotlib seaborn
Uso: abre QuantumCyberGuard_mejorado.ipynb en Google Colab, sube el CSV y ejecuta celda a celda de arriba hacia abajo.

Guía paso a paso
Paso 1 — Conseguir los datos. Descarga el dataset desde Kaggle (enlace arriba), sube el archivo Global_Cybersecurity_Threats_2015-2024.csv a tu sesión de Colab con el botón de archivos, o usa la API de Kaggle.
Paso 2 — Instalar dependencias. Descomenta la celda de instalación al inicio del notebook y ejecútala. En Colab ya vienen TensorFlow y scikit-learn; solo necesitas qiskit, qiskit-aer e imbalanced-learn.
Paso 3 — EDA (Sección 2). Ejecuta las celdas de análisis exploratorio. Observa los gráficos y la matriz de correlación; te darán intuición sobre qué variables son más predictivas.
Paso 4 — Preprocesamiento (Sección 3). Se aplica Label Encoding a variables categóricas, se crean dos features nuevas (Risk Score y Normalized Resolution Time) y se genera la variable objetivo IsAnomaly usando percentiles extremos (5% y 95%). No hay valores nulos en este dataset, pero la celda de limpieza los manejaría si apareciesen.
Paso 5 — Random Forest (Sección 4). Se balancea el dataset con SMOTE y se entrena un Random Forest con validación cruzada de 10 folds. Revisa el reporte de clasificación y la gráfica de importancia de features; las pérdidas financieras y el tiempo de resolución suelen ser las más importantes.
Paso 6 — LSTM Autoencoder (Sección 5). Se crean secuencias de longitud 10 para alimentar el modelo recurrente. El autoencoder aprende a reconstruir eventos normales; los que tienen mayor error de reconstrucción se clasifican como anomalías. El umbral se fija en el percentil 95 del error.
Paso 7 — Isolation Forest + PCA (Sección 6). Modelo completamente no supervisado. La contaminación (CONTAMINATION = 0.05) es el parámetro clave: auméntalo si crees que hay más del 5% de anomalías en tu dataset. El PCA proyecta a 2D para visualizar los clusters.
Paso 8 — Autoencoder Denso (Sección 7). Similar al LSTM pero sin estructura secuencial: más rápido de entrenar. Útil para comparar con el LSTM y el Isolation Forest.
Paso 9 — Grover en Qiskit (Sección 8). Se ejecuta Grover con n=6 bits en el simulador Aer (simulación clásica de circuito cuántico). Se mide el tiempo de ejecución real para estimar t_oracle, y luego se extrapola con la fórmula teórica π/4·√N a tamaños reales de llave (hasta 128 bits). Los resultados muestran que para 128 bits, incluso con Grover y suposiciones optimistas de 1µs por llamada al oráculo, el tiempo sigue siendo de cientos de miles de años.
Paso 10 — Resumen (Sección 9). La celda final imprime todas las métricas juntas para facilitar la comparación entre modelos.
