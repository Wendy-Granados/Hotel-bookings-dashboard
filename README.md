# Hotel-bookings-dashboard
Interactive Power BI dashboard for analyzing hotel bookings, cancellations, pricing, guest origin, market segments, and monthly reservation trends.
# Hotel Bookings Dashboard

## 1. Descripción del proyecto

Dashboard desarrollado en Power BI para analizar información de reservas hoteleras, considerando variables relacionadas con cancelaciones, precios, estancias, segmentos de mercado y características de los huéspedes.

El proyecto tiene como objetivo practicar la transformación, modelado y visualización de datos para facilitar el seguimiento de indicadores relacionados con las reservas.

## 2. Objetivos

- Analizar el comportamiento de las reservas y cancelaciones.
- Comparar el precio promedio de las habitaciones por año.
- Identificar los meses con mayor número de cancelaciones y reservas.
- Analizar la duración de las estancias.
- Comparar las reservas de acuerdo con el segmento de mercado.
- Identificar la procedencia de los huéspedes.
- Presentar indicadores de forma interactiva mediante filtros y visualizaciones.

## 3. Herramientas utilizadas

- Power BI Desktop
- Power Query
- DAX

## 4. Fuente de datos

Dataset de reservas hoteleras utilizado con fines de práctica y aprendizaje en análisis y visualización de datos.

La información contiene registros de reservas junto con variables relacionadas con fechas, huéspedes, precios, canales de distribución, segmentos de mercado, habitaciones y estado de la reservación.

## 5. Preparación y limpieza de datos

La limpieza de datos se realizó en Power Query antes de utilizar la información en las visualizaciones.

### 5.1 Revisión inicial

Antes de realizar transformaciones se revisaron:

- Tipos de datos de las columnas.
- Valores nulos y errores.
- Valores en blanco.
- Registros duplicados.
- Valores inconsistentes.
- Valores fuera del contexto esperado para cada variable.
- Formato y consistencia de fechas.
- Columnas necesarias para el análisis.

### 5.2 Tratamiento de valores nulos y en blanco

Un valor nulo o vacío no debe eliminarse automáticamente. Primero se debe determinar qué representa dentro de la variable y si su ausencia afecta el análisis.

La regla de tratamiento depende del significado de la columna:

- **Conservar:** cuando el valor nulo representa una situación válida dentro del negocio o dataset.
- **Reemplazar:** cuando existe una forma confiable de determinar el valor correcto o utilizar una categoría como "No especificado".
- **Eliminar la fila:** cuando la ausencia del dato impide realizar el análisis y el registro deja de ser útil.
- **Eliminar la columna:** cuando la variable presenta una cantidad considerable de datos faltantes y no aporta información relevante al objetivo del dashboard.

En Power Query se puede revisar la cantidad y distribución de valores nulos o vacíos mediante las herramientas de **Calidad de columna**, **Distribución de columna** y **Perfil de columna**.

No se debe aplicar una misma regla de limpieza a todas las columnas; el tratamiento debe depender del significado de cada variable y del objetivo del análisis.

### 5.3 Revisión de consistencia

Se verificó que los valores fueran coherentes con el tipo de información que representa cada campo.

Algunos ejemplos de validaciones:

- Fechas con formato correcto.
- Años y meses correspondientes.
- Cantidades expresadas como valores numéricos.
- Variables categóricas con categorías consistentes.
- Precios almacenados como valores numéricos.
- Valores negativos o cero únicamente cuando tengan sentido para la variable.
- Categorías escritas de forma consistente.

### 5.4 Revisión de duplicados

nSe revisaron registros duplicados para evitar que una misma reserva fuera contabilizada más de una vez.

La eliminación de duplicados debe realizarse considerando las columnas que permitan identificar correctamente un registro, evitando eliminar registros válidos que simplemente tengan valores similares.

### 5.5 Regla general de limpieza

La limpieza de datos debe realizarse de acuerdo con el propósito del dashboard. Antes de modificar un valor se debe responder:

1. ¿Qué representa este dato?
2. ¿Es válido que esté vacío?
3. ¿La ausencia del dato afecta algún indicador?
4. ¿Existe información suficiente para reemplazarlo correctamente?
5. ¿Eliminarlo puede alterar la interpretación del análisis?

El objetivo no es eliminar la mayor cantidad de valores posibles, sino conservar información válida y garantizar que los datos utilizados sean coherentes con las preguntas que busca responder el dashboard.

## 6. Modelo de datos
### 6.1 Tabla principal
<img width="371" height="392" alt="image" src="https://github.com/user-attachments/assets/9ed93c90-e9c9-4349-b9b2-c3232fb08b80" />

**hotel_bookings**

Contiene la información utilizada para el análisis de las reservas.

Principales campos:

- `hotel`
- `is_canceled`
- `lead_time`
- `arrival_date_year`
- `arrival_date_month`
- `arrival_date_week_number`
- `arrival_day_of_month`
- `stays_in_weekend_nights`
- `stays_in_week_nights`
- `adults`
- `children`
- `babies`
- `meal`
- `country`
- `market_segment`
- `distribution_channel`
- `is_repeated_guest`
- `previous_cancellations`
- `previous_bookings_not_canceled`
- `reserved_room_type`
- `booking_changes`
- `deposit_type`
- `agent`
- `company`
- `customer_type`
- `precio_por_noche`
- `required_car_parking_spaces`
- `total_of_special_requests`
- `reservation_status`
- `reservation_status_date`

## 7. Medidas DAX

Las medidas utilizadas en el dashboard se documentan de forma individual en esta sección.

### 7.1 Número de clientes

Número de clientes =
COUNT(hotel_bookings[country])

## 8. Preguntas que responde el dashboard

El dashboard permite analizar el comportamiento de las reservas mediante las siguientes preguntas:

- ¿Cuántas reservas fueron canceladas?
- ¿Cuál es el precio promedio de habitación por noche?
- ¿De qué países provienen los huéspedes?
- ¿Cómo cambia el precio por noche entre los diferentes años?
- ¿Cómo varía el tiempo de estancia?
- ¿Qué meses presentan mayor número de cancelaciones?
- ¿Cómo se distribuyen las reservas por segmento de mercado?
- ¿Qué meses concentran un mayor número de reservas?
- ¿Cómo se distribuyen las reservas según su estatus?

## 9. Filtros

### 9.1 Año

Permite seleccionar el año de llegada para analizar la información correspondiente al periodo seleccionado.

### 9.2 Estatus de reservación

Permite filtrar las reservas de acuerdo con su estado.

## 10. Visualizaciones

### 10.1 Tarjetas KPI

- Número de reservas canceladas.
- Precio promedio de habitación por noche.

### 10.2 ¿De dónde vienen los huéspedes?

**Tipo:** Gráfico de barras agrupadas.

Muestra la procedencia de los huéspedes según el país registrado.

### 10.3 Comparación de precio por noche anual

**Tipo:** Embudo.

Permite comparar el precio por noche entre los diferentes años disponibles.

### 10.4 Tiempo de estancia

**Tipo:** Gráfico de líneas.

Permite visualizar la variación del tiempo de estancia durante el periodo analizado.

### 10.5 Comportamiento mensual

**Tipo:** Gráfico combinado de columnas agrupadas y líneas.

Muestra el comportamiento de las reservas mes a mes para facilitar la comparación entre periodos.

### 10.6 Meses con mayor número de cancelaciones

**Tipo:** Gráfico combinado de columnas agrupadas y líneas.

Permite comparar el número de cancelaciones entre los diferentes meses.

### 10.7 Reservas por segmento de mercado

**Tipo:** Matriz.

Muestra la distribución de las reservas según el segmento de mercado.

### 10.8 Meses más ocupados

**Tipo:** Gráfico de barras 100 % apiladas.

Permite comparar la participación de las reservas entre los diferentes meses.

## 11. Interactividad

El dashboard permite interactuar con la información mediante:

- Filtro por año.
- Filtro por estatus de reservación.
- Selección de elementos dentro de las visualizaciones.
- Actualización dinámica de los indicadores y gráficos relacionados.

## 12. Resultado

![Dashboard Hotel Bookings](https://github.com/user-attachments/assets/ac4c9f67-86d5-4550-8ec3-83fc92917c76)

