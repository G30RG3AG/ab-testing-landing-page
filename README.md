Experimento A/B en página de inicio
Descripción del proyecto
Este proyecto analiza un experimento A/B realizado sobre una página de
inicio (landing page) con dos versiones: A y B. El objetivo es
identificar qué versión ofrece mejores resultados para el negocio
mediante el análisis del gasto de los usuarios convertidos, la tasa de
conversión y la relación entre variables categóricas y la conversión.
El análisis se realiza con Python y herramientas de análisis estadístico
para respaldar las recomendaciones con evidencia cuantitativa.
Objetivos
- Explorar y validar la calidad del conjunto de datos.
- Comparar el gasto promedio de los usuarios convertidos entre las
  versiones A y B.
- Comparar las tasas de conversión de ambas versiones.
- Evaluar la asociación entre la fuente de tráfico y la conversión.
- Evaluar la asociación entre el tipo de usuario y la conversión.
- Visualizar los resultados y formular recomendaciones de negocio.
Datos
El archivo de trabajo es landing_experiment.csv. El conjunto de datos
contiene 40,000 registros y 9 variables:
  Variable                            Descripción
  user_id                           Identificador del usuario
  date                              Fecha de exposición a la página
  landing                           Versión de la página mostrada: A o
                                      B
  region                            Región geográfica del usuario
  dispositivo                       Tipo de dispositivo
  traffic_source                    Fuente de tráfico
  user_type                         Tipo de usuario: nuevo o recurrente
  converted                         Indicador de conversión
  gasto                             Gasto registrado por el usuario; es
                                  cero cuando no hubo gasto
La información cubre el periodo del 1 al 28 de enero de 2026. Se
identificaron 40,000 usuarios únicos. La distribución por versión fue de
19,982 registros para A y 20,018 para B, una asignación prácticamente
equilibrada.
El archivo de datos no se incluye en este repositorio. Si los datos
están sujetos a las condiciones de uso de una plataforma educativa,
deben compartirse únicamente cuando exista autorización para hacerlo.

Herramientas y bibliotecas
- Python --- análisis y procesamiento de datos.
- Pandas y NumPy --- manipulación y exploración de datos.
- SciPy --- pruebas estadísticas.
- Statsmodels --- prueba z para comparar proporciones.
- Matplotlib y Seaborn --- visualización de datos.
Metodología
1. Exploración y calidad de datos
Se inspeccionaron las primeras filas, los tipos de datos, los valores
ausentes, los identificadores únicos, el rango temporal y la
distribución de las variables categóricas. Las versiones A y B
presentaron cantidades similares de registros.
2. Gasto promedio de los usuarios convertidos
Se comparó el gasto entre los usuarios que convirtieron en cada versión
mediante una prueba t de Welch para muestras independientes, con un
nivel de significancia de 0.05.
- Estadístico t: -9.4810
- Valor p: menor que 0.05
Resultado: se rechazó la hipótesis nula de igualdad de medias. El
gasto promedio de los usuarios convertidos fue significativamente mayor
en la versión B.
3. Tasa de conversión por versión
Se utilizó una prueba z para dos proporciones para comparar las
tasas de conversión de las páginas A y B.
  Versión     Usuarios   Conversiones   Tasa de conversión
  A             19,982          2,512              12.57 %
  B             20,018          3,194              15.95 %
- Estadístico z: -9.6774
- Valor p: menor que 0.05
- Diferencia entre las tasas: aproximadamente 3.38 puntos
  porcentuales a favor de B.
Resultado: se rechazó la hipótesis nula de igualdad de proporciones.
La versión B tuvo una tasa de conversión significativamente superior a
la versión A.
4. Fuente de tráfico y conversión
Se aplicó una prueba chi-cuadrado de independencia para evaluar la
asociación entre traffic_source y converted.
- Estadístico chi-cuadrado: 8.6621
- Valor p: 0.034138
Resultado: se rechazó la hipótesis nula de independencia. Se
encontró una asociación estadísticamente significativa entre la fuente
de tráfico y la conversión.
Organic generó la mayor cantidad absoluta de conversiones (2,480),
mientras que Email presentó la tasa de conversión más alta,
aproximadamente 14.99 %. Ads registró 1,759 conversiones y una tasa
aproximada de 14.73 %. Estas diferencias deben interpretarse
considerando tanto el volumen de usuarios como la tasa de conversión.
5. Tipo de usuario y conversión
Se aplicó una prueba chi-cuadrado de independencia para evaluar la
relación entre user_type y converted.
- Estadístico chi-cuadrado: 0.5135
- Valor p: 0.473634
Resultado: no se rechazó la hipótesis nula. No se encontró evidencia
estadística suficiente para afirmar que el tipo de usuario esté asociado
con la conversión.
Las tasas observadas fueron aproximadamente 14.36 % para usuarios
nuevos y 14.09 % para recurrentes. La diferencia es pequeña y no
resultó estadísticamente significativa.
6. Visualización
Se elaboraron gráficos de cantidades absolutas y gráficos de
proporciones para examinar la conversión según la fuente de tráfico y el
tipo de usuario. Las visualizaciones permiten distinguir el volumen
total de conversiones de la efectividad relativa de cada categoría.
Conclusiones principales
1. La versión B obtuvo mejores resultados en los dos indicadores
   principales: presentó una tasa de conversión de 15.95 %, frente a
   12.57 % de A, y también un gasto promedio significativamente mayor
   entre los usuarios convertidos.
2. La fuente de tráfico mostró asociación con la conversión.
   Organic concentró el mayor volumen de conversiones, mientras que
   Email tuvo la tasa de conversión observada más alta.
3. No se encontró una asociación estadísticamente significativa entre
   el tipo de usuario y la conversión. Con estos resultados, no hay
   evidencia suficiente para afirmar que los usuarios nuevos o
   recurrentes conviertan mejor.
4. Los resultados estadísticos ayudan a orientar decisiones, pero una
   asociación no demuestra causalidad por sí sola.
Recomendaciones de negocio
- Priorizar la versión B como candidata para la página de inicio,
  dado que superó a A en tasa de conversión y gasto promedio entre los
  usuarios convertidos.
- Continuar monitoreando los canales de adquisición. Organic
  aporta el mayor volumen de conversiones y Email presenta la tasa
  observada más alta; para decidir inversiones, conviene añadir costos
  de adquisición e ingresos o valor generado por canal.
- No diferenciar la página únicamente por tipo de usuario con base
  en este análisis, ya que no se encontró evidencia estadística
  suficiente de una asociación con la conversión.
- Validar el rendimiento de la versión B después de su implementación
  y vigilar los indicadores a lo largo del tiempo.
Cómo reproducir el análisis
1. Clona o descarga este repositorio.
2. Obtén landing_experiment.csv desde la fuente autorizada y colócalo
   en la ruta que utilice el notebook.
3. Abre ab_testing_analysis.ipynb en Jupyter Notebook o JupyterLab.
4. Instala las bibliotecas necesarias si aún no están disponibles:
   pip install pandas numpy scipy statsmodels matplotlib seaborn jupyter
5. Ejecuta las celdas en orden para reproducir la exploración, las
   pruebas estadísticas y las visualizaciones.

Autor
Proyecto de análisis de datos desarrollado como parte de la formación en
Data Analytics.
