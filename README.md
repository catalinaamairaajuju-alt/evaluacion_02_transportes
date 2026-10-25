
# Evaluación 02 — Análisis de Operaciones Aéreas en Chile

## Descripción
Proyecto de análisis exploratorio de datos sobre operaciones aéreas en Chile, utilizando información pública de la Junta de Aeronáutica Civil.

## Objetivo
Analizar la evolución de las operaciones aéreas por año, aeropuerto, tipo de operación y mes, mediante Python y herramientas de visualización.

## Tecnologías utilizadas
- Python 3.11
- Pandas y NumPy
- Matplotlib y Seaborn
- Jupyter Notebook
- Visual Studio Code
- Git y GitHub

## Fuente de datos
- Portal: datos.gob.cl
- Conjunto: Operaciones de Aeronaves
- Institución: Junta de Aeronáutica Civil
- Archivo original: data/raw/operaciones-aeropuertos.csv

## Metodología
1. Descarga y conservación de datos originales.
2. Perfilamiento y validación de calidad.
3. Transformación de fechas y categorías.
4. Exportación de datos procesados a CSV y Parquet.
5. Análisis de operaciones por año, aeropuerto, tipo y mes.
6. Generación de cinco gráficos.

## Resultados principales
- 16.172 registros y 4 columnas originales.
- 69 aeropuertos identificados.
- Período: enero de 2000 a septiembre de 2026.
- Total: 10.682.254 operaciones.
- Domésticas: 9.251.397 (86,61 %).
- Internacionales: 1.430.857 (13,39 %).
- Aeropuerto con más operaciones acumuladas: SCEL (3.132.971).
- Enero registra el mayor promedio mensual para 2000–2025.
- Se observa una caída pronunciada de operaciones durante 2020.

## Calidad de datos
No se detectaron valores nulos, filas duplicadas, fechas inválidas ni operaciones negativas en las comprobaciones realizadas.

## Visualizaciones
Los cinco gráficos se encuentran en `output/figures/`:

1. `grafico_01_evolucion_anual.png`
2. `grafico_02_top_aeropuertos.png`
3. `grafico_03_tipo_operacion.png`
4. `grafico_04_promedio_mensual.png`
5. `grafico_05_evolucion_tipo.png`

## Ejecución
1. Crear y activar un entorno virtual de Python.
2. Instalar las dependencias con `pip install -r requirements.txt`.
3. Abrir `notebooks/evaluacion02.ipynb` en Visual Studio Code.
4. Seleccionar el entorno virtual como kernel y ejecutar las celdas en orden.

## Consideraciones
Los datos de 2026 llegan solo hasta septiembre, por lo que sus totales anuales no son directamente comparables con años completos.

Los promedios mensuales se calcularon utilizando los años 2000–2025.

## Conclusión
El análisis evidencia un predominio de las operaciones domésticas, una concentración importante de actividad en SCEL y variaciones temporales, incluida la disminución de 2020.

Los resultados permiten describir tendencias de la actividad aérea en Chile a partir de los datos disponibles.
