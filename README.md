# Challenge-Telecom-X-parte-2
📋 Descripción del Proyecto
Este proyecto forma parte del desafío "Churn de Clientes" de Telecom X, una empresa que enfrenta una alta tasa de cancelaciones de servicio. El objetivo es realizar un análisis exploratorio completo (EDA) para identificar los factores que llevan a la pérdida de clientes y generar insights estratégicos que apoyen al equipo de Data Science en la construcción de modelos predictivos.

🎯 Objetivos

✅ Extraer y procesar datos desde una API externa en formato JSON
✅ Aplicar el proceso ETL (Extracción, Transformación y Carga)
✅ Limpiar y manejar inconsistencias en los datos
✅ Realizar un Análisis Exploratorio de Datos (EDA)
✅ Crear visualizaciones estratégicas para identificar patrones de evasión
✅ Generar insights accionables para reducir el churn


🗂️ Estructura del Proyecto
telecom-x-churn/
│
├── README.md                  # Documentación del proyecto
├── telecom_x_analisis.py      # Código fuente principal (análisis completo)
│
└── outputs/
    ├── churn_distribucion.png     # Gráfico: distribución de evasión
    ├── churn_categoricas.png      # Gráfico: evasión por variables categóricas
    └── churn_numericas.png        # Gráfico: evasión por variables numéricas

🔧 Dependencias e Instalación
Requisitos previos

Python 3.8 o superior
pip (gestor de paquetes de Python)

Instalación de librerías
Ejecuta el siguiente comando en tu terminal:
bashpip install pandas numpy requests matplotlib seaborn
LibreríaVersión recomendadaUsopandas>= 2.0Manipulación de datosnumpy>= 1.24Operaciones numéricasrequests>= 2.28Consumo de APImatplotlib>= 3.7Visualizaciones baseseaborn>= 0.12Visualizaciones estadísticas

🚀 Cómo Ejecutar el Proyecto
Opción 1 — Google Colab (recomendado)

Abre Google Colab
Crea un nuevo notebook
Copia y pega el código de telecom_x_analisis.py
Ejecuta todas las celdas con Ctrl + F9

Opción 2 — Jupyter Notebook local
bash# 1. Clona o descarga el repositorio
git clone https://github.com/tu-usuario/telecom-x-churn.git
cd telecom-x-churn

# 2. Instala las dependencias
pip install pandas numpy requests matplotlib seaborn

# 3. Abre Jupyter
jupyter notebook

# 4. Ejecuta el archivo telecom_x_analisis.py
Opción 3 — Script Python directo
bashpython telecom_x_analisis.py

📊 Descripción del Dataset
Los datos son extraídos directamente desde la API de Telecom X en formato JSON:
URL: https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json
Diccionario de variables principales
ColumnaTipoDescripcióncustomerIDStringIdentificador único del clientegenderCategóricaGénero del cliente (Male/Female)SeniorCitizenBinaria¿Es adulto mayor? (0/1)PartnerCategórica¿Tiene pareja? (Yes/No)DependentsCategórica¿Tiene dependientes? (Yes/No)tenureNuméricaMeses como clienteContractCategóricaTipo de contrato (Month-to-month, One year, Two year)PaymentMethodCategóricaMétodo de pagoMonthlyChargesNuméricaCargo mensual en USDTotalChargesNuméricaTotal acumulado pagado en USDInternetServiceCategóricaTipo de servicio de internetChurnBinaria (target)¿El cliente canceló? (Yes/No → 1/0)DailyChargesNuméricaCargo diario calculado (MonthlyCharges / 30)

🔍 Etapas del Análisis
1. 📥 Extracción de Datos
Consumo de la API mediante requests.get() y conversión del JSON anidado a DataFrame usando pd.json_normalize().
2. 🧹 Limpieza y Transformación (ETL)

Eliminación de filas duplicadas
Conversión de tipos de datos incorrectos (TotalCharges a numérico)
Manejo de valores nulos (imputación con mediana)
Normalización de la variable Churn a valores binarios (0/1)
Renombramiento de columnas (eliminación de prefijos del JSON anidado)

3. 🔢 Ingeniería de Variables

Creación de la columna DailyCharges = MonthlyCharges / 30

4. 📈 Análisis Descriptivo
Cálculo de métricas estadísticas: media, mediana, desviación estándar, mínimo y máximo para todas las variables numéricas.
5. 📊 Visualizaciones

Distribución del Churn: gráfico de barras y torta
Variables categóricas: tasa de evasión por género, contrato, método de pago, etc.
Variables numéricas: boxplots de tenure, MonthlyCharges y TotalCharges segmentados por Churn


💡 Principales Insights

Los siguientes hallazgos fueron obtenidos del análisis exploratorio:


📌 La tasa general de evasión ronda el 26% de los clientes
📌 Los clientes con contrato mes a mes tienen una tasa de cancelación significativamente mayor que los contratos anuales o bianuales
📌 Los clientes que cancelaron llevan en promedio menos meses como clientes (bajo tenure)
📌 Los clientes con cargos mensuales más altos tienen mayor tendencia a cancelar
📌 Los clientes adultos mayores (SeniorCitizen = 1) presentan una mayor tasa de churn
📌 Los clientes sin pareja ni dependientes cancelan con mayor frecuencia
