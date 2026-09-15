# 🚗 Data Experience: Análisis y predicción del precio de vehículos usados

## 📌 Descripción del proyecto

Este proyecto fue desarrollado como parte de **Data Experience** y tiene como propósito analizar un conjunto de datos de vehículos usados para identificar qué características se relacionan con su precio de venta y evaluar qué tan útil es la información disponible para realizar predicciones.

A través de diferentes etapas de exploración, limpieza, análisis estadístico y modelamiento predictivo, buscamos responder una pregunta central:

> 🔎 **¿Qué factores se relacionan con el precio de venta de los vehículos usados y qué tan útil puede ser el precio actual para estimarlo?**

## 🎯 Objetivo

Analizar las características de los vehículos usados y construir modelos predictivos que permitan estimar su **precio de venta (`Selling_Price`)** a partir de diferentes variables del vehículo.

## 📊 Sobre el dataset

El conjunto de datos contiene información sobre vehículos usados y sus principales características.

Entre las variables analizadas se encuentran:

| Variable | Descripción |
|---|---|
| `Car_Name` | Nombre del vehículo |
| `Year` | Año del vehículo |
| `Selling_Price` | Precio de venta |
| `Present_Price` | Precio actual |
| `Kms_Driven` | Kilometraje recorrido |
| `Fuel_Type` | Tipo de combustible |
| `Seller_Type` | Tipo de vendedor |
| `Transmission` | Tipo de transmisión |
| `Owner` | Número de propietarios anteriores |

El dataset original contaba con **301 registros y 9 variables**.

Después del proceso de limpieza se obtuvieron **299 registros**, eliminando registros duplicados y corrigiendo inconsistencias en los nombres de los vehículos.

# 🔎 Metodología

El proyecto se desarrolló en **tres módulos principales**.

## 🧹 Módulo 1: Exploración y limpieza de datos

En esta primera etapa se realizó una revisión general del dataset para conocer su estructura y calidad.

### Actividades realizadas:

- 📥 Carga del dataset.
- 👀 Exploración de los primeros registros.
- 📋 Revisión de tipos de datos y estructura.
- ❌ Identificación de valores nulos.
- 🔁 Identificación y eliminación de registros duplicados.
- ✏️ Corrección de espacios en los nombres de los vehículos.
- 📊 Revisión de estadísticas descriptivas.

### Resultado

El dataset pasó de:

**301 registros → 299 registros**

Después de la limpieza, no se identificaron valores nulos y se obtuvo una base más consistente para continuar con el análisis.

# 📈 Módulo 2: Análisis exploratorio

En esta etapa se analizaron las principales características estadísticas de los datos y las relaciones entre las variables.

Se utilizaron medidas como:

- Media
- Mediana
- Moda
- Varianza
- Desviación estándar
- Rango
- Correlación

También se analizaron posibles valores atípicos y diferencias entre categorías.

## 💡 Principales hallazgos

### 💰 Relación entre precio actual y precio de venta

Uno de los principales descubrimientos fue la fuerte relación positiva entre:

`Present_Price` ↔ `Selling_Price`

con una correlación aproximada de:

**📌 0,88**

Esto indica que los vehículos con un mayor precio actual tienden a presentar también un mayor precio de venta.

### 🛣️ Relación con el kilometraje

La correlación entre:

`Kms_Driven` ↔ `Selling_Price`

fue aproximadamente:

**📌 0,03**

Lo que representa una relación muy débil dentro de este conjunto de datos.

### 🚘 Tipo de transmisión

También se observaron diferencias en el precio de venta promedio entre vehículos automáticos y manuales.

Los vehículos automáticos presentaron un precio de venta promedio superior al de los vehículos manuales.

Sin embargo, esta diferencia debe interpretarse teniendo en cuenta que los grupos no tienen el mismo número de observaciones.

### ⚠️ Valores atípicos

Se identificaron posibles valores atípicos principalmente en variables como:

- `Selling_Price`
- `Present_Price`
- `Kms_Driven`

Estos valores no fueron eliminados automáticamente, ya que un valor extremo no necesariamente representa un error en los datos.

# 🤖 Módulo 3: Modelamiento predictivo

Después de analizar los datos, se planteó una segunda pregunta:

> 🔮 **¿Podemos predecir el precio de venta utilizando las características del vehículo?**

Para responderla, se utilizaron como variables predictoras:

- `Year`
- `Present_Price`
- `Kms_Driven`
- `Owner`

Y como variable objetivo:

- `Selling_Price`

Los datos se dividieron en:

- 🟢 **80 % para entrenamiento**
- 🔵 **20 % para prueba**

Además, se aplicó estandarización de las variables mediante `StandardScaler`.

# 🧠 Modelos utilizados

Para comparar diferentes alternativas de predicción se evaluaron dos modelos:

## 1️⃣ Regresión lineal y polinomica

Se utilizó `SGDRegressor` como modelo de regresión.

### Resultados:

- **R²:** 0,7195
- **RMSE:** 2,6887

El modelo obtuvo un R² cercano al 72 %, lo que indica un desempeño favorable para explicar la variación del precio de venta en los datos de prueba.

## 2️⃣ Random Forest 🌳

También se evaluó un modelo `RandomForestRegressor` para comparar su desempeño con la regresión.

### Resultados:

- **R²:** 0,4891
- **RMSE:** 3,6287

# 🏆 Comparación de modelos

| Modelo | R² | RMSE |
|---|---:|---:|
| 🥇 Regresión lineal | **0,7195** | **2,6887** |
| Random Forest | 0,4891 | 3,6287 |

Para el **R²**, un valor mayor representa un mejor desempeño.

Para el **RMSE**, un valor menor representa un menor error de predicción.

Por lo tanto, la **regresión lineal obtuvo el mejor resultado** para este conjunto de datos.


# 💡 Conclusiones

A partir del análisis realizado, se pueden destacar las siguientes conclusiones:

- 🔍 La variable `Present_Price` presentó la relación más fuerte con `Selling_Price`, con una correlación aproximada de **0,88**.
- 🛣️ `Kms_Driven` presentó una relación muy débil con el precio de venta, cercana a **0,03**.
- 🚘 Se observaron diferencias en los precios de venta según el tipo de transmisión.
- 🧹 El proceso de limpieza permitió trabajar con una base de **299 registros**.
- 🤖 La **regresión lineal** obtuvo mejores resultados que Random Forest.
- 📊 El modelo de regresión alcanzó un **R² de 0,7195** y un **RMSE de 2,6887**.
- 🧠 La comparación permitió observar que un modelo más complejo no necesariamente genera mejores predicciones.

En conclusión, para este conjunto de datos, la **regresión lineal fue el modelo más adecuado de los evaluados para estimar el precio de venta de los vehículos**.

```text
📦 DataExperience_Vehiculos
│
├── 📄 README.md
├── 📓 proyecto_dataexperience.ipynb
└── 📊 car_data.csv
