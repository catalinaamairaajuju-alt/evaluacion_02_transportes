# Evaluación 2 - Visualización de Datos de Transporte

## Problema

El transporte aéreo constituye una actividad relevante para la conectividad de Chile. Analizar las operaciones realizadas en los aeropuertos permite identificar tendencias temporales, concentración de actividad y diferencias entre vuelos domésticos e internacionales.

Este proyecto busca responder las siguientes preguntas:

- ¿Cómo evolucionaron las operaciones aéreas entre 2000 y 2026?
- ¿Cuáles son los aeropuertos que concentran más operaciones?
- ¿Qué proporción corresponde a operaciones domésticas e internacionales?
- ¿Cómo varía la actividad aérea según el mes?
- ¿Qué diferencias se observan en la distribución de operaciones?

## Fuente de datos

Los datos provienen del portal público [datos.gob.cl](https://datos.gob.cl/).

- **Institución:** Junta de Aeronáutica Civil (JAC).
- **Conjunto de datos:** Operaciones de Aeronaves.
- **Archivo:** `data/raw/operaciones-aeropuertos.csv`.
- **Período disponible:** enero de 2000 a septiembre de 2026.
- **Registros:** 16.172.
- **Variables originales:** 4.

El archivo contiene información sobre el período, el aeropuerto, la clasificación de la operación y la cantidad de operaciones registradas.

## Adquisición

El archivo CSV se obtuvo desde una fuente pública y se almacenó en la carpeta `data/raw/`.

Se conservó el archivo original sin modificaciones manuales para asegurar la trazabilidad del proceso.

Las transformaciones se realizaron mediante Python, generando archivos independientes en `data/processed/`.

## Configuración del entorno

El proyecto se desarrolló utilizando:

- Python 3.11
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook
- Visual Studio Code
- Git y GitHub

Las dependencias se administran mediante `requirements.txt`.

## Estructura del proyecto

```text
evaluacion_02_transportes/
├── data/
│   ├── raw/
│   │   └── operaciones-aeropuertos.csv
│   └── processed/
├── notebooks/
│   └── evaluacion02.ipynb
├── src/
├── output/
│   └── figures/
├── docs/
├── README.md
├── requirements.txt
└── .gitignore
```

La carpeta `raw` contiene los datos originales; `processed`, los datos transformados; `notebooks`, el análisis; y `output/figures`, las visualizaciones exportadas.

## Perfilamiento

El perfilamiento inicial permitió identificar:

| Indicador | Resultado |
|---|---:|
| Registros | 16.172 |
| Columnas originales | 4 |
| Aeropuertos identificados | 69 |
| Primera fecha | Enero de 2000 |
| Última fecha | Septiembre de 2026 |
| Operaciones totales | 10.682.254 |

Las variables originales son:

- `mes_id`: período de registro.
- `aeropuerto_oaci`: identificador del aeropuerto.
- `internacional_domestico`: clasificación de la operación.
- `cnt_operaciones`: cantidad de operaciones.

## Calidad de datos

Se realizaron comprobaciones de:

- Valores nulos.
- Registros duplicados.
- Fechas inválidas.
- Cantidades negativas.
- Coherencia de los totales agregados.

En las verificaciones ejecutadas no se identificaron valores nulos, duplicados, fechas inválidas ni operaciones negativas.

## Preparación

Se utilizó Pandas para cargar, inspeccionar y preparar los datos.

El procesamiento incluyó la interpretación de fechas, la estandarización de variables analíticas y la creación de una versión limpia del conjunto.

Los resultados se exportaron a CSV y Parquet, manteniendo separado el archivo original.

## Variables derivadas

Se incorporaron cuatro variables para facilitar el análisis:

| Variable | Descripción |
|---|---|
| `fecha` | Fecha interpretada a partir del período original |
| `anio` | Año de la operación |
| `mes` | Mes de la operación |
| `tipo_operacion` | Categoría de operación utilizada en el análisis |

El conjunto procesado contiene ocho columnas.

## Dimensionalidad

El análisis considera diferentes dimensiones:

| Dimensión | Variable | Aplicación |
|---|---|---|
| Temporal | `anio` | Evolución anual |
| Temporal | `mes` | Comportamiento mensual |
| Geográfica | `aeropuerto_oaci` | Comparación entre aeropuertos |
| Categórica | `tipo_operacion` | Comparación doméstica e internacional |
| Cuantitativa | `cnt_operaciones` | Medición de actividad aérea |

La combinación de estas dimensiones permite analizar el comportamiento de las operaciones desde distintas perspectivas.

## Transformaciones analíticas

Se realizaron agrupaciones y agregaciones para obtener:

- Operaciones totales por año.
- Operaciones acumuladas por aeropuerto.
- Operaciones por tipo.
- Promedio mensual de operaciones.
- Evolución anual separada por tipo.
- Distribución de cantidades de operaciones.

Las transformaciones se desarrollaron mediante operaciones de Pandas, principalmente agrupaciones y sumatorias.

## Diseño de visualizaciones

Las visualizaciones se seleccionaron según la pregunta analítica y el tipo de información.

| Visualización | Pregunta | Tipo de gráfico |
|---|---|---|
| Evolución anual | ¿Cómo cambia la actividad con el tiempo? | Líneas |
| Top 10 aeropuertos | ¿Dónde se concentran las operaciones? | Barras |
| Tipo de operación | ¿Cuál es la proporción por categoría? | Circular |
| Promedio mensual | ¿Cómo varía la actividad durante el año? | Barras |
| Evolución por tipo | ¿Cómo evolucionan ambas categorías? | Líneas |
| Distribución de operaciones | ¿Cómo se distribuyen las cantidades registradas? | Histograma |
| Comparación por tipo | ¿Cómo difieren las distribuciones? | Diagrama de caja |

Se priorizaron títulos descriptivos, etiquetas comprensibles y una representación coherente de los valores.

## Matplotlib

Matplotlib se utilizó para representar tendencias, comparaciones y proporciones.

Entre las visualizaciones realizadas se encuentran:

1. Evolución anual de operaciones.
2. Top 10 de aeropuertos.
3. Proporción de operaciones domésticas e internacionales.
4. Promedio mensual.
5. Evolución anual por tipo.

Los gráficos se exportaron en formato PNG a `output/figures/`.

## Seaborn

Seaborn se utilizó para complementar el análisis mediante visualizaciones estadísticas.

Se elaboraron:

6. Histograma de distribución de operaciones.
7. Diagrama de caja de operaciones según su clasificación.

Estas representaciones permiten examinar la dispersión y las diferencias entre categorías.

## Visualización multidimensional

El análisis combina dimensiones temporales, geográficas y categóricas con la cantidad de operaciones.

Por ejemplo, la evolución anual por tipo de operación utiliza:

- Año.
- Tipo de operación.
- Cantidad de operaciones.

Esta combinación permite comparar simultáneamente la evolución temporal de las categorías doméstica e internacional.

## Benchmark visual

Se realizó una comparación de tiempos de generación de histogramas utilizando Matplotlib y Seaborn.

En una ejecución se obtuvieron los siguientes resultados:

| Biblioteca | Tiempo |
|---|---:|
| Matplotlib | 0,0731 segundos |
| Seaborn | 0,0931 segundos |

En esa medición, Matplotlib presentó un menor tiempo de ejecución.

Estos valores corresponden a una prueba puntual y no permiten establecer una superioridad general de rendimiento. Los resultados pueden variar según el entorno, el tamaño de los datos y las condiciones de ejecución.

La comparación de claridad, legibilidad y facilidad de interpretación debe complementarse con una revisión visual de los gráficos.

## Validación

Se verificó que los totales obtenidos mediante distintas agrupaciones coincidieran con el total del conjunto de datos.

Se utilizaron instrucciones `assert` para comprobar la coherencia de los resultados.

Las validaciones de agregación por año y tipo de operación finalizaron correctamente, con un total de **10.682.254 operaciones**.

## Hallazgos

### Hallazgo 1: Predominio de operaciones domésticas

Las operaciones domésticas representan el 86,61 % del total, equivalentes a 9.251.397 operaciones.

Las internacionales corresponden al 13,39 %, con 1.430.857 operaciones.

### Hallazgo 2: Concentración de actividad en SCEL

El aeropuerto SCEL presenta la mayor cantidad acumulada, con 3.132.971 operaciones.

Esto evidencia una concentración importante de actividad en dicho aeropuerto dentro del conjunto analizado.

### Hallazgo 3: Evolución temporal

La serie anual muestra una disminución pronunciada durante 2020 y una recuperación posterior.

Los datos permiten describir esta variación, pero no demostrar por sí solos sus causas.

## Limitaciones

El conjunto presenta las siguientes limitaciones:

- Los registros de 2026 llegan solamente hasta septiembre.
- Los totales de años incompletos no deben compararse directamente con años completos.
- El análisis es descriptivo y no permite establecer relaciones causales.
- Los resultados dependen de la cobertura y los criterios de registro de la fuente.
- El benchmark se realizó mediante una medición puntual.

Para analizar estacionalidad se utilizaron los años completos de 2000 a 2025.

## Consideraciones éticas

El proyecto se desarrolló considerando principios de integridad, transparencia y responsabilidad profesional.

Se mantuvieron los datos originales sin modificaciones manuales y se documentaron las transformaciones realizadas.

También se verificó la calidad de la información y se utilizaron herramientas de control de versiones para mantener un registro de cambios.

Las conclusiones se formularon a partir de los resultados observados, evitando presentar asociaciones como relaciones causales.

Se declara expresamente la cobertura parcial de 2026 para prevenir interpretaciones engañosas.

## Conclusiones

El análisis de 16.172 registros permitió caracterizar la actividad aérea en Chile entre enero de 2000 y septiembre de 2026.

Se identificó un predominio de operaciones domésticas, una concentración importante en SCEL y variaciones temporales relevantes.

El uso de Pandas, Matplotlib y Seaborn permitió realizar transformaciones, visualizaciones y validaciones reproducibles.

Asimismo, Git y GitHub facilitaron el control de versiones y la organización del proyecto.

Los resultados muestran la importancia de interpretar los datos considerando su calidad, cobertura y limitaciones.

## Instrucciones de ejecución

1. Descargar o clonar el repositorio.
2. Abrir la carpeta del proyecto en Visual Studio Code.
3. Crear un entorno virtual de Python.
4. Activar el entorno virtual.
5. Instalar las dependencias.
6. Abrir `notebooks/evaluacion02.ipynb`.
7. Seleccionar el intérprete de Python del entorno virtual.
8. Ejecutar las celdas secuencialmente desde el inicio.

Comandos de instalación para Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Los datos originales deben permanecer en `data/raw/`.


## Autor
**Catalina Riveros**

Proyecto académico — Evaluación 2: Visualización de Datos de Transporte.

Repositorio: https://github.com/catalinaamairaajuju-alt/evaluacion_02_transportes
