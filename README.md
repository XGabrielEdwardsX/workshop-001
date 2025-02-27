# Workshop - 001: Data Engineer

## 📌 Introduction
This workshop is a real exercise from a job interview, providing a better understanding of the recruitment process. Additionally, it can be uploaded to GitHub as part of a professional portfolio.

## 🎯 Project Objective
The main objective is to demonstrate knowledge in data management and visualization. A CSV file with data from candidates who participated in selection processes will be provided. The goal is to perform data analysis, manipulation, and visualization through graphs.

## 📋 Requirements
1. **Data Migration**: An application must be created to migrate data from the CSV file to a relational database.
2. **Data Visualization**: Reports and graphs must be generated from the database, not directly from the CSV file.

## 📂 Dataset
A dataset with 50,000 candidate records is provided. Key fields include:

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

### 🔍 Hiring Criteria
A candidate is considered **hired** if they have a score greater than or equal to **7** in both the **Code Challenge Score** and the **Technical Interview**.

## 📊 Expected Visualizations
- **Hires by Technology** (Pie Chart)
- **Hires by Year** (Horizontal Bar Chart)
- **Hires by Experience Level** (Bar Chart)
- **Hires by Country Over the Years** (Multi-line Chart for **USA, Brazil, Colombia, and Ecuador**)

---

## 🛠 Steps to Complete the Project

### 1️⃣ Programs and Libraries Used
The following tools and libraries were used to develop this project:

| Tool / Library | Description | Link |
|------------------------|-------------|--------|
| **[Python](https://www.python.org/)** | Programming language used for data processing. | 🔗 [Documentation](https://docs.python.org/3/) |
| **[MySQL Workbench](https://www.mysql.com/products/workbench/)** | Graphical interface for working with MySQL databases. | 🔗 [Documentation](https://dev.mysql.com/doc/workbench/en/) |
| **[MySQL Community Server](https://dev.mysql.com/downloads/mysql/)** | Relational database management system used for data storage. | 🔗 [Documentation](https://dev.mysql.com/doc/refman/8.0/en/) |
| **[Visual Studio Code](https://code.visualstudio.com/)** | Code editor used for project development. | 🔗 [Documentation](https://code.visualstudio.com/docs) |
| **[Git](https://git-scm.com/)** | Version control system used for code management. | 🔗 [Documentation](https://git-scm.com/doc) |
| **[Jupyter Notebook](https://jupyter.org/)** | Interactive environment for running Python code and visualizing data. | 🔗 [Documentation](https://jupyter-notebook.readthedocs.io/en/stable/) |
| **[Pandas](https://pandas.pydata.org/)** | Library for data manipulation and analysis in Python. | 🔗 [Documentation](https://pandas.pydata.org/docs/) |
| **[SQLAlchemy](https://www.sqlalchemy.org/)** | SQL toolkit for efficiently handling databases. | 🔗 [Documentation](https://docs.sqlalchemy.org/en/20/) |

---

## 🛠 Environment Setup

### ✅ Clone the Repository
Open the terminal and run the following command to clone the repository:

```bash
git clone https://github.com/XGabrielEdwardsX/workshop-001
```

Then, access the project directory:

```bash
cd workshop
```

### ✅ Create and Activate the Virtual Environment
To maintain a clean environment and avoid dependency conflicts, it is recommended to use a virtual environment in Python. In this case, the environment will be called `workshop`.

#### 🔹 On macOS/Linux:
```bash
python -m venv workshop
source workshop/bin/activate
```

#### 🔹 On Windows (CMD or PowerShell):
```bash
python -m venv workshop
workshop\Scripts\activate
```

Once the virtual environment is activated, the terminal will display something like:
```
(workshop) $
```
This indicates that the virtual environment is active.

### ✅ Install Dependencies
Within the `workshop` virtual environment, install the necessary libraries for the project:

```bash
pip install pandas sqlalchemy mysql-connector-python jupyter matplotlib seaborn
```

If you need to add more libraries in the future, you can do so using:

```bash
pip install <library_name>
```

To ensure dependencies are recorded in the project, execute:

```bash
pip freeze > requirements.txt
```

This will generate a `requirements.txt` file, which can be used to install all dependencies in another environment with:

```bash
pip install -r requirements.txt
```

### ✅ Using Jupyter Notebook in Visual Studio Code
If you use **Visual Studio Code**, install the official **Jupyter** extension from the VS Code marketplace. Once installed, you can open `.ipynb` files and run them directly in the interactive environment.

To run Jupyter in Visual Studio Code:
1. Open **Visual Studio Code**.
2. Install the **Jupyter** extension if you haven't already.
3. Open any `.ipynb` file and ensure the selected kernel is the `workshop` environment.
   ![image](https://github.com/user-attachments/assets/441197d4-8922-43e5-acd9-b75d8c183d76)
4. Use the available commands to run cells and visualize results.

---

## 📂 Project Structure

This project follows a clear organization to facilitate maintenance and scalability. The structure and function of each folder and file are described below:

| **Structure** | **Description** |
|-------------------------|----------------|
| `csv/` | Contains the CSV files used in the project, including the original data (`candidates.csv`) and the cleaned data (`candidates_cleaned.csv`). |
| `db_folder/` | Contains files necessary for database connection. |
| ├── `db.py` | Module handling the connection to the MySQL database. |
| ├── `__init__.py` | Allows `db_folder` to be imported as a module. |
| `notebooks/` | Contains Jupyter notebooks used in the project's workflow. |
| ├── `readData-001.ipynb` | Notebook for reading and exploring data from the CSV file. |
| ├── `cleanData-002.ipynb` | Notebook for cleaning and transforming data before migration. |
| ├── `dataMigration-003.ipynb` | Notebook for migrating data to the MySQL database. |
| ├── `reporting.ipynb` | Notebook for generating reports and visualizing data. |
| `workshopFile/` | Folder containing the project PDF. |
| `.gitignore` | File to ignore unnecessary files in Git. |
| `README.md` | Main project documentation. |
| `requirements.txt` | List of dependencies needed to run the project. |

---

Below is the missing section of the README translated into English:

---

## 🗄 Database Configuration

Before starting the workflow, it is necessary to configure the connection to the database. To do this, the project includes the following files:

We have a folder named **db_folder** that contains the following:

### 📂 `db.py` - MySQL Connection Module
- This file defines the function `get_connection()`, which establishes a connection with MySQL using **mysql-connector**.
- The connection parameters (host, user, password, and database) are obtained from environment variables for added security.
- If the environment variables are not defined, default values are used:
  - **Host**: `localhost`
  - **User**: `root`
  - **Password**: `root`
  - **Database**: `workshop_001`

**Main code in `db.py`:**
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
- This module will be used in other scripts to access the database without needing to rewrite the configuration.

### 📂 `__init__.py` - Module Initialization
- This file allows the folder containing the database connection code to be treated as a **Python package**.
- It imports the `get_connection()` function from `db.py` so that it can be imported in the migration notebook.

**Code in `__init__.py`:**
```python
from .db import get_connection
```

---

## 🔄 Project Workflow

**Below is an explanation of each notebook used for performing various analyses:**

1️⃣ **`readData-001.ipynb` - Reading the CSV File**
   - **Purpose**: To read and understand the original dataset.
   - **Tasks**:
     - Loads the `candidates.csv` file using **Pandas**.
     - Displays the first few rows and analyzes the columns.
     - Identifies missing values and examines data types.

2️⃣ **`cleanData-002.ipynb` - Data Cleaning and Transformation**
   - **Purpose**: To prepare the data for use in the database.
   - **Tasks**:
     - Converts the **Application Date** column to `datetime` type.
     - Creates a new column **Score**, based on the candidates' scores.
     - Generates the **Hired** column, which indicates whether a candidate was hired.
     - Abbreviates country names to 3-letter codes using **pycountry**.
     - Saves the cleaned data in `candidates_cleaned.csv`.

3️⃣ **`dataMigration-003.ipynb` - Data Migration to MySQL**
   - **Purpose**: To insert the data into the MySQL database.
   - **Tasks**:
     - Creates the database in MySQL Workbench, naming it: `workshop_001`
     - Connects to MySQL using **SQLAlchemy**.
     - Creates the `candidates` table.
     - Inserts the cleaned data into the database.

4️⃣ **`reporting.ipynb` - Data Analysis and Visualization**
   - **Purpose**: To generate charts and reports from the database.
   - **Tasks**:
     - Connects to the database and queries the hired candidates.
     - Generates charts using **Matplotlib** and **Seaborn**:
       - **Hires by Technology** (pie chart).
       - **Hires by Year** (horizontal bar chart).
       - **Hires by Experience Level** (bar chart).
       - **Hires by Country Over the Years** (multi-line chart).

### insights

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
