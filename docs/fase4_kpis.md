# Fase 4: Definición de KPIs

## 1. Introducción

En esta fase se definen los indicadores clave de desempeño (KPIs) que permitirán medir y analizar el comportamiento del mercado de Airbnb en Nueva York.

Los KPIs se construyen a partir del dataset preparado en la Fase 3 y están directamente alineados con las hipótesis planteadas en la Fase 2. Su objetivo es transformar los datos en métricas claras que faciliten la toma de decisiones tanto para los anfitriones como para la plataforma.

## 2. KPIs definidos

### 🔹 KPI 1: Precio promedio por distrito

**Definición:**  
Promedio del precio por noche agrupado por distrito (`neighbourhood_group`).

**Fórmula:**  
Precio promedio = promedio de `price`

**Justificación de negocio:**  
Este KPI permite analizar cómo la ubicación influye en el precio, que es uno de los factores centrales del problema planteado en el proyecto. Dado que Nueva York presenta grandes diferencias entre distritos, entender estas variaciones es clave para interpretar la estructura del mercado.

Para los anfitriones, este indicador sirve como referencia para fijar precios competitivos dentro de su zona. Para la plataforma, permite identificar qué zonas concentran mayor valor.

**Relación con hipótesis:**  
Aporta evidencia para la Hipótesis 1, ya que permite observar cómo se distribuyen los precios entre distritos. Mientras el test estadístico indica si existen diferencias, este KPI permite entender cómo esas diferencias responden al factor geográfico, que es uno de los ejes del problema de negocio.

**Interpretación:**  
- Diferencias claras entre distritos confirman que la ubicación es un factor determinante del precio.
- Distritos con precios más altos reflejan mayor disposición a pagar.
- Permite identificar zonas donde ajustar precios o encontrar oportunidades.

### 🔹 KPI 2: Precio promedio por tipo de alojamiento

**Definición:**  
Promedio del precio por noche según el tipo de alojamiento (`room_type`).

**Fórmula:**  
Precio promedio = promedio de `price`

**Justificación de negocio:**  
El tipo de alojamiento representa directamente la propuesta de valor del producto. Este KPI permite analizar cómo este factor influye en el precio, alineándose con el objetivo del proyecto de entender qué variables determinan el valor del mercado.

**Relación con hipótesis:**  
Contribuye a la Hipótesis 2 al permitir observar si el tipo de alojamiento genera diferencias relevantes en el precio. Esto permite evaluar si este factor tiene un impacto real en la fijación de tarifas.

**Interpretación:**  
- Diferencias marcadas indican que el tipo de alojamiento es un factor clave del precio.
- Permite entender qué tipo de oferta captura mayor valor.
- Ayuda a definir estrategias de pricing según el tipo de propiedad.

### 🔹 KPI 3: Promedio de reseñas por tipo de anfitrión

**Definición:**  
Promedio de `number_of_reviews` según el tipo de anfitrión (`host_type`).

**Fórmula:**  
Promedio de reseñas = promedio de `number_of_reviews`

**Justificación de negocio:**  
Las reseñas funcionan como una aproximación a la demanda. Este KPI permite analizar si el perfil del anfitrión influye en el desempeño de los alojamientos, lo cual está directamente relacionado con el objetivo del proyecto.

**Relación con hipótesis:**  
Permite interpretar los resultados de la Hipótesis 3, al mostrar cómo varía la demanda entre anfitriones profesionales y ocasionales. De esta forma, se evalúa si el perfil del anfitrión es un factor relevante en el éxito de un alojamiento.

**Interpretación:**  
- Valores más altos en un grupo indican mayor nivel de actividad o demanda.
- Permite identificar si la profesionalización tiene impacto en el desempeño.
- Aporta evidencia sobre el rol del anfitrión en el mercado.

### 🔹 KPI 4: Nivel de actividad del alojamiento

**Definición:**  
Promedio de reseñas mensuales (`reviews_per_month`).

**Fórmula:**  
Actividad = promedio de `reviews_per_month`

**Justificación de negocio:**  
Este KPI permite medir la dinámica de la demanda en el tiempo, lo cual es fundamental para entender el comportamiento del mercado más allá del precio.

**Relación con hipótesis:**  
Complementa el análisis de la demanda asociado a la Hipótesis 3 y a la pregunta sobre relación entre precio, disponibilidad y demanda. Permite observar si los alojamientos con mayor actividad presentan patrones diferenciados.

**Interpretación:**  
- Valores altos indican mayor rotación y demanda constante.
- Permite identificar segmentos con mayor dinamismo.
- Aporta contexto sobre el comportamiento real del mercado.

### 🔹 KPI 5: Ingreso potencial estimado

**Definición:**  
Estimación del ingreso anual basada en precio y ocupación.

**Fórmula:**  
Ingreso potencial = `price` * (365 - `availability_365`)

**Justificación de negocio:**  
Este KPI integra los dos componentes principales del objetivo del proyecto: precio y demanda. Permite estimar el desempeño económico de los alojamientos y evaluar qué combinaciones de factores generan mejores resultados.

**Relación con hipótesis:**  
Integra los resultados de todas las hipótesis, ya que combina:
- El efecto del precio (Hipótesis 1 y 2)
- El comportamiento de la demanda (Hipótesis 3 y análisis de disponibilidad)

Esto permite analizar el impacto conjunto de los factores identificados.

**Interpretación:**  
- Valores altos indican alojamientos bien posicionados en el mercado.
- Permite identificar oportunidades de maximización de ingresos.
- Resume el efecto combinado de las variables analizadas.

