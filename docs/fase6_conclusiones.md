# Fase 6: Análisis y Conclusiones

## 1. Resumen ejecutivo

El análisis del mercado de Airbnb en Nueva York (dataset 2019, 48,410 registros) confirma estadísticamente que el precio y la demanda están determinados por tres factores: el distrito geográfico, el tipo de alojamiento y el perfil del anfitrión. Manhattan lidera en precio promedio (\\$172.90/noche), las propiedades completas cuestan casi el triple que las habitaciones compartidas, y los anfitriones profesionales acumulan más reseñas a precios más bajos mediante una estrategia de volumen. Estas conclusiones responden directamente la pregunta de negocio planteada en la Fase 1 y proporcionan una base para decisiones estratégicas de anfitriones y plataforma.

---

## 2. Resultados por hipótesis

| # | Hipótesis | Test | Estadístico | p-valor | Conclusión |
|---|-----------|------|-------------|---------|------------|
| H1 | El precio promedio es igual en los 5 distritos | Kruskal-Wallis | H = 6,942.9 | ≈ 0.0000 | Se rechaza H₀ — existen diferencias significativas de precio entre distritos |
| H2 | El precio promedio es igual entre tipos de alojamiento | Kruskal-Wallis | H = 22,408.1 | ≈ 0.0000 | Se rechaza H₀ — el tipo de alojamiento genera diferencias de precio significativas |
| H3 | No hay diferencia en reseñas entre tipos de anfitrión | Mann-Whitney U | U = 234,786,039 | 1.44e-93 | Se rechaza H₀ — los anfitriones profesionales tienen más reseñas en promedio |

Las tres hipótesis nulas fueron rechazadas con evidencia estadística extremadamente sólida (p ≪ 0.05). Se utilizaron pruebas no paramétricas porque los datos de precio y reseñas no cumplen los supuestos de normalidad ni homocedasticidad.

---

## 3. KPIs — Valores calculados e interpretación

### KPI 1: Precio promedio por distrito

| Distrito | Precio promedio (USD/noche) |
|----------|-----------------------------|
| Manhattan | $172.90 |
| Brooklyn | $115.92 |
| Queens | $94.10 |
| Staten Island | $94.24 |
| Bronx | $83.86 |

**Interpretación:** Manhattan es un 106% más caro que el Bronx. La ubicación es el factor individual de mayor impacto en el precio. Brooklyn se posiciona como la alternativa más atractiva en términos de relación precio-demanda.

---

### KPI 2: Precio promedio por tipo de alojamiento

| Tipo de alojamiento | Precio promedio (USD/noche) |
|---------------------|----------------------------|
| Entire home/apt | $189.10 |
| Private room | $83.39 |
| Shared room | $64.20 |

**Interpretación:** El tipo de alojamiento introduce una brecha de precio de casi 3x entre extremos. El mercado está compuesto mayoritariamente por propiedades completas (51.7%), lo que eleva el precio promedio general del mercado.

---

### KPI 3: Promedio de reseñas por tipo de anfitrión

| Tipo de anfitrión | Reseñas promedio | Precio promedio (USD/noche) |
|-------------------|------------------|-----------------------------|
| Profesional | 28.98 | $127.93 |
| Ocasional | 20.55 | $142.54 |

**Interpretación:** Los anfitriones profesionales acumulan +8.4 reseñas en promedio, pero cobran $14.61 menos por noche. Esto evidencia una estrategia de volumen: mayor ocupación a precios más competitivos. Los ocasionales mantienen precios más altos pero con menor frecuencia de uso.

---

### KPI 4: Nivel de actividad del alojamiento (reseñas mensuales)

Los alojamientos en **Brooklyn** y **Manhattan** presentan la mayor actividad mensual, especialmente en habitaciones privadas. Queens y Staten Island muestran los niveles más bajos de rotación, lo que puede indicar menor demanda relativa o menor visibilidad en la plataforma.

**Interpretación:** La actividad mensual correlaciona con la densidad de visitantes y el atractivo turístico de cada zona. Los barrios con mayor actividad ofrecen mayor seguridad de ingresos recurrentes para el anfitrión.

---

### KPI 6: Ingreso potencial estimado

**Fórmula:** `price × (365 - availability_365)`

| Distrito | Ingreso potencial promedio (USD/año) |
|----------|--------------------------------------|
| Manhattan | Mayor ingreso absoluto |
| Brooklyn | Segunda posición, brecha reducida con Manhattan |
| Queens | Ingreso moderado |
| Staten Island | Ingreso moderado |
| Bronx | Ingreso más bajo |

Barrios con mayor ingreso potencial estimado: principalmente Manhattan y barrios clave de Brooklyn (Williamsburg, Bedford-Stuyvesant).

**Interpretación:** El ingreso potencial combina precio y ocupación estimada. Manhattan lidera en términos absolutos, pero varios barrios de Brooklyn presentan una relación favorable entre precio razonable y alta ocupación, convirtiéndolos en las mejores oportunidades de inversión fuera de Manhattan.

> *Nota: Este KPI es una estimación de techo máximo. Asume que todos los días no disponibles se traducen en ocupación efectiva, lo que no necesariamente ocurre en la realidad.*

---

## 4. Recomendaciones estratégicas

### Para anfitriones

- **Nuevos anfitriones en Manhattan:** iniciar con precios ligeramente por debajo del promedio del barrio para acumular reseñas rápidamente, luego ajustar al alza.
- **Anfitriones ocasionales con habitación privada:** precio objetivo entre $75–$90 para ser competitivos con el promedio del segmento ($83.39).
- **Anfitriones en Queens y Staten Island:** reducir restricciones de estancia mínima para mejorar la conversión; los precios ya son competitivos.
- **Anfitriones con múltiples propiedades:** priorizar ocupación sobre precio — la estrategia de volumen con precios moderados maximiza el ingreso potencial total.

### Para la plataforma Airbnb

- **Programas de visibilidad en Queens y Staten Island:** campañas de marketing específicas para equilibrar la demanda geográfica del mercado.
- **Incentivos escalonados para profesionalización responsable:** fomentar alta calidad de servicio sin concentrar demasiadas propiedades en pocos operadores.
- **Herramientas de pricing dinámico:** los patrones de precio son predecibles y consistentes; recomendaciones de precio en tiempo real optimizarían ingresos y conversión.

---

## 5. Limitaciones

1. **Dataset de 2019 (pre-pandemia):** no refleja el estado actual del mercado ni las regulaciones vigentes en Nueva York.
2. **`availability_365` como proxy:** indica disponibilidad, no ocupación real. El KPI 6 sobreestima el ingreso potencial.
3. **Sin datos de costos:** el ingreso potencial es bruto; no se puede calcular ganancia neta.
4. **Sesgo de selección:** solo listados activos en el momento de la extracción; listados inactivos no están representados.
5. **Clasificación binaria de anfitriones:** la distinción Ocasional/Profesional simplifica el espectro real de operadores.
6. **Análisis transversal:** no permite analizar tendencias temporales ni estacionalidad.

---

## 6. Conclusión general

El proyecto confirma que el mercado de Airbnb en Nueva York presenta patrones claros y estadísticamente significativos. La ubicación, el tipo de alojamiento y el perfil del anfitrión son determinantes clave del precio y la demanda, y su comprensión permite a los anfitriones posicionarse estratégicamente y a la plataforma optimizar sus herramientas de soporte.

El framework CRISP-DM permitió avanzar de manera estructurada desde la comprensión del problema hasta la generación de valor accionable, pasando por hipótesis, preparación de datos, indicadores de desempeño y dashboard. Este ciclo completo demuestra el valor del proceso analítico riguroso aplicado a datos reales de mercado.
