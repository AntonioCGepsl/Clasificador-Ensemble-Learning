# Clasificador (Ensemble Learning)

## Descripción

Esta aplicación permite la **clasificación automática de sonidos respiratorios** mediante un sistema de **Ensemble Learning** formado por cinco modelos de redes neuronales UJANet previamente entrenados.

El programa analiza automáticamente una colección de **20 archivos de audio**, compuesta por:

- **10 sonidos respiratorios normales**
- **10 sonidos respiratorios con sibilancias (Wheeze)**

Cada audio es preprocesado mediante la extracción de coeficientes **MFCC**, clasificado por los cinco modelos del ensemble y finalmente etiquetado como:

- **Normal**
- **Wheeze**

Una vez finalizado el proceso, la aplicación genera una interfaz gráfica con las principales métricas de clasificación.

---

# Características

- Clasificación automática mediante Ensemble Learning.
- Carga simultánea de cinco modelos UJANet.
- Extracción automática de características MFCC.
- Clasificación de 20 archivos WAV.
- Cálculo de métricas de evaluación.
- Interfaz gráfica de resultados.

---

# Requisitos del sistema

## Sistema operativo

Compatible con:

- Windows 10/11
- Linux
- macOS

---

## Lenguaje de programación: Python

Se recomienda utilizar la siguiente versión:

- Python 3.13 o superior

---

# Librerías necesarias

La aplicación utiliza las siguientes librerías:

| Librería | Uso |
|----------|-----|
| tensorflow | Inferencia de los modelos UJANet |
| numpy | Procesamiento numérico |
| librosa | Carga y extracción de MFCC |
| matplotlib | Visualización de resultados |
| scikit-learn | Métricas de clasificación |
| tkinter | Interfaz gráfica |
| pillow | Carga de logotipos |
| itertools | Representación de la matriz de confusión |

---

# Estructura del proyecto

```
Proyecto/

│
├── Clasificador.py
│
├── Audios/
│   ├── N01.wav
│   ├── ...
│   ├── N10.wav
│   ├── W01.wav
│   ├── ...
│   └── W10.wav
│
├── Modelo/
│   ├── ujanet_fold_1.keras
│   ├── ujanet_fold_2.keras
│   ├── ujanet_fold_3.keras
│   ├── ujanet_fold_4.keras
│   └── ujanet_fold_5.keras
│
├── Media/
│   ├── logo epsl.png
│   └── logo uja.png
│
└── README.md
```

---

# Archivos necesarios

## Modelos entrenados

La carpeta **Modelo** debe contener obligatoriamente los cinco modelos entrenados del ensemble:

```
Modelo/

ujanet_fold_1.keras
ujanet_fold_2.keras
ujanet_fold_3.keras
ujanet_fold_4.keras
ujanet_fold_5.keras
```

Si alguno de ellos falta, la aplicación no podrá ejecutarse.

---

## Audios

La carpeta **Audios** debe contener exactamente **20 archivos WAV**:

- **10 audios normales**, cuyo nombre debe comenzar por **N**.
- **10 audios con sibilancias**, cuyo nombre debe comenzar por **W**.

Ejemplo:

```
Audios/

N01.wav
N02.wav
...
N10.wav

W01.wav
W02.wav
...
W10.wav
```

**Importante:** los nombres de los archivos deben comenzar por **N** o **W**, ya que la aplicación utiliza esta convención para asignar la clase verdadera y calcular las métricas de clasificación.

---

##  Imágenes (OPCIONAL)

```
Media/

logo epsl.png
logo uja.png
```

Estos archivos son opcionales y únicamente se utilizan para mostrar los logotipos en la interfaz.

---

# Ejecución

Desde la carpeta del proyecto ejecutar:

```bash
python Clasificador.py
```

La aplicación localizará automáticamente:

- Los cinco modelos entrenados.
- Los veinte audios.
- Las dos imágenes.

---

# Flujo de funcionamiento

## 1. Carga del ensemble

Se cargan los cinco modelos UJANet almacenados en la carpeta **Modelo**.

---

## 2. Preprocesamiento

Cada archivo WAV es preprocesado para adaptarlo al formato de entrada requerido por el clasificador:

- Reescalado a 22.050 Hz.
- Ajustado a una duración de 5 segundos.
- Convertido en una representación MFCC de 40 coeficientes.
- Normalizado.
- Adaptado al tamaño de entrada de la red neuronal.

---

## 3. Clasificación

Cada audio se evalúa con los cinco modelos.

Las probabilidades obtenidas se combinan mediante la media aritmética para obtener la predicción final del ensemble.

---

## 4. Evaluación

Tras clasificar los 20 audios se calculan automáticamente:

- Accuracy.
- Precision.
- Recall.
- F1-score.
- Sensibilidad.
- Especificidad.
- Matriz de confusión.

---

## 5. Resultados

Tras finalizar la clasificación, la aplicación muestra una interfaz gráfica con:

- Tiempo total de clasificación y latencia media por archivo.
- Reporte de clasificación.
- Matriz de confusión.
- Métricas de evaluación (sensibilidad, especificidad, precisión, recall y F1-score).
- Distribución de la confianza del ensemble.

---

# Autor

**Antonio Carrasco Garrido**

Escuela Politécnica Superior de Linares

*Universidad de Jaén*

Año 2026
