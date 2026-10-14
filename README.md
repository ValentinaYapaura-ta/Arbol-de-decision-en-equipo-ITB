Predicción de Abandono en Estudiantes Terciarios 🎓📊
Instituto Tecnológico Beltrán — Modelo de Aprendizaje Automático con Árboles de Decisión
Este proyecto implementa un modelo de Machine Learning supervisado mediante el algoritmo de Árbol de Decisión (Decision Tree Classifier) basado en el criterio de Entropía. Su objetivo principal es predecir de manera temprana la probabilidad de deserción de estudiantes de carreras terciarias en base a variables socio-demográficas, académicas e institucionales recabadas durante su primer año de cursada.
Requisitos del Sistema
Para ejecutar este script necesitás tener instalado Python 3.8+ junto a las siguientes librerías:
pandas — Para manipulación de estructuras de datos y DataFrames.
scikit-learn — Para el entrenamiento, división y evaluación del modelo de Machine Learning.
math — Módulo nativo de Python para cálculos matemáticos.
Instalación de Dependencias
Podés instalar las dependencias ejecutando en la terminal:

pip install pandas scikit-learn
(O python -m pip install pandas scikit-learn si estás en Windows).

Estructura e Implementación del Código
El script principal (TP_Estudiantes_Grupo.py) está organizado secuencialmente en las siguientes secciones:
Análisis Exploratorio de Datos (EDA) & Entropía Inicial H(S):
Filtrado y conteo exploratorio de variables cuantitativas y cualitativas.
Cálculo programático explícito de la Entropía Inicial del conjunto de datos mediante logaritmos en base 2: 
H(S) = -p_a \log_2(p_a) - p_c \log_2(p_c)
Preprocesamiento y Codificación de Datos:
Conversión de la estructura primaria a un DataFrame de Pandas.
Codificación de variables categóricas nominales (One-Hot Encoding) mediante
pd.get_dummies().
Divisibilidad del conjunto de datos en Entrenamiento (80%) y Prueba (20%) con conservación de proporciones estratificadas (stratify=y).
Entrenamiento del Modelo:
Construcción del clasificador DecisionTreeClassifier configurado con criterion="entropy" y una profundidad máxima acotada (max_depth=4) para prevenir el sobreajuste (overfitting).
Evaluación de Desempeño:
Cálculo de la métrica general de acierto (Accuracy).
Generación de la Matriz de Confusión (Verdaderos Positivos, Falsos Positivos, Falsos Negativos y Verdaderos Negativos).
Visualización del Reporte de Clasificación formateado al español (Precisión, Sensibilidad/Recall, Puntuación F1 y Soporte).
Módulo de Predicción de Nuevos Ingresantes:
Función interactiva predecir_nuevo_estudiante() que toma datos de un estudiante recién matriculado, simula el proceso de decisión y devuelve el diagnóstico esperado (Continúa / Abandonó) junto a su porcentaje de probabilidad de abandono.

Interpretación de Variables Relevantes
​Al analizar los nodos superiores del Árbol de Decisión y la reducción de entropía realizada en cada división, las variables más determinantes para predecir el abandono son:
​Cantidad de Materias Desaprobadas en el Primer Cuatrimestre: Es la variable con mayor Ganancia de Información. Registrar más de 2 a 3 materias reprobadas es el indicador directo de mayor peso para la deserción.
​Promedio del Primer Cuatrimestre: Un promedio general por debajo de 6.00 marca un umbral de vulnerabilidad académica crítica.
​Asistencia Promedio (%): Registros de asistencia inferiores al 60\% correlacionan directamente con la desvinculación progresiva del estudiante.
​Edad y Situación Laboral: La interacción entre estudiantes mayores de 30 años que trabajan activamente presenta mayor presión sobre los tiempos de cursada.

​Recomendaciones para la Institución
​Basándonos en las variables identificadas por el árbol, se sugieren las siguientes acciones preventivas para el Instituto Tecnológico Beltrán:
​Sistema de Alerta Temprana (SAT): Configurar alertas automáticas al cierre del primer cuatrimestre para detectar alumnos con promedio < 6.00 o con más de 2 materias desaprobadas.
​Refuerzo de Tutorías y Nivelación: Diseñar talleres de acompañamiento académico enfocado en las asignaturas con mayor tasa de reprobación durante el primer cuatrimestre.
​Protocolo de Asistencia Cero: Implementar un canal de contacto directo al detectar caídas consecutivas en la asistencia acumulada antes de llegar al cierre de cursada.
​Flexibilización de Horarios: Ofrecer alternativas de tutoría o cursada híbrida para estudiantes en franjas etarias adultas que combinan estudio y trabajo.
