# Dataset InnovaCorp — Empleados

Caso sintético para un curso de **Calidad de Datos y Análisis Exploratorio** en Python / Pandas.

---

## Notebook en Colab

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/arnaldo-ramirez-ml/InnovaCorp/blob/main/InnovaCorp.ipynb)

Notebook semilla.

## 1. Descripción general

InnovaCorp es una empresa peruana ficticia. El dataset contiene su plantilla de empleados:

---

## 2. Archivos entregables

| Archivo | Descripción | Uso |
|---|---|---|
| `InnovaCorp.sqlite` | Datos en formato SQLite | Para el uso de los alumnos |
| empleados.parquet| Formato preferido para análisis directo con Python | Para el uso de los alumnos |
| empleados.csv| Legible por casi cualquier medio - utf8 | Mantenido por compatibilidad |
| `README.md` | Este documento | Documentación |

---

## 3. Dimensiones del dataset

- **Total filas:** 2,014
- **IDs únicos:** 2,006 (2,000 originales + 6 casi-duplicados con id propio)
- **Filas duplicadas exactas:** 8
- **Columnas:** 13

---

## 4. Esquema de columnas

| # | Nombre | Tipo | Descripción |
|---|---|---|---|
| 1 | `id_empleado` | string | Clave primaria. Formato `EMP-00001` a `EMP-02006`. |
| 2 | `nombres` | string | Nombres y apellidos peruanos generados aleatoriamente. |
| 3 | `genero` | categórico | `M` (48%), `F` (48%), `Otro` (4%). |
| 4 | `fecha_nacimiento` | fecha (ISO `YYYY-MM-DD`) | Edad derivada con respecto al 31-dic-2025. |
| 5 | `fecha_ingreso` | fecha (ISO `YYYY-MM-DD`) | Fecha de alta en la empresa. |
| 6 | `area` | categórico | Una de 8 áreas (ver §5.1). |
| 7 | `cargo` | string | Cargo coherente con área y nivel. |
| 8 | `nivel` | ordinal | `Junior`, `Semi-Senior`, `Senior`, `Líder`, `Gerente`, `VP`. |
| 9 | `salario_mensual` | numérico | Soles peruanos (PEN), 2 decimales. |
| 10 | `evaluacion_desempeno` | numérico | Escala 1.0–5.0, una decimal. |
| 11 | `modalidad_trabajo` | categórico | `Presencial` (30%), `Híbrido` (50%), `Remoto` (20%). |
| 12 | `ciudad` | categórico | `Lima` (75%), `Arequipa` (15%), `Trujillo` (10%). |
| 13 | `antiguedad_anios` | entero | Redundante con `fecha_ingreso` a propósito (referencia 31-dic-2025). |

---

## 5. Catálogos de valores categóricos

### 5.1 Áreas (8)

`Tecnología`, `Producto`, `Marketing`, `Ventas`, `Operaciones`, `Finanzas`, `Recursos Humanos`, `Legal`.

### 5.2 Niveles ordinales (6)

`Junior` → `Semi-Senior` → `Senior` → `Líder` → `Gerente` → `VP`.

### 5.3 Cargos por área

Patrón (ejemplo Tecnología):

| Nivel | Cargo |
|---|---|
| Junior | Desarrollador Junior |
| Semi-Senior | Desarrollador Semi-Senior |
| Senior | Desarrollador Senior |
| Líder | Tech Lead |
| Gerente | Gerente de Tecnología |
| VP | VP de Tecnología |

Se aplica un patrón análogo en cada área (`Analista Financiero`, `Ejecutivo de Ventas`, `Especialista de Marketing`, etc.).

---


## 6. Carga rápida (Python)

```python
import pandas as pd
import sqlite3

con = sqlite3.connect("InnovaCorp.db")
df = pd.read_sql("SELECT * FROM EMPLEADOS", con)

print(df.shape)         # (2014, 13)
print(df.dtypes)
print(df.head())
```

---
