# Dashboard Interactivo de Análisis de Delitos - Ciudad de Buenos Aires

## Introducción

Este proyecto desarrolla un dashboard interactivo para el análisis de delitos en la Ciudad Autónoma de Buenos Aires (CABA), implementando un flujo completo de trabajo con datos: adquisición, almacenamiento local y visualización interactiva. El proyecto completo (incluyendo la notebook, scripts y este documento) se encuentra disponible en la siguiente URL de Git: **`https://github.com/mabanchio/PACD-TP2.git`**.

## Datasets Seleccionados y Fuente Pública
Dirección General Estadística Criminal y Mapa del Delito Subsecretaría de Investigación y Estadística Criminal Ministerio de Seguridad: 

Contiene los homicidios, hurtos (sin violencia), lesiones y robos (con violencia) que ocurrieron en el ámbito de la Ciudad de Buenos Aires.

https://data.buenosaires.gob.ar/dataset/delitos

### Tema: Análisis de Delitos en la Ciudad Autónoma de Buenos Aires (CABA)

Este proyecto utiliza **cuatro datasets públicos** del gobierno de la Ciudad de Buenos Aires, que contienen información detallada sobre delitos reportados en la ciudad:

- **2021**: `https://cdn.buenosaires.gob.ar/datosabiertos/datasets/ministerio-de-justicia-y-seguridad/delitos/delitos_2021.csv`
- **2022**: `https://cdn.buenosaires.gob.ar/datosabiertos/datasets/ministerio-de-justicia-y-seguridad/delitos/delitos_2022.csv`
- **2023**: `https://cdn.buenosaires.gob.ar/datosabiertos/datasets/ministerio-de-justicia-y-seguridad/delitos/delitos_2023.csv`
- **2024**: `https://cdn.buenosaires.gob.ar/datosabiertos/datasets/ministerio-de-justicia-y-seguridad/delitos/delitos_2024.csv`

Estos datasets contienen información sobre:
- Tipo y subtipo de delito
- Ubicación geográfica (barrio, comuna, coordenadas)
- Fecha y hora del incidente
- Variables adicionales como uso de arma y uso de moto

## Almacenamiento y Operación de Datos

### Implementación de Base de Datos SQLite

**El proyecto implementa SQLite como base de datos local:** Los datasets se procesan y almacenan en una base de datos SQLite local (`bdd/delitos_caba.sqlite`), cumpliendo con el requisito de base de datos del proyecto. Esta implementación permite:

- **Persistencia de datos**: Los datos se mantienen almacenados entre sesiones
- **Consultas SQL optimizadas**: Uso de consultas SQL para análisis y visualizaciones
- **Escalabilidad**: Manejo eficiente de grandes volúmenes de datos
- **Portabilidad**: Base de datos ligera y autocontenida

### Flujo de Procesamiento de Datos

1. **Descarga automática**: Los datasets se descargan automáticamente desde las URLs oficiales del gobierno de CABA
2. **Carga en DataFrames**: Cada archivo CSV se carga en un DataFrame de Pandas individual
3. **Concatenación**: Los cuatro DataFrames se combinan en un único DataFrame unificado
4. **Limpieza y transformación**: Se aplican transformaciones de datos para normalizar formatos y tipos
5. **Almacenamiento en SQLite**: Los datos procesados se almacenan en la tabla `delitos` de la base de datos SQLite
6. **Consultas SQL**: Todas las visualizaciones se generan mediante consultas SQL a la base de datos

## Pasos para la Ejecución y Visualización del Dashboard

### Prerrequisitos

- Python 3.7 o superior
- Jupyter Notebook o Google Colab
- Las siguientes librerías de Python:
  - pandas
  - numpy
  - plotly
  - matplotlib
  - seaborn

### Instrucciones de Ejecución

1. **Clonar el repositorio**:
   ```bash
   git clone https://github.com/mabanchio/PACD-TP2.git
   cd PACD-TP2
   ```

2. **Abrir la notebook principal**:
   - Abrir `TP_Análisis_de_Datos_Dashboard_Delitos_CABA.ipynb` en Jupyter Notebook o Google Colab

3. **Ejecutar todas las celdas**:
   - Ejecutar las celdas en orden secuencial
   - La notebook descargará automáticamente los datasets
   - Procesará y limpiará los datos
   - Generará los gráficos interactivos

4. **Visualizar el dashboard**:
   - Los gráficos se mostrarán directamente en la notebook
   - Se generará automáticamente el archivo HTML del dashboard completo en `html/dashboard_delitos_caba.html`
   - Abrir el archivo HTML en cualquier navegador web para la visualización interactiva

### Estructura del Proyecto

```
PACD-TP2/
├── TP Análisis de Datos - Dashboard - Delitos CABA.ipynb  # Notebook principal
├── dataset/                                           # Datasets descargados
│   ├── delitos_2021.csv
│   ├── delitos_2022.csv
│   ├── delitos_2023.csv
│   └── delitos_2024.csv
├── bdd/                                               # Base de datos SQLite
│   └── delitos_caba.sqlite
├── html/                                              # Dashboard exportado
│   └── dashboard_delitos_caba.html
└── README.md                                          # Este archivo
```

## Uso de Inteligencia Artificial Generativa (IAG) en el Desarrollo

La **Inteligencia Artificial Generativa (IAG) fue fundamental** y utilizada para los siguientes propósitos clave en el desarrollo de este proyecto:

### 1. Asistencia y Corrección de Código
- **Consulta, optimización y corrección de errores de código** (*debugging*)
- Resolución de problemas de sintaxis y lógica en el procesamiento de datos
- Optimización de funciones de transformación y limpieza de datos
- **Implementación de SQLite**: Desarrollo de la estructura de base de datos y consultas SQL optimizadas

### 2. Implementación de Visualización
- Apoyo en la **implementación del gráfico del mapa de calor** (*heatmap*) interactivo
- Desarrollo de configuraciones avanzadas para gráficos de densidad geográfica
- Implementación de controles interactivos (dropdowns) para filtrado dinámico

### 3. Funcionalidad de Exportación
- Desarrollo de la **funcionalidad de exportación de los gráficos** en formato HTML
- Implementación de métodos para combinar múltiples visualizaciones en un dashboard unificado
- Configuración de opciones de exportación con librerías de JavaScript embebidas

### 4. Estructura de Presentación
- Creación de la **estructura de presentación HTML** utilizada en la exportación final del dashboard
- Desarrollo de estilos CSS responsivos para visualización en diferentes dispositivos
- Implementación de layout en grid para organización óptima de visualizaciones

### 5. Documentación
- **Generación de la documentación del proyecto** (la creación de este mismo archivo `README.md`)
- Estructuración de contenido técnico y explicaciones detalladas
- Formateo y organización de información para máxima claridad y replicabilidad

## Características del Dashboard

El dashboard incluye las siguientes visualizaciones interactivas:

1. **Gráfico de Barras**: Delitos por año y tipo
2. **Treemap**: Distribución de delitos por barrio y tipo
3. **Gráfico de Líneas**: Evolución temporal de delitos por tipo
4. **Mapa de Calor**: Geolocalización de delitos con controles interactivos

Todas las visualizaciones son completamente interactivas y permiten explorar los datos desde múltiples perspectivas.

## Tecnologías Utilizadas

- **Python**: Lenguaje de programación principal
- **SQLite**: Base de datos local para almacenamiento y consultas
- **Pandas**: Manipulación y análisis de datos
- **Plotly**: Visualizaciones interactivas
- **Matplotlib/Seaborn**: Visualizaciones adicionales
- **HTML/CSS**: Dashboard web responsivo
- **Jupyter Notebook**: Entorno de desarrollo

## Autor

Trabajo realizado en el marco de la asignatura **ASIG00202 - Programación Avanzada para Ciencia de Datos** (Universidad de la Ciudad, 2025). 

**Alumno**
- Matias A. Banchio


---

**Nota**: Este proyecto forma parte del Trabajo Práctico del segundo módulo de "Programación Avanzada en Ciencia de Datos" de la Universidad de la Ciudad de Buenos Aires.
