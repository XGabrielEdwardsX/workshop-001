# WORKSHOP_001

# 📊 Hiring Process ETL Pipeline & Analysis
An end-to-end data engineering project to analyze hiring trends from 50,000 candidate records using Python, MySQL, and Jupyter Notebooks.

All the instructions can be found in **workshopFile/Workshop -001 Data engineer.pdf**

# 📂 Repository Structure
```markdown
workshop/
├── csv/
│   └── candidates.csv         # Raw dataset
├── db_folder/
│   ├── __pycache__
│   ├── __init__.py
│   └── db.py                 # Database-related scripts
├── images/
│   └── images.png            # Image files
├── notebooks/
│   ├── cleanAndTransform-003.ipynb    # Data cleaning and transformation
│   ├── csvMigrationToDatabase-002.ipynb  # CSV to database migration
│   ├── readData-001.ipynb             # Initial data reading
│   └── reporting-004.ipynb            # Reporting and analysis
├── workshop/
│   └── workshop-001 Data engineer.pdf # Workshop documentation
├── .gitignore
├── README.md                 # You are here 📍
└── requirements.txt          # Python dependencies
```

### We have a CSV file called `candidates.csv` which we will analyze using the following technologies

## 🛠️ Tech Stack
### Core Technologies
| Category       | Tools                  |
|----------------|------------------------|
| Languages      | Python                |
| Database       | MySQL                 |
| Data Tools     | Pandas, NumPy, SQLAlchemy |
| Visualization  | Matplotlib, Seaborn   |
| Environment    | Jupyter Notebook, Virtual Environments |

### Key Libraries
- `pandas`          # Data manipulation
- `SQLAlchemy`      # Database ORM
- `pycountry`       # Country code conversion
- `matplotlib`      # Visualization
- `mysql-connector-python`  # MySQL integration

## 🚀 Quick Start Guide
### 1. Environment Setup
```bash
# Create and activate virtual environment
python -m venv workshop
source workshop/bin/activate      # Linux/macOS
.\workshop\Scripts\activate       # Windows

# Install dependencies
pip install -r requirements.txt
```

### 2. Database Configuration
1. Start MySQL server
2. Create database:
   ```sql
   CREATE DATABASE workshop_001;
   ```
3. Update credentials in `db_folder/db.py`:
   ```python
   # Default configuration:
   host="localhost",
   user="root",
   password="root",
   database="workshop_001"
   ```

### 3. Data Import
Place `candidates.csv` in the `/csv` directory.

## 🔄 Workflow Pipeline
### 1. Data Exploration (`readData-001.ipynb`)
- Verify dataset integrity
- Confirm data types (10 strings, 3 integers)
- Check for null/duplicate values

### 2. Database Migration (`csvMigrationToDatabase-002.ipynb`)
#### Key Operations:
- Creates `raw_candidates` table
- Imports 50k records to MySQL
- Schema: `first_name`, `last_name`, `email`, `application_date`, `country`, `yoe`, etc.

### 3. Data Transformation (`cleanAndTransform-003.ipynb`)
#### Transformations Applied:
1. `application_date` → DATE type
2. Added calculated columns:
   - `score = (code_challenge + technical_interview) / 2`
   - `hired = 1 if score ≥ 7 else 0`
3. Countries → ISO 3-letter codes (e.g., USA, ECU)
4. Output: `candidates_cleaned` table

### 4. Analysis & Reporting (`reporting-004.ipynb`)
#### 6 Graphics:
- **Hiring by Tech Area**
- **Hiring Numbers by Tech Area**
- **Hiring Probability**
- **Hiring Over The Years**
- **Hiring by Seniority**
- **Hiring by Countries Over The Year**

**NOTE:** Although the charts are available in the notebook, they will be better visualized in a dashboard built with Power BI.

## 🔑 Key Insights
### Hiring Trends 2021-2022
- 🎯 **13.4% Hire Rate**: Only 6,700 candidates met hiring criteria
- 📉 **2022 Hiring Collapse**: 50% reduction vs. previous years
- 🎮 **Tech Dominance**: Game Development & DevOps = 62% of hires

### 🌎 Geographic Shifts
- **2021**: US hiring ↑ 40%
- **Ecuador**: Consistently underperformed

### 👩‍💼 Entry-Level Preference
- **Interns/Trainees**: 78% of hires