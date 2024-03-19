# UPO-BigData
Este es un repositorio para el módulo de BigData y visualización de datos de Experto de la UPO.

# Análisis del Global Terrorism Database (GTD) utilizando R

Este proyecto se centra en el análisis del Global Terrorism Database (GTD), una base de datos de acceso abierto que incluye información sobre ataques terroristas en todo el mundo desde 1970 hasta 2017. Mantenida por el Consorcio Nacional para el Estudio del Terrorismo y Respuestas al Terrorismo (START), con sede en la Universidad de Maryland, esta base de datos contiene más de 180,000 incidentes terroristas, proporcionando una visión integral de las tendencias globales del terrorismo.

## Contexto

El GTD ofrece datos detallados sobre ubicaciones geográficas, tácticas, perpetradores, objetivos y resultados de ataques terroristas, basándose en artículos de medios no clasificados. Esta rica fuente de datos permite una exploración profunda de las tendencias del terrorismo, los cambios a lo largo del tiempo y las diferencias regionales, ayudando a entender mejor el panorama global del terrorismo y su impacto en España.

## Objetivos del Proyecto

- Explorar las tendencias del terrorismo global desde 1970 hasta 2017.
- Identificar los países y regiones más afectados por el terrorismo.
- Evidenciar los ataques presentes por año en España.
- Contribuir al desarrollo de investigaciones en base a este conjunto de datos

## Metodología

Este análisis se realiza utilizando R y RStudio, aprovechando paquetes como `dplyr`, `ggplot2`, y `leaflet` para manipulación de datos, visualización y mapeo geoespacial, respectivamente. La metodología incluye:

1. **Limpieza y Preparación de Datos**: Selección de variables relevantes, manejo de valores faltantes y corrección de errores.
2. **Análisis Exploratorio de Datos (AED)**: Estadísticas descriptivas y visualizaciones iniciales para comprender la distribución de los datos.
3. **Visualización Avanzada**: Creación de gráficos y mapas detallados para explorar las tendencias y patrones del terrorismo.

### Nota Metodológica
Para la creación de los códigos R se utilizó como apoyo ChatGPT 4. En todo caso, fueron corroborados, modificados y adaptados según su respuesta en R Studio 2023.12.1 para Windows.

## Estructura del Repositorio

- `/src`: Contiene scripts de R para el análisis y visualización de datos en la carpeta `/img`. Para visualizar correctamente los archivos `html` exportados en R, se recomienda descargar los mismos y ejecutarlos en local.
- `/data`: Directorio para los datasets utilizados y generados durante el análisis. Inicialmente se pensó cargar el dataset en formato CSV pero por su tamaño solo se colocó el enlace para redirigir al sitio oficial para su descarga. Por defecto, en todo código se toma /data/dataset_GTD.csv como el dataset existente que deberá descargar, renombrar y colocar en esta carpeta para que los códigos de /src sean rápidamente funcionales. 
- `/docs`: Documentación adicional, incluyendo el GTD Codebook.
- `README.md`: Descripción del proyecto, metodología, estructura del repositorio y cómo ejecutar los scripts.

## Cómo Utilizar

Para reproducir este análisis, siga estos pasos:

1. Clonar el repositorio a su máquina local.
2. Abrir RStudio y establecer el directorio del repositorio clonado como su directorio de trabajo.
3. Instalar los paquetes de R necesarios ejecutando `install.packages(c("dplyr", "ggplot2", "leaflet", "readr", "tidyr", "DT", "plotly", "highcharter", "stringr", "janitor", "lubridate", "sf"))`.
4. Descargar y reemplazar dataset dataset_GTD.csv según indicaciones en `/data/Data Set.md`
4. Ejecutar los scripts en el directorio `/src` en orden.

## Contacto

Para preguntas o colaboraciones, por favor, contacte al autor del proyecto a través de patriciopantaleo@gmail.com.

