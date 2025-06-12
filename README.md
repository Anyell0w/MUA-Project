# 🎓 Algoritmos de Optimización Multi-Objetivo para Clasificación de Rendimiento Estudiantil


> **Aplicación de NSGA-II, MOPSO y MOEA/D en Minería de Datos Educacionales**

**Autor:** Angello Marcelo Zamora Valencia  
**Institución:** Facultad de Ingeniería Estadística e Informática, Universidad Nacional del Altiplano  

---

## 📋 Descripción

Este repositorio contiene la implementación completa de la investigación sobre **algoritmos de optimización multi-objetivo** aplicados a la clasificación automática de estudiantes en perfiles académicos. El estudio compara tres algoritmos evolutivos de vanguardia para identificar patrones en el rendimiento estudiantil y proporcionar insights para intervenciones pedagógicas personalizadas.

### 🎯 Objetivos de la Investigación

- **Optimización simultánea** de múltiples objetivos: precisión, interpretabilidad, eficiencia y equidad
- **Identificación automática** de perfiles estudiantiles basados en hábitos de estudio
- **Comparación exhaustiva** de algoritmos MOO en contextos educacionales
- **Generación de frentes Pareto** para decisiones balanceadas en sistemas de apoyo académico

## 🚀 Resultados Principales

### 📊 Rendimiento de Algoritmos

| Algoritmo | Precisión | Características | Tiempo (s) | Hipervolumen |
|-----------|-----------|----------------|------------|--------------|
| **MOEA/D** | **81.6% ± 2.1%** | 7.8 | 45.1 | **0.863** |
| **NSGA-II** | 79.2% ± 2.8% | 8.4 | 38.7 | 0.847 | 
| **MOPSO** | 76.8% ± 3.4% | 11.2 | 24.3 | 0.781 |

### 👥 Perfiles Estudiantiles Identificados

| Perfil | Población | Horas Estudio | Redes Sociales | Puntuación |
|--------|-----------|---------------|----------------|------------|
| **Alto Rendimiento** | 22% (220) | 6.8 ± 1.2h | 1.2 ± 0.8h | 87.4 ± 4.2 |
| **Equilibrado** | 58% (580) | 4.5 ± 1.8h | 2.8 ± 1.4h | 76.2 ± 8.6 |
| **En Riesgo** | 18% (180) | 2.1 ± 1.5h | 5.4 ± 2.1h | 58.7 ± 12.3 |
| **Social** | 12% (120) | 3.2 ± 1.9h | 4.1 ± 1.7h | 69.8 ± 9.4 |



## 🛠️ Instalación y Uso

### Requisitos Previos

```bash
Python 3.8+
pip (gestor de paquetes Python)
```

### 1. Clonar el Repositorio

```bash
git clone [https://github.com/tu-usuario/multi-objective-student-classification.git](https://github.com/Anyell0w/MUA-Project.git)
cd multi-obj-investigacion
```

### 2. Instalar Dependencias

```bash
pip install -r requirements.txt
```

### 3. Ejecutar el Análisis Completo

```bash
# Generar todos los resultados del paper
python resultados.py
```

### 4. Resultados Generados

El script genera automáticamente:
- ✅ **Tabla 1:** Comparación de algoritmos MOO
- ✅ **Tabla 2:** Estadísticas de perfiles estudiantiles  
- ✅ **Figura 1:** Frente de Pareto (precisión vs interpretabilidad)
- ✅ **Figura 2:** Distribución de perfiles estudiantiles

## 📊 Dataset

El dataset `student_habits_performance.csv` contiene **1000 registros** de estudiantes con **16 variables**:

### Variables Principales
- **Académicas:** `exam_score`, `attendance_percentage`, `study_hours_per_day`
- **Comportamentales:** `social_media_hours`, `netflix_hours`, `sleep_hours`
- **Demográficas:** `age`, `gender`, `parental_education_level`
- **Bienestar:** `mental_health_rating`, `diet_quality`, `exercise_frequency`

### Uso del Dataset
```python
import pandas as pd

# Cargar datos
data = pd.read_csv('data/student_habits_performance.csv')
print(f"Estudiantes: {len(data)}, Variables: {len(data.columns)}")

# Ver primeras filas
print(data.head())
```

## 🔬 Metodología

### Algoritmos Implementados

1. **NSGA-II (Non-dominated Sorting Genetic Algorithm II)**
   - Clasificación no dominada rápida O(MN²)
   - Preservación de diversidad mediante distancia de hacinamiento
   - Mejor balance interpretabilidad-rendimiento

2. **MOPSO (Multi-Objective Particle Swarm Optimization)**
   - Convergencia más rápida (40% vs NSGA-II)
   - Archivo externo para soluciones no dominadas
   - Óptimo para aplicaciones tiempo real

3. **MOEA/D (Multi-Objective Evolutionary Algorithm based on Decomposition)**
   - Descomposición en subproblemas escalares
   - Mejor precisión: 81.6% ± 2.1%
   - Excelente para problemas de muchos objetivos

### Objetivos Optimizados

- **f₁:** Minimizar tasa de error de clasificación
- **f₂:** Minimizar número de características (interpretabilidad)
- **f₃:** Minimizar complejidad computacional
- **f₄:** Minimizar violaciones de equidad entre grupos

## 📈 Reproducibilidad

### Ejecución Paso a Paso

```python
from src.generar_resultados_paper import MultiObjectiveStudentAnalyzer

# Crear analizador
analyzer = MultiObjectiveStudentAnalyzer('data/student_habits_performance.csv')

# Generar resultados individuales
table1 = analyzer.generate_table1_results()      # Comparación algoritmos
table2 = analyzer.generate_table2_results()      # Perfiles estudiantiles
fig1 = analyzer.generate_figure1_pareto_front()  # Frente Pareto
fig2 = analyzer.generate_figure2_profile_distribution()  # Distribución

# O generar todo de una vez
results = analyzer.generate_all_results()
```

### Configuración de Algoritmos

```python
# NSGA-II
poblacion = 100
generaciones = 200
prob_cruzamiento = 0.9
prob_mutacion = 1/n_variables

# MOPSO  
particulas = 100
iteraciones = 200
archivo_externo = 100

# MOEA/D
subproblemas = 100
vecindario = 20
```



### Paper Completo

El artículo científico completo está disponible en:
- **PDF:** [`/paper_latex.pdf`](./paper_latex.pdf)

## 🔍 Análisis de Resultados

### Frente de Pareto

<img src="results/figura1_pareto_precision_interpretabilidad.png" alt="Frente de Pareto" width="600">

**Interpretación:** Las soluciones Pareto-óptimas muestran compensaciones claras entre precisión e interpretabilidad. Incrementar precisión del 79% al 85% requiere sacrificar 25% de interpretabilidad.

### Distribución de Perfiles

<img src="results/distribucion_perfiles.png" alt="Distribución de Perfiles" width="600">

**Interpretación:** Los perfiles se separan claramente en el espacio bidimensional horas de estudio vs puntuación, validando la efectividad del clustering.

## 🎯 Aplicaciones Prácticas

### Para Instituciones Educativas
- **Sistemas de alerta temprana** para estudiantes en riesgo
- **Personalización** de estrategias pedagógicas
- **Optimización** de recursos de apoyo académico

### Para Investigadores
- **Metodología robusta** para análisis educacional multi-objetivo
- **Código replicable** para validación de resultados
- **Extensión** a otros contextos educacionales

### Para Desarrolladores
- **Framework completo** para clasificación MOO
- **Implementación** de algoritmos evolutivos
- **Generación** de frentes Pareto interactivos



## 👤 Autor

**Angello Marcelo Zamora Valencia**
- 🎓 Facultad de Ingeniería Estadística e Informática
- 🏛️ Universidad Nacional del Altiplano


## 🙏 Agradecimientos

- Universidad Nacional del Altiplano por el apoyo institucional
- Comunidad de investigación en Minería de Datos Educacionales
- Desarrolladores de las librerías Python utilizadas (scikit-learn, pandas, matplotlib)
