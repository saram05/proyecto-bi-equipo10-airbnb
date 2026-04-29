## 1. Descripción del contexto del dataset

### 1.1 Airbnb como negocio

Airbnb es una plataforma digital fundada en 2008 que conecta a personas que desean alquilar sus propiedades (anfitriones o *hosts*) con viajeros que buscan alojamiento temporal. Opera en más de 220 países y cuenta con más de 7 millones de alojamientos activos a nivel mundial, consolidándose como una alternativa directa a los hoteles tradicionales.

- Airbnb cobra una comisión tanto a los anfitriones (~3%) como a los huéspedes (~14%) por cada reserva realizada.
- Los ingresos de la empresa dependen del volumen y el precio promedio de las reservas.
- El éxito de la plataforma depende de la calidad, diversidad y competitividad de los alojamientos.

### 1.2 Nueva York como mercado

Nueva York es uno de los mercados más representativos y complejos de Airbnb a nivel mundial:

• **Tamaño:** Aproximadamente 49,000 alojamientos activos en 2019.
- **Turismo:** Ña ciudad recibe más de 65 millones de visitantes al año.
- **Geográficamente:** Se divide en 5 distritos (Manhattan, Brooklyn, Queens, Bronx y Staten Island) con realidades socioeconómicas muy distintas.
- **Regulación:** NYC ha implementado restricciones a los alquileres cortos (menos de 30 días), lo que convierte el mercado en altamente competitivo y regulado.
- **Mercado:** Permite análisis robustos sobre precios, demanda y comportamiento de anfitriones.

### 1.3 Descripción del dataset

El dataset utilizado para este análisis contiene información detallada sobre los alojamientos de Airbnb en Nueva York durante el año 2019. Proviene de Inside Airbnb, una iniciativa independiente que recopila y publica datos de la plataforma para fomentar la transparencia del mercado.

| Característica | Detalle |
|--------|------|
| **Nombre** | New York City Airbnb Open Data | 
| **Fuente**   | https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data | 
| **Periodo** | Año 2019 | 
| **Tamaño** | 48,895 filas × 16 columnas | 
| **Unidad de análisis** | Cada fila representa un alojamiento (propiedad ofrecida en Airbnb)| 

### 1.4 Diccionario de variables

El dataset contiene 16 variables que describen aspectos geográficos, características de la propiedad, información del anfitrión y comportamiento de los huéspedes:

| #  | Variable                              | Tipo de Dato | Descripción |
|----|------------------------------------|--------------|-------------|
| 1  | id                                 | Integer      | Identificador único del alojamiento |
| 2  | name                               | Text         | Título del anuncio |
| 3  | host_id                            | Integer      | Identificador único del anfitrión |
| 4  | host_name                          | Text         | Nombre del anfitrión |
| 5  | neighbourhood_group                | Categorical  | Distrito (Manhattan, Brooklyn, Queens, Bronx, Staten Island) |
| 6  | neighbourhood                      | Categorical  | Barrio específico (221 barrios únicos) |
| 7  | latitude                           | Numeric      | Coordenada de latitud |
| 8  | longitude                          | Numeric      | Coordenada de longitud |
| 9  | room_type                          | Categorical  | Tipo de habitación (Entire home/apt, Private room, Shared room) |
| 10 | price                              | Numeric      | Precio por noche (USD) |
| 11 | minimum_nights                     | Numeric      | Mínimo de noches requeridas |
| 12 | number_of_reviews                  | Numeric      | Número total de reseñas |
| 13 | last_review                        | Date         | Fecha de la última reseña |
| 14 | reviews_per_month                  | Numeric      | Promedio de reseñas mensuales |
| 15 | calculated_host_listings_count     | Numeric      | Cantidad de propiedades del anfitrión |
| 16 | availability_365                   | Numeric      | Días disponibles al año |

## 2. Identificación del problema de análisis

### 2.1 Problema de negocio

El crecimiento de Airbnb ha cambiado la forma en que las personas viajan y ofrecen alojamiento, especialmente en ciudades como Nueva York, donde hay una oferta muy amplia. Esto ha hecho que el mercado sea altamente competitivo, y que muchos anfitriones no tengan claro qué factores influyen realmente en el éxito de sus propiedades.

Por eso, surge la siguiente pregunta:

> ¿Qué factores geográficos, de tipo de propiedad y del perfil del anfitrión influyen en el precio y la demanda de los alojamientos en Nueva York?

Responder esto permite usar los datos para tomar mejores decisiones, que es el objetivo principal de un análisis de Business Intelligence.

### 2.2 Relevancia del problema

Este análisis es importante principalmente para dos actores;
Por un lado, los anfitriones, que necesitan definir precios y estrategias con base en datos, y no solo en intuición. Entender el mercado les ayuda a mejorar su oferta y aumentar sus reservas. Por otro lado, Airbnb, que puede usar esta información para entender mejor el comportamiento del mercado, identificar oportunidades y mejorar sus recomendaciones.

Aunque hay otros interesados, este proyecto se enfoca en el mercado y en los anfitriones, porque son quienes pueden tomar acciones directas con los resultados.

### 2.3 Enfoque del análisis

El análisis se centra en tres aspectos clave:

- Cómo se distribuyen los precios según la ubicación  
- Qué tipo de anfitriones existen y cómo se comportan  
- Cómo se relacionan la disponibilidad, la demanda y el precio  

Estos puntos permiten entender el mercado de forma general y servirán como base para el desarrollo del análisis y el dashboard.

## 3. Preguntas clave de análisis

Para guiar el desarrollo del proyecto, se formulan las siguientes preguntas clave, alineadas con el problema de negocio identificado:

### 🔹 Pregunta 1: ¿Cómo varían los precios entre los 5 distritos de NYC y qué tipos de habitación predominan en cada uno?

**Lo que buscamos responder:**
- ¿Manhattan es realmente el borough más caro del mercado?
- ¿En qué distrito predomina el alquiler de casas completas frente a habitaciones privadas?
- ¿Existen barrios con buena relación calidad-precio fuera de Manhattan?

**Variables involucradas:**  
`price`, `neighbourhood_group`, `neighbourhood`, `room_type`

**Valor para la toma de decisiones:**  
Permite a los anfitriones establecer precios competitivos y a Airbnb identificar zonas con oportunidades de crecimiento.

### 🔹 Pregunta 2: ¿Los anfitriones profesionales con múltiples propiedades tienen mejor desempeño en reseñas y precios que los anfitriones ocasionales?

**Lo que buscamos responder:**
- ¿Qué porcentaje del mercado representan los anfitriones profesionales?
- ¿Sus propiedades están concentradas en zonas específicas?
- ¿Generan mayor confianza que los anfitriones ocasionales?

**Variables involucradas:**  
`calculated_host_listings_count`, `number_of_reviews`, `price`, `neighbourhood_group`

**Valor para la toma de decisiones:**  
Permite entender la estructura del mercado y detectar posibles casos de "hoteles fantasma", relevantes para reguladores y la plataforma.

### 🔹 Pregunta 3: ¿Qué relación existe entre la disponibilidad anual, el número de reseñas y el precio de los alojamientos?

**Lo que buscamos responder:**
- ¿Los alojamientos más caros tienen menor disponibilidad? es decir, mayor demanda?
- ¿Existe una correlación clara entre número de reseñas y ocupación?
- ¿Qué características comunes tienen los alojamientos con mejor desempeño?

**Variables involucradas:**  
`availability_365`, `number_of_reviews`, `reviews_per_month`, `price`

**Valor para la toma de decisiones:**  
Ayuda a los anfitriones a entender qué factores están asociados con una alta demanda y cómo optimizar su oferta.