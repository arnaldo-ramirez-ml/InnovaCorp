
Actúa como un Analista de Datos experto.

Tenemos un DataFrame de pandas llamado df_empleados con aproximadamente 2.000 filas y 13 columnas: id_empleado, nombres, genero, fecha_nacimiento, fecha_ingreso, area, cargo, nivel, salario_mensual, evaluacion_desempeno, modalidad_trabajo, ciudad, antiguedad_anios.

El objetivo exclusivo de este análisis es diagnosticar exhaustivamente los valores nulos/perdidos (missing data).

Genera el código en Python utilizando pandas y missingno (o seaborn en su defecto). Cada parte del análisis debe estar contenido en una celda para ejecutarse en Google Colab. Incluye la instalación de bibliotedas no disponibles de forma predeterminada.

El código debe realizar lo siguiente:

1. Resumen Cuantitativo:
- Conteo total de valores nulos por columna ordenado de mayor a menor.
- Porcentaje exacto de valores nulos respecto al total de filas para cada columna.
- Identificación del número de filas que tienen 1, 2 o más valores nulos simultáneamente.

2. Análisis Visual de Datos Faltantes:
- Matriz de nulidad (Matrix): Para visualizar la distribución espacial y los patrones de los nulos a lo largo de todo el dataset.
- Gráfico de barras (Bar): Para observar rápidamente la completitud de cada variable.
- Mapa de calor de correlación (Heatmap): Para identificar si la ausencia de un dato en una columna está estadísticamente relacionada con la ausencia en otra.

3. Diagnóstico y Comentarios:
- Comenta cada bloque de código explicando detalladamente qué buscar en los resultados y en las gráficas.