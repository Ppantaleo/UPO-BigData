# Análisis de Tendencias del Terrorismo

Este documento presenta un análisis breve de las tendencias del terrorismo global basado en el Global Terrorism Database (GTD).
En primer lugar, necesitamos cargar el dataset que se puede hacer de esta forma en R:

```r
library(readr)
gtd <- read_csv("/data/dataset_GTD.csv")

```

Si lo descargas en tu ordenador, debes colocar la ubicación correcta del archivo .csv

## Número de Ataques Terroristas por Año

Para entender cómo ha evolucionado la frecuencia de ataques terroristas a lo largo del tiempo, generamos la siguiente tabla y gráfico.

### Crear dataframe

```r
library(dplyr)

ataques_por_año <- gtd %>%
  group_by(iyear) %>%
  summarise(Num_Attacks = n())

```

### Tabla1: Número de Ataques por Año

La tabla muestra el número de ataques terroristas registrados cada año en el dataset.

```r
# Instala el paquete DT si aún no lo has hecho
if (!requireNamespace("DT", quietly = TRUE)) install.packages("DT")
library(DT)

# Asegúrate de que ataques_por_año está ordenado por año
ataques_por_año <- ataques_por_año %>%
  arrange(iyear)

# Crea la tabla interactiva con DT
tabla_interactiva <- datatable(ataques_por_año, options = list(pageLength = 10, order = list(list(0, 'asc'))),
                               caption = "Número de Ataques Terroristas por Año")

# Guarda la tabla como HTML
archivo_html <- "/src/img/tabla1.html"
saveWidget(tabla_interactiva, archivo_html, selfcontained = TRUE)
```

[Ver la tabla interactiva de ataques por año](/src/img/tabla1.html)


### Gráfico1: Número de Ataques por Año

El gráfico que muestra los datos de la tabla 1

```r
library(ggplot2)

# Suponiendo que ataques_por_año ya está creado y contiene las columnas iyear y Num_Attacks
ggplot(ataques_por_año, aes(x = iyear, y = Num_Attacks)) +
  geom_line() +  # Dibuja la línea
  geom_point() + # Agrega puntos en cada dato
  theme_minimal() + # Utiliza un tema minimalista para el gráfico
  labs(title = "Evolución del Número de Ataques Terroristas por Año",
       x = "Año",
       y = "Número de Ataques",
       caption = "Fuente: Global Terrorism Database")

```
![Evolución del Número de Ataques Terroristas por Año](/src/img/grafico1.png)

## Ataques terroristas por países

Para entender cómo ha evolucionado la frecuencia de ataques terroristas a lo largo del tiempo y en qué paises principalmente, generamos la siguiente tabla y gráfico.

### Crear dataframe

```r
library(dplyr)

ataques_por_pais <- gtd %>%
  group_by(country_txt) %>%
  summarise(Num_Attacks = n()) %>%
  arrange(desc(Num_Attacks))

```

### Tabla2: Ataque terroristas por países

La tabla muestra el número de ataques terroristas registrados cada año en el dataset.

```r
# Crea la tabla interactiva con DT
tabla_interactiva_paises <- datatable(ataques_por_pais, 
                                      options = list(pageLength = 15, 
                                                     autoWidth = TRUE,
                                                     order = list(list(2, 'desc'))), # Ordena descendentemente por Num_Attacks
                                      caption = 'Número de Ataques Terroristas por País')

# Guarda la tabla como HTML
saveWidget(tabla_interactiva_paises, 'src/img/tabla2.html', selfcontained = TRUE)

```

[Ver la tabla interactiva de ataques por paises](/src/img/tabla2.html)


### Gráfico2: Top 10 países más afectados por ataques terroristas

El gráfico que muestra el Top 10 de países más afectados por ataques terroristas

```r
library(ggplot2)

ggplot(ataques_por_pais[1:10,], aes(x = reorder(country_txt, -Num_Attacks), y = Num_Attacks)) +
  geom_bar(stat = "identity") +
  theme_minimal() +
  coord_flip() +
  labs(title = "Top 10 Países Más Afectados por Ataques Terroristas",
       x = "País",
       y = "Número de Ataques")

```
![Top 10 Países Más Afectados por Ataques Terroristas](/src/img/grafico2.png)

## Número de Ataques Terroristas por Año en España

Para entender cómo ha evolucionado la frecuencia de ataques terroristas a lo largo del tiempo en España, generamos la siguiente tabla y gráfico.

### Crear dataframe

```r
library(dplyr)

ataques_espana <- gtd %>%
  filter(country_txt == "Spain") %>%
  group_by(iyear) %>%
  summarise(Num_Attacks = n())

ataques_espana <- ataques_espana %>%
  arrange(iyear)

```

### Tabla3: Número de Ataques por Año en España

La tabla muestra el número de ataques terroristas registrados cada año en el dataset para España.

```r
# Crea la tabla interactiva con DT
tabla_interactiva_espana <- datatable(ataques_espana, 
                                      options = list(pageLength = 5, autoWidth = TRUE),
                                      caption = 'Evolución de Ataques Terroristas en España por Año')

# Guarda la tabla como HTML en la ubicación deseada
ruta_archivo_html <- "C:/Users/Patricio/Documents/GitHub/UPO-BigData/src/img/tabla_interactiva_espana.html"
saveWidget(tabla_interactiva_espana, ruta_archivo_html, selfcontained = TRUE)
```

[Ver la tabla interactiva de ataques por año](/src/img/tabla3.html)


### Gráfico3: Número de Ataques por Año en España

El gráfico que muestra los datos de la tabla 3

```r
library(ggplot2)

ggplot(ataques_espana, aes(x = iyear, y = Num_Attacks)) +
  geom_line(color = "blue", size = 1) +
  geom_point(color = "red", size = 2) +
  theme_minimal() +
  labs(title = "Evolución de Ataques Terroristas en España (1970-2017)",
       x = "Año",
       y = "Número de Ataques",
       caption = "Fuente: Global Terrorism Database")
```
![Evolución del Número de Ataques Terroristas por Año en España](/src/img/grafico3.png)