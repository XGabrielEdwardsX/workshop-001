# Workshop - 001: Data Engineer

## 📌 Introducción
Este workshop es un ejercicio real de una entrevista de trabajo, proporcionando una mejor comprensión del proceso de reclutamiento. Además, puede ser subido a GitHub como parte de un portafolio profesional.

## 🎯 Objetivo del Proyecto
El objetivo principal es demostrar conocimientos en gestión de datos y visualización. Se proporcionará un archivo CSV con datos de candidatos que participaron en procesos de selección. La meta es realizar análisis, manipulación de datos y visualización mediante gráficos.

## 📋 Requerimientos
1. **Migración de Datos**: Se debe crear una aplicación para migrar los datos del archivo CSV a una base de datos relacional.
2. **Visualización de Datos**: Los reportes y gráficos deben obtenerse a partir de la base de datos, no directamente desde el archivo CSV.

## 📂 Conjunto de Datos
Se proporciona un conjunto de datos con 50,000 registros sobre candidatos. Los campos clave incluyen:

- **First Name**
- **Last Name** 
- **Email** 
- **Country** 
- **Application Date** 
- **Yoe** (Years of Experience)
- **Seniority** 
- **Technology** 
- **Code Challenge Score** 
- **Technical Interview** 

### 🔍 Criterio de Contratación
Un candidato se considera **contratado** si tiene un puntaje mayor o igual a **7** tanto en el **Code Challenge Score** como en el **Technical Interview**.

## 📊 Visualizaciones Esperadas
- **Contrataciones por Tecnología** (Gráfico de pastel)
- **Contrataciones por Año** (Gráfico de barras horizontal)
- **Contrataciones por Nivel de Experiencia** (Gráfico de barras)
- **Contrataciones por País a lo largo de los años** (Gráfico de líneas múltiples para **USA, Brasil, Colombia y Ecuador**)

---

## 🛠 Pasos para realizar el proyecto

### 1️⃣ Programas y Librerías utilizadas
Para desarrollar este proyecto, se utilizaron las siguientes herramientas y librerías:

| Herramienta / Librería | Descripción | Enlace |
|------------------------|-------------|--------|
| **[Python](https://www.python.org/)** | Lenguaje de programación utilizado para el procesamiento de datos. | 🔗 [Documentación](https://docs.python.org/3/) |
| **[MySQL Workbench](https://www.mysql.com/products/workbench/)** | Interfaz gráfica para trabajar con bases de datos MySQL. | 🔗 [Documentación](https://dev.mysql.com/doc/workbench/en/) |
| **[MySQL Community Server](https://dev.mysql.com/downloads/mysql/)** | Sistema de gestión de bases de datos relacional utilizado para almacenar los datos. | 🔗 [Documentación](https://dev.mysql.com/doc/refman/8.0/en/) |
| **[Visual Studio Code](https://code.visualstudio.com/)** | Editor de código utilizado para el desarrollo del proyecto. | 🔗 [Documentación](https://code.visualstudio.com/docs) |
| **[Git](https://git-scm.com/)** | Sistema de control de versiones utilizado para el manejo del código. | 🔗 [Documentación](https://git-scm.com/doc) |
| **[Jupyter Notebook](https://jupyter.org/)** | Entorno interactivo para ejecutar código Python y visualizar datos. | 🔗 [Documentación](https://jupyter-notebook.readthedocs.io/en/stable/) |
| **[Pandas](https://pandas.pydata.org/)** | Librería para la manipulación y análisis de datos en Python. | 🔗 [Documentación](https://pandas.pydata.org/docs/) |
| **[SQLAlchemy](https://www.sqlalchemy.org/)** | Toolkit SQL para manejar bases de datos de forma eficiente. | 🔗 [Documentación](https://docs.sqlalchemy.org/en/20/) |

---

## 🛠 Configuración del Ambiente

### ✅ Clonar el repositorio
Abre la terminal y ejecuta el siguiente comando para clonar el repositorio:

```bash
git clone https://github.com/XGabrielEdwardsX/workshop-001
```

Luego, accede al directorio del proyecto:

```bash
cd workshop
```

### ✅ Crear y activar el entorno virtual
Para mantener un entorno limpio y evitar conflictos de dependencias, se recomienda utilizar un entorno virtual en Python. En este caso, el entorno se llamará `workshop`.

#### 🔹 En macOS/Linux:
```bash
python -m venv workshop
source workshop/bin/activate
```

#### 🔹 En Windows (CMD o PowerShell):
```bash
python -m venv workshop
workshop\Scripts\activate
```

Una vez activado el entorno virtual, la terminal mostrará algo como:
```
(workshop) $
```
Esto indica que el entorno virtual está activo.

### ✅ Instalar las dependencias
Dentro del entorno virtual `workshop`, instala las librerías necesarias para el proyecto:

```bash
pip install pandas sqlalchemy mysql-connector-python jupyter matplotlib seaborn
```

Si en el futuro necesitas agregar más librerías, puedes hacerlo usando:

```bash
pip install <nombre_de_la_librería>
```

Para asegurarte de que las dependencias quedan registradas en el proyecto, ejecuta:

```bash
pip freeze > requirements.txt
```

Esto generará un archivo `requirements.txt`, el cual puede ser utilizado para instalar todas las dependencias en otro entorno con:

```bash
pip install -r requirements.txt
```

### ✅ Uso de Jupyter Notebook en Visual Studio Code
Si utilizas **Visual Studio Code**, instala la extensión oficial de **Jupyter** desde el marketplace de VS Code. Una vez instalada, puedes abrir archivos `.ipynb` y ejecutarlos directamente en el entorno interactivo.

Para ejecutar Jupyter en Visual Studio Code:
1. Abre **Visual Studio Code**.
2. Instala la extensión de **Jupyter** si aún no lo has hecho.
3. Abre cualquier archivo `.ipynb` y asegúrate de que el kernel seleccionado sea el del entorno `workshop`.
4. Usa los comandos disponibles para ejecutar celdas y visualizar los resultados.

---

## 📂 Estructura del Proyecto

Este proyecto sigue una organización clara para facilitar su mantenimiento y escalabilidad. A continuación, se describe la estructura y la función de cada carpeta y archivo:

| **Estructura**          | **Descripción** |
|-------------------------|----------------|
| `csv/`                 | Contiene los archivos CSV utilizados en el proyecto, incluyendo los datos originales (`candidates.csv`) y los datos limpiados (`candidates_cleaned.csv`). |
| `db_folder/`           | Contiene los archivos necesarios para la conexión con la base de datos. |
| ├── `db.py`            | Módulo que maneja la conexión a la base de datos MySQL. |
| ├── `__init__.py`      | Permite que `db_folder` pueda ser importado como un módulo. |
| `images/`              | Contiene imágenes utilizadas en la documentación, como diagramas y capturas de pantalla. |
| `notebooks/`           | Contiene los notebooks de Jupyter utilizados en el flujo de trabajo del proyecto. |
| ├── `readData-001.ipynb` | Notebook para la lectura y exploración de datos desde el archivo CSV. |
| ├── `cleanData-002.ipynb` | Notebook para la limpieza y transformación de los datos antes de la migración. |
| ├── `dataMigration-003.ipynb` | Notebook para la migración de los datos a la base de datos MySQL. |
| ├── `reporting.ipynb`  | Notebook para la generación de reportes y visualización de datos. |
| `workshop/`            | Carpeta que contiene la configuración del ambiente. |
| `workshopFile/`        | Carpeta que tiene el PDF DEL pryecto. |
| `.gitignore`           | Archivo para ignorar archivos innecesarios en Git. |
| `README.md`            | Documentación principal del proyecto. |
| `requirements.txt`     | Lista de dependencias necesarias para ejecutar el proyecto. |

---

## 🗄 Configuración de la Base de Datos

Antes de iniciar el flujo de trabajo, es necesario configurar la conexión a la base de datos. Para ello, el proyecto incluye los siguientes archivos:

Tenemos una carpeta llamada db_folder que contiene lo siguiente:

### 📂 `db.py` - Módulo de Conexión a MySQL
- Este archivo define la función `get_connection()`, que establece una conexión con MySQL utilizando **mysql-connector**.
- Los parámetros de conexión (host, usuario, contraseña y base de datos) se obtienen de las variables de entorno para mayor seguridad.
- Si las variables de entorno no están definidas, se utilizan valores por defecto:
  - **Host**: `localhost`
  - **Usuario**: `root`
  - **Contraseña**: `root`
  - **Base de datos**: `workshop_001`

**Código principal en `db.py`:**
```python
import os
import mysql.connector

def get_connection():
    return mysql.connector.connect(
        host=os.getenv("DB_HOST", "localhost"),
        user=os.getenv("DB_USER", "root"),
        password=os.getenv("DB_PASSWORD", "root"),
        database=os.getenv("DB_NAME", "workshop_001")
    )
```
- Este módulo se utilizará en otros scripts para acceder a la base de datos sin necesidad de reescribir la configuración.

### 📂 `__init__.py` - Inicialización del Módulo
- Este archivo permite que la carpeta donde está ubicada la base de datos sea tratada como un **paquete de Python**.
- Importa la función `get_connection()` de `db.py` para poder importarlo en el notebook de migración

**Código en `__init__.py`:**
```python
from .db import get_connection
```

---

## 🔄 Flujo de Trabajo del Proyecto

**A continuación, se explica cada notebook utilizado para la realización algunos análisis:**

1️⃣ **`readData-001.ipynb` - Lectura del Archivo CSV**
   - **Propósito**: Leer y comprender el conjunto de datos original.
   - **Tareas**:
     - Identificar valores nulos y analiza los tipos de datos.

2️⃣ **`csvMigrationToDatabase-002.ipynb` - Limpieza y Transformación de Datos**
   - **Propósito**: Preparar los datos para su uso en la base de datos.
   - **Tareas**:
     - Enviar el csv a una base de datos llamada workshop_001 en una tabla llamada "candidates" en MySQL con 
      Se migran los datos limpios a la misma base de datos, pero en una tabla diferente llamada candidatos_limpios

3️⃣ **`cleanAndTransform-003.ipynb` - Limpieza y transformación**
   - **Propósito**: Insertar los datos en la base de datos MySQL.
   - **Tareas**:
     - Utilizar sqlAlchemy para empezar a manipular las columnas
     - Se convierte la columna application_date a datetime ya que anteriormente era tipo object
     - Se crean 2 columnas llamadas Score que depende de los dos scores que se dan en el csv
     (Code_challenge_score and Tecnhical_interview_score) para determinar si un candidato es contrado o no
     - El paso anterior da lugar a crear una columna hired, que es una booleana que determina si un 
     candidato fue contratado (1) o si no fue contratado (0)

4️⃣ **`reporting.ipynb` - Análisis y Visualización de Datos**
   - **Propósito**: Generar gráficos y reportes a partir de la base de datos.
   - **Tareas**:
     - Conexión a la base de datos y consulta de los datos contratados.
     - Generación de gráficos con **Matplotlib** y **Seaborn**:
       - **Contrataciones por Tecnología** (gráfico de pastel).
       - **Contrataciones por Año** (gráfico de barras horizontal).
       - **Contrataciones por Nivel de Experiencia** (gráfico de barras).
       - **Contrataciones por País a lo largo de los años** (gráfico de líneas múltiples).
       - **Entre otros gráficos**
---

### Conclusions

The analysis of hiring trends reveals several key insights:  

1. **Game Development and DevOps Dominate**  
   - These two fields have significantly higher hiring rates compared to other tech areas.  

2. **Low Hiring Probability**  
   - Only **13.4% of candidates** successfully pass the evaluation process, indicating a highly selective hiring approach.  

3. **Hiring Decline in 2022**  
   - A nearly **50% drop** in recruitment occurred in 2022, possibly due to technological advancements or external factors affecting candidate quality.  

4. **Entry-Level Positions are Preferred**  
   - **Interns and Trainees** are hired more frequently than Mid-Level or Senior professionals, suggesting a focus on training new talent.  

5. **United States’ Hiring Surge in 2021**  
   - The **U.S. overtook other countries in hiring** that year, while Ecuador struggled to recover.  

Overall, the data indicates a **highly competitive and selective hiring environment**, with shifts in demand based on technological advancements and market trends.



