# Fase 2: Formulación de Hipótesis

## 1. Introducción
En esta fase se definen las hipótesis que guiarán el análisis estadístico del proyecto. Estas parten de las preguntas clave de la Fase 1 y buscan comprobar, con datos, si ciertas relaciones o diferencias realmente existen en el mercado.

Para cada hipótesis se plantea: Hipótesis nula (H0), Hipótesis alternativa (H1), Justificación, Variables involucradas, Test estadístico

## 2. Hipótesis planteadas

### 🔹 Hipótesis 1: Precios según ubicación

**H0:** El precio promedio por noche es igual en los 5 distritos de Nueva York. 
**H1:** Al menos uno de los distritos tiene un precio promedio significativamente diferente al resto.

**Justificación:**  
La ubicación suele ser uno de los factores más importantes en el precio. Validar esto permite entender si realmente hay zonas más costosas y cómo influye la ubicación en el mercado.

**Variables relacionadas:**
1. `price` (numérica)
2. `neighbourhood_group` (categórica con 5 grupos)

**Test estadístico a aplicar:**
ANOVA de una vía, ya que se comparan medias de más de dos grupos. Si los datos no cumplen los supuestos de normalidad u homogeneidad de varianzas, se usará la alternativa no paramétrica de Kruskal-Wallis.

### 🔹 Hipótesis 2: Precios según tipo de alojamiento

**H0:** El precio promedio por noche es igual entre los distintos tipos de habitación (Entire home/apt, Private room, Shared room).
**H1:** Al menos un tipo de habitación tiene un precio promedio significativamente diferente.

**Justificación:**  
No es lo mismo alquilar una propiedad completa que una habitación. Esta hipótesis permite confirmar qué tanto influye este factor en el precio.

**Variables relacionadas:**
1. `price` (numérica)
2. `room_type` (categórica con 3 grupos)

**Test estadístico a aplicar:**
ANOVA de una vía, con Kruskal-Wallis como alternativa si no se cumplen los supuestos. Si el test es significativo, se aplicará un test post-hoc (Tukey) para identificar entre qué tipos de habitación existen diferencias.


### 🔹 Hipótesis 3: Anfitriones profesionales vs ocasionales

**H0:** No hay diferencia en el número de reseñas entre los anfitriones con una sola propiedad y los que tienen múltiples propiedades.
**H1:** Los anfitriones con múltiples propiedades tienen en promedio un número de reseñas diferente al de los anfitriones ocasionales.

**Justificación:**  
Permite entender si tener más propiedades se relaciona con mejor desempeño dentro de la plataforma.

**Variables relacionadas:**
1. `number_of_reviews` (numérica)
2. `calculated_host_listings_count` (numérica, usada para agrupar en "ocasional" vs "profesional")

**Test estadístico a aplicar:**
T-test de Welch para comparar medias de dos grupos independientes. Si los datos no son normales, se usará la alternativa no paramétrica de Mann-Whitney U.

## 3. Resumen de hipótesis

| # | Hipótesis | Variables | Tipo de análisis | Test |
|---|----------|----------|------------------|------|
| 1 | Diferencias de precio según ubicación | price, neighbourhood_group | Comparación de medias entre múltiples grupos | ANOVA |
| 2 | Diferencias de precio según tipo de alojamiento | price, room_type | Comparación de medias entre múltiples grupos | ANOVA |
| 3 | Diferencias entre anfitriones | number_of_reviews, calculated_host_listings_count | Comparación de medias entre dos grupos | T-test de Welch |

## 4. Nivel de significancia

Para todas las pruebas se utilizará un nivel de significancia de **α = 0.05**. Esto implica que:

- Si el valor p < 0.05, se rechaza la hipótesis nula H0.
- Si el valor p ≥ 0.05, no se cuenta con evidencia suficiente para rechazar H0.

Este criterio permite tomar decisiones basadas en evidencia estadística con un nivel de confianza adecuado.

