# Fase 3: Preparación y modelado de datos

## 1. Introducción

En esta fase se lleva a cabo la preparación del dataset que será utilizado en el análisis del proyecto de Business Intelligence. El objetivo principal es garantizar que los datos sean consistentes, confiables y adecuados para responder a las hipótesis planteadas en la fase anterior.

La calidad de los datos es un factor crítico, ya que cualquier error, inconsistencia o valor atípico puede afectar directamente los resultados del análisis. Por esta razón, se realizan procesos de limpieza, transformación y selección de variables, además de estructurar la información de manera que facilite su análisis y visualización en etapas posteriores.

## 2. Exploración inicial del dataset

Antes de realizar cualquier transformación, se llevó a cabo una exploración inicial con el fin de comprender la estructura y calidad de los datos. El dataset contiene información sobre aproximadamente 48,895 alojamientos en la ciudad de Nueva York, incluyendo variables relacionadas con precio, ubicación, tipo de alojamiento, actividad del anfitrión y nivel de demanda.

Durante esta etapa se identificaron:

1. Presencia de valores nulos en algunas variables, especialmente en `reviews_per_month`.
2. Variables de tipo identificador que no aportan valor analítico.
3. Distribuciones con alta dispersión, particularmente en la variable `price`.
4. Posibles valores extremos (outliers) que pueden afectar el análisis.

## 3. Limpieza de datos

Con base en la exploración inicial, se realizaron las siguientes acciones de limpieza:

### 3.1 Eliminación de duplicados
Se eliminaron registros duplicados para evitar sesgos en el análisis. La presencia de duplicados puede generar una sobre-representación de ciertos alojamientos y afectar métricas como promedios o conteos.

### 3.2 Tratamiento de valores nulos
Se identificaron valores nulos en la variable `reviews_per_month`. Estos fueron reemplazados por 0, bajo el supuesto de que corresponden a alojamientos sin actividad reciente o sin reseñas registradas en el periodo analizado.

### 3.3 Eliminación de variables no relevantes
Se eliminaron variables que no aportan valor al análisis, como:
- `id`
- `host_name`

Estas variables cumplen funciones de identificación, pero no contribuyen a explicar el comportamiento del mercado ni a responder las hipótesis planteadas.

## 4. Transformación de datos

Con el objetivo de enriquecer el análisis, se realizaron transformaciones sobre algunas variables clave.

### 4.1 Clasificación del tipo de anfitrión
Se creó una nueva variable denominada `host_type`, que clasifica a los anfitriones en dos categorías:

- **Ocasional:** anfitriones con una sola propiedad.
- **Profesional:** anfitriones con más de una propiedad.

Esta transformación permite analizar el impacto del nivel de experiencia o escala del anfitrión en variables como precio y demanda.

### 4.2 Conversión de tipos de datos
La variable `last_review` fue convertida a formato de fecha, lo que permite su uso en análisis temporales y mejora la consistencia del dataset.

## 5. Tratamiento de outliers

Durante la exploración se identificó que la variable `price` presenta una distribución altamente sesgada, con valores extremos significativamente superiores al promedio.

Para mitigar este efecto, se decidió eliminar los valores por encima del percentil 99 de la variable `price`. Esta técnica permite:

1. Reducir el impacto de valores atípicos extremos.
2. Mantener la representatividad del dataset.
3. Mejorar la interpretación de los resultados.

## 6. Selección de variables

A partir del dataset original, se realizó una selección de variables basada en su relevancia para las hipótesis planteadas en la Fase 2. Las variables seleccionadas fueron:

### Variables relacionadas con precio
- `price`

### Variables geográficas
- `neighbourhood_group`
- `neighbourhood`

### Variables del tipo de alojamiento
- `room_type`

### Variables de demanda
- `number_of_reviews`
- `reviews_per_month`

### Variables de disponibilidad
- `availability_365`

### Variables del perfil del anfitrión
- `host_type`

## 7. Definición de dimensiones y métricas

Desde una perspectiva de Business Intelligence, es fundamental diferenciar entre dimensiones y métricas para facilitar el análisis y la construcción de dashboards.

### Dimensiones
Las dimensiones corresponden a variables categóricas que permiten segmentar la información:

- `neighbourhood_group`
- `neighbourhood`
- `room_type`
- `host_type`

### Métricas
Las métricas corresponden a variables numéricas que pueden ser agregadas:

- `price`
- `number_of_reviews`
- `reviews_per_month`
- `availability_365`

## 8. Estructura final del dataset

El dataset resultante presenta una estructura tabular optimizada para análisis:

- Cada fila representa un alojamiento.
- Cada columna representa una variable relevante.
