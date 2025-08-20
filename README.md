# TelecomX-Churn-Analysis-P1

Telecom X – Análisis de Evasión de Clientes (Parte 1)

Proyecto de ETL + EDA para comprender la evasión de clientes (Churn) en Telecom X y sentar las bases de un modelo predictivo.

📌 Objetivo

Extraer datos desde la API (JSON).

Transformar y estandarizar la información (aplanado, limpieza, features).

Cargar un dataset limpio para análisis.

Explorar patrones de churn con visualizaciones y métricas descriptivas.

Entregar un informe dentro del notebook con hallazgos y recomendaciones.

TelecomX-Churn-Analysis-P1/
├─ notebooks/
│  └─ TelecomX-Churn-Analysis-P1.ipynb   # Notebook principal (ETL + EDA + Informe)
├─ data/
│  └─ TelecomX_clean_P1.csv              # (Opcional) Dataset limpio exportado
├─ README.md                              # Este archivo
├─ .gitignore
└─ LICENSE

🔗 Fuente de datos

API JSON (GitHub Raw):
https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/main/TelecomX_Data.json

El JSON contiene:

customerID (ID único)

Churn (objetivo: Yes/No)

Bloques anidados: customer, phone, internet, account (aplanados en el ETL)

▶️ Cómo ejecutar (Colab recomendado)

Abre el notebook notebooks/TelecomX-Churn-Analysis-P1.ipynb en Google Colab.

Ejecuta las celdas en orden:

Extracción: descarga del JSON con requests.

Transformación: json_normalize → limpieza → estandarización.

EDA: visualizaciones y métricas.

Informe: celda que genera el reporte final en Markdown.

(Opcional) Exporta el dataset limpio:

df_clean.to_csv("data/TelecomX_clean_P1.csv", index=False)

🧪 Pipeline ETL (Resumen)

Extract

Carga del JSON desde la API.

Conversión a DataFrame.

Transform

Aplanado de estructuras anidadas con pandas.json_normalize(sep="_").

Tipificación: conversión de cargos a numérico.

Binarios: mapeo Yes/No → 1/0 (robusto a “No internet/phone service”).

Features:

Cargo_Diario = Cargo_Mensual / 30.

NumServicios = suma de servicios binarios (teléfono, seguridad, backup, streaming, etc.).

Validaciones: nulos, duplicados por customerID, categorías.

Load

df_clean listo para EDA / modelado.

Exportación opcional a data/TelecomX_clean_P1.csv.

📊 Análisis Exploratorio (EDA)

Distribución de Evasión (0 = No, 1 = Sí).

Evasión por variables categóricas:

Tipo de contrato, método de pago, servicio de internet, género.

Variables numéricas vs Evasión:

Antigüedad (tenure), cargo mensual, cargo total, cargo diario.

Boxplots, histogramas y matriz de correlación.

KPIs automáticos: tasas por segmento y medianas comparativas.

📝 Informe dentro del notebook

El notebook genera un informe en Markdown con:

Introducción (problema y objetivo).

Limpieza y Tratamiento (qué se hizo en ETL).

EDA (tablas + gráficos).

Conclusiones e Insights.

Recomendaciones de acción.
