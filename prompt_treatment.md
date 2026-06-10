# Tratamiento de Valores Faltantes Basado en Hipótesis Aceptadas

Actúa como un Científico de Datos Senior especializado en limpieza y preparación de datos.

Dispones de un DataFrame de pandas llamado **df_empleados**.

## Objetivo

Aplicar directamente los tratamientos definidos para los valores faltantes, asumiendo que las hipótesis sobre los mecanismos de ausencia ya fueron analizadas y validadas previamente.

**No debes volver a validar las hipótesis ni realizar pruebas estadísticas.**

Tu tarea consiste únicamente en:

1. Ejecutar las transformaciones indicadas.
2. Generar código Python limpio y comentado.
3. Mostrar un resumen de los cambios realizados.
4. Verificar que no se introduzcan errores durante el proceso.

---

## Tratamientos a implementar

### salario_mensual

Hipótesis aceptada:
- Mecanismo MCAR.

Tratamiento:
- Imputar los valores faltantes utilizando la mediana de `nivel`.
- Si existen combinaciones de (`nivel`, `area`) con suficiente cantidad de registros, utilizar la mediana por (`nivel`, `area`).
- Si alguna combinación no posee suficientes observaciones, utilizar la mediana por `nivel` como respaldo.

---

### evaluacion_desempeno

Hipótesis aceptada:
- Mecanismo MAR asociado a la antigüedad.

Tratamiento:
- No imputar valores.
- Crear una nueva columna booleana llamada `tiene_evaluacion`.
- Valor `True` cuando exista evaluación.
- Valor `False` cuando la evaluación sea nula.

---

### ciudad

Hipótesis aceptada:
- Mecanismo MCAR.

Tratamiento:
- Reemplazar los valores faltantes por la categoría `"No especificado"`.

---

### modalidad_trabajo

Hipótesis aceptada:
- Los valores `"N/A"` representan datos faltantes de captura.

Tratamiento:
1. Convertir `"N/A"` a `NaN`.
2. Reemplazar los faltantes por `"No especificado"`.
3. Conservar la columna como categórica.

---

### area

Hipótesis aceptada:
- Los faltantes son MCAR.
- Existen problemas de calidad de formato.

Tratamiento:
1. Eliminar espacios iniciales y finales.
2. Unificar mayúsculas/minúsculas.
3. Estandarizar variantes equivalentes (por ejemplo, `"RR.HH."`, `"Recursos Humanos"`, `"RRHH"`).
4. Convertir cadenas vacías a `NaN`.
5. Reemplazar faltantes por `"No especificado"`.

---

## Requisitos de implementación

Genera el código en celdas separadas.

### Celda 1
Crear una copia de trabajo:

```python
df_trabajo = df_empleados.copy()
```

### Celda 2
Aplicar el tratamiento de `salario_mensual`.

### Celda 3
Aplicar el tratamiento de `evaluacion_desempeno`.

### Celda 4
Aplicar el tratamiento de `ciudad`.

### Celda 5
Aplicar el tratamiento de `modalidad_trabajo`.

### Celda 6
Aplicar el tratamiento de `area`.

### Celda 7
Generar un reporte final que muestre:

- Cantidad de valores faltantes antes y después.
- Número de registros afectados por cada transformación.
- Tipos de datos finales.
- Verificación de que no existan errores en las columnas tratadas.

## Formato de salida esperado

Para cada celda:

- Breve explicación.
- Código Python ejecutable en Google Colab.
- Comentarios claros dentro del código.

No realizar análisis exploratorio ni validación estadística.
Asumir que todas las hipótesis son correctas y proceder directamente con el tratamiento.
