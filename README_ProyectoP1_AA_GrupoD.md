<div align="center">

# 🎓 Predicción del Rendimiento Académico
### Proyecto del Primer Parcial · Aprendizaje Automático · Grupo D

**Universidad de Guayaquil**  
Facultad de Ciencias Matemáticas y Físicas  
Carrera de Ciencia de Datos e Inteligencia Artificial

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Colab](https://img.shields.io/badge/Google-Colab-F9AB00?logo=googlecolab&logoColor=black)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikitlearn&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-Trabajo_colaborativo-181717?logo=github&logoColor=white)

**De los datos a decisiones educativas más oportunas y responsables.**

[📓 Abrir notebook principal](ProyectoP1_AA_GrupoD.ipynb) · [🚀 Abrir en Google Colab](https://colab.research.google.com/github/caritopuya-ops/ProyectoP1_AA_GrupoD/blob/main/ProyectoP1_AA_GrupoD.ipynb) · [👥 Ver aportes individuales](REPORTES/)

</div>

---

## 📌 Presentación del proyecto

El objetivo de este trabajo es construir y evaluar un **pipeline de aprendizaje automático** que permita analizar el rendimiento académico de estudiantes y responder dos preguntas:

1. **¿Qué calificación final podría obtener un estudiante?** — *Regresión lineal múltiple*.
2. **¿Es probable que el estudiante apruebe o repruebe?** — *Regresión logística*.

El proyecto tiene un enfoque **académico y preventivo**: las predicciones buscan orientar tutorías y apoyos oportunos, **no etiquetar ni sancionar estudiantes**. Los resultados deben interpretarse con sus limitaciones y nunca sustituir las decisiones de docentes y orientadores.

## 🗂️ Datos utilizados

| Característica | Descripción |
|---|---|
| Dataset | **Student Performance / Student Alcohol Consumption** |
| Archivo principal | [`student-mat.csv`](student-mat.csv) |
| Asignatura del conjunto seleccionado | Matemáticas |
| Observaciones | **395 estudiantes** |
| Variables originales | **33 columnas** |
| Variable objetivo numérica | **`G3`**: calificación final (0–20) |
| Variable objetivo binaria | **`aprueba`**: 1 si `G3 ≥ 10`, 0 en caso contrario |
| Fuente | [Kaggle — Student Alcohol Consumption](https://www.kaggle.com/datasets/uciml/student-alcohol-consumption) |

**Nota metodológica:** los datos originales no contienen valores faltantes; para el ejercicio se introduce un 5 % de faltantes aleatorios en `absences` y `studytime`, como solicita la consigna. El archivo original se conserva sin alterar.

## 🔬 Metodología

```text
Datos originales (student-mat.csv)
             │
             ▼
  1. Análisis exploratorio
     Estadísticas · Gráficos · Correlaciones
             │
             ▼
  2. Preprocesamiento
     Faltantes · Duplicados · IQR
     Imputación · One-Hot · Escalado
             │
             ▼
  3. Separación entrenamiento / prueba
             80 % / 20 %
             │
       ┌─────┴─────┐
       ▼           ▼
  4. Regresión   5. Regresión
     lineal         logística
     G3             aprueba
       │           │
       ▼           ▼
  MSE · RMSE · R²  Exactitud · Precisión · Recall
       └─────┬─────┘
             ▼
  6. Interpretación técnica y ética
```

### Modelos y evaluaciones

- **Regresión lineal A:** incluye `G1` y `G2` para comparar el efecto de utilizar las calificaciones previas.
- **Regresión lineal B:** excluye `G1` y `G2` para estudiar la posibilidad de alertas más tempranas.
- **Regresión logística:** clasifica aprobación o reprobación **sin usar `G1`, `G2` ni `G3` como predictores**.
- **Umbrales de clasificación:** comparación de `0.3`, `0.5` y `0.7`, considerando el costo de no detectar estudiantes en riesgo.
- **Análisis complementario:** supuestos de regresión lineal y comparación opcional con **Ridge y Lasso**.

> **Sobre la fuga de datos:** las transformaciones del preprocesamiento deben aprenderse únicamente con el conjunto de entrenamiento, mediante `Pipeline` y `ColumnTransformer`. Además, el uso de `G1` y `G2` debe justificarse por el momento en que esas notas estarían disponibles.

## 👥 Integrantes y responsabilidades

| Integrante | Área de contribución | Evidencia |
|---|---|---|
| **Caroline Yomaira Puya Gómez** | Análisis exploratorio (EDA) | [`REPORTES/`](REPORTES/) |
| **Marvin Alex Galán Martínez** | Limpieza y preprocesamiento | [`REPORTES/`](REPORTES/) |
| **Jeremy Freddy González Baquerizo** | Regresión lineal A/B y métricas | [`REPORTES/`](REPORTES/) |
| **Jeremi Anthony Pincay Ramírez** | Regresión logística y umbrales | [`REPORTES/`](REPORTES/) |
| **Angy Belén Soto Lozano** | Interpretación, conclusiones y ética | [`REPORTES/`](REPORTES/) |
| **Jhon Franklin Mejía Castro** | Supuestos, Ridge/Lasso e integración | [`REPORTES/`](REPORTES/) |

**Paralelo:** CDDEIA-ELNO-4-2 · **Grupo:** D · **Período:** 2026–2027 CII

Cada aporte debe ser revisado y defendido por su autor. El historial de GitHub permite observar los cambios realmente realizados por cada integrante.

## 📁 Estructura del repositorio

```text
ProyectoP1_AA_GrupoD/
├── README.md                       # Presentación y guía del proyecto
├── student-mat.csv                 # Dataset original
├── ProyectoP1_AA_GrupoD.ipynb     # Notebook principal del grupo
├── REPORTES/                       # Aportes individuales documentados
└── presentacion/                   # Material para la defensa, si se publica
```

> Algunas carpetas o aportes pueden incorporarse progresivamente. La versión de entrega será la que esté publicada en la rama principal `main` al finalizar la integración.

## ▶️ Cómo ejecutar el proyecto

### Opción 1 — Google Colab (recomendada para la entrega)

1. Abre el [notebook principal en Colab](https://colab.research.google.com/github/caritopuya-ops/ProyectoP1_AA_GrupoD/blob/main/ProyectoP1_AA_GrupoD.ipynb).
2. Si la ejecución utiliza una ruta local para el CSV, descarga `student-mat.csv` desde este repositorio y súbelo al entorno de Colab, o ajusta la lectura para usar una URL pública del archivo.
3. Selecciona **Entorno de ejecución → Ejecutar todas**.
4. Revisa las métricas, visualizaciones e interpretaciones antes de presentar resultados.

### Opción 2 — JupyterLab

```powershell
git clone https://github.com/caritopuya-ops/ProyectoP1_AA_GrupoD.git
cd ProyectoP1_AA_GrupoD
```

Abre `ProyectoP1_AA_GrupoD.ipynb` en JupyterLab y ejecuta todas las celdas. Utiliza un entorno Python con `numpy`, `pandas`, `matplotlib`, `seaborn`, `scipy`, `scikit-learn` y `statsmodels`.

> Los notebooks de `REPORTES/` son contribuciones individuales. Según el directorio desde el que se ejecuten, puede ser necesario usar `../student-mat.csv` o colocar temporalmente una copia local del CSV junto al notebook. **No se debe duplicar el CSV dentro del repositorio.**

## 🔀 Colaboración y trazabilidad

El grupo trabaja en el repositorio público y registra cambios con commits individuales. Antes de modificar archivos compartidos, cada integrante debe sincronizar su copia con la rama `main`.

```powershell
git pull origin main
# Revisar y modificar solo la sección asignada
git add REPORTES/NOMBRE_DEL_APORTE.ipynb
git commit -m "Describir el aporte real realizado"
git pull --rebase origin main
git push origin main
```

- Los commits deben corresponder a **contribuciones reales**, realizadas desde la cuenta de cada estudiante.
- No utilizar `git push --force` sobre `main`.
- Verificar las evidencias en el [historial de commits](https://github.com/caritopuya-ops/ProyectoP1_AA_GrupoD/commits/main).
- Si aparece un conflicto de Git, resolverlo antes de continuar.

## 🧭 Estado de la entrega

| Componente | Qué se verificará |
|---|---|
| EDA | Distribuciones, correlaciones y tres hallazgos interpretados |
| Preprocesamiento | Imputación, IQR, codificación y escalado dentro de un pipeline |
| Regresión lineal | Modelos A y B, MSE/RMSE/R², cálculo manual y cinco supuestos |
| Regresión logística | Métricas, tres umbrales y elección razonada |
| Ética | Limitaciones, sesgos potenciales y uso responsable |
| Colaboración | Commits verificables de los seis integrantes |
| Defensa | Presentación y explicación del trabajo por todo el grupo |

**Fecha de entrega:** domingo **29 de noviembre de 2026, 18:00** (según el aula virtual).  
**Importante:** el enlace del repositorio debe ser público y accesible para el docente.

## ⚖️ Uso responsable de inteligencia artificial

Para apoyar la organización, la revisión y la documentación del proyecto se utilizó asistencia de **ChatGPT**. Los integrantes deben verificar el código, reproducir los resultados, escribir sus interpretaciones con sus propias palabras y declarar en el notebook final el uso concreto de herramientas de IA, de acuerdo con la consigna docente. La autoría de los commits debe reflejar el trabajo realmente realizado por cada estudiante.

## 📚 Referencias

- Cortez, P., & Silva, A. (2008). *Using data mining to predict secondary school student performance*. Proceedings of the 5th Future Business Technology Conference (FUBUTEC 2008), 5–12.
- UCI Machine Learning Repository. *Student Performance*. https://archive.ics.uci.edu/dataset/320/student+performance
- scikit-learn developers. (s. f.). *User guide*. https://scikit-learn.org/stable/user_guide.html

---

<div align="center">

**Grupo D · Aprendizaje Automático · Universidad de Guayaquil**  
*Aprender de los datos para acompañar mejor a los estudiantes.*

</div>
