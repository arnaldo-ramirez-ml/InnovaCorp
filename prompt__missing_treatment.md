# Validación de Hipótesis de Valores Faltantes y Aplicación de Tratamientos

Actúa como un Científico de Datos Senior especializado en calidad de datos y análisis de valores faltantes.

Dispones de un DataFrame de pandas llamado **df_empleados**.

## Objetivo

Validar empíricamente las hipótesis planteadas sobre los mecanismos de ausencia de datos (MCAR, MAR o NMAR) y, únicamente si la evidencia las respalda, generar el código Python para aplicar el tratamiento sugerido.

## Metodología requerida

Para cada variable indicada:

1. Analiza la distribución de los valores faltantes.
2. Construye una variable indicadora de ausencia (`is_null`).
3. Evalúa si la ausencia está asociada con otras variables observadas mediante:
   - Tablas de contingencia.
   - Comparación de distribuciones.
   - Chi-cuadrado para variables categóricas.
   - t-test o Mann-Whitney para variables numéricas cuando corresponda.
   - Cualquier otra prueba estadística que consideres pertinente.
4. Explica claramente la evidencia encontrada.
5. Determina si la hipótesis original queda:
   - VALIDADA
   - NO VALIDADA
   - INCONCLUSA

## Reglas de decisión

### Si la hipótesis queda VALIDADA

- Explica brevemente por qué.
- Genera el código Python necesario para implementar exactamente el tratamiento sugerido.
- Incluye comentarios explicativos en el código.

### Si la hipótesis queda NO VALIDADA

- Explica claramente qué evidencia contradice la hipótesis.
- NO implementes el tratamiento originalmente propuesto.
- Propón un tratamiento alternativo más adecuado.
- Justifica técnicamente la recomendación.
- Genera el código Python correspondiente al nuevo tratamiento.

### Si la hipótesis queda INCONCLUSA

- Explica qué información falta para validarla.
- No implementes cambios automáticos.
- Propón análisis adicionales.

---

## Hipótesis a validar

### salario_mensual

**Hipótesis:**

- Mecanismo: MCAR
- Justificación:
  - No existe patrón aparente con otras columnas.
  - Se espera que los nulos estén distribuidos homogéneamente por área y nivel.

**Tratamiento sugerido:**

- Imputar con la mediana por nivel.
- Si se detecta dependencia con área, imputar por combinación (nivel, área).

---

### evaluacion_desempeno

**Hipótesis:**

- Mecanismo: MAR
- Justificación:
  - Los nulos se concentran en empleados con poca antigüedad.
  - La ausencia dependería de variables observables.

**Tratamiento sugerido:**

- No imputar.
- Crear una columna booleana `tiene_evaluacion`.

---

### ciudad

**Hipótesis:**

- Mecanismo: MCAR
- Justificación:
  - Posible error aleatorio de captura.
  - No debería concentrarse en ningún grupo específico.

**Tratamiento sugerido:**

- Reemplazar faltantes por la categoría `"No especificado"`.

---

### modalidad_trabajo

**Hipótesis:**

- Mecanismo: Ambiguo.
- Justificación:
  - Existen registros con `"N/A"`.
  - Podría tratarse de fallas de captura (MCAR) o de procesos incompletos (MAR/NMAR).

**Tratamiento sugerido:**

1. Convertir `"N/A"` a NaN.
2. Evaluar el mecanismo de ausencia.
3. Aplicar el tratamiento más apropiado según la evidencia.

---

### area

**Hipótesis:**

- Mecanismo: MCAR.
- Justificación:
  - Existen vacíos, espacios y variantes de formato.
  - Los verdaderos faltantes deberían ser aleatorios.

**Tratamiento sugerido:**

1. Normalizar formatos.
2. Convertir vacíos a NaN.
3. Reemplazar faltantes por `"No especificado"`.

---

## Formato de salida

Para cada variable generar:

```text
# Variable: nombre_variable

## Validación de hipótesis

Evidencia encontrada:
...

Resultado:
[VALIDADA | NO VALIDADA | INCONCLUSA]

## Recomendación

...

## Código Python

```python
...
```
```

Al finalizar, generar una tabla resumen:

| Variable | Hipótesis inicial | Resultado | Tratamiento final |
|-----------|------------------|------------|-------------------|
| ... | ... | ... | ... |
