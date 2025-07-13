# 🧬 Eye Cancer Patient Data Analysis

A comprehensive dataset of **5,000 patients** diagnosed with **Melanoma**, **Retinoblastoma**, or **Lymphoma**. This dataset is designed for use in healthcare research, machine learning, survival analysis, and exploratory data analysis.

---

## 📂 Dataset Summary

| Feature Category | Description |
|------------------|-------------|
| 📊 **Demographics** | Age (1–90), Gender (Male, Female, Other), Country |
| 🧪 **Clinical Info** | Cancer Type, Stage at Diagnosis, Laterality |
| 💉 **Treatment** | Surgery, Radiation (dose in Gy), Chemotherapy (session count) |
| ⚕️ **Outcomes** | Survival Time (months), Outcome Status (Active, Remission, Deceased) |
| 🧬 **Genetics** | BRAF mutation status, Family History of Eye Cancer |

---

## 📈 Key Statistics

- **Average survival time:** `61 months`
- **Average patient age:** `45 years`
- **Most prevalent cancer:** `Lymphoma (1,637 cases)`
- **Country with highest cases:** `Australia (~850/year)`
- **BRAF mutation present:** ~50%
- **Positive family history:** ~51%
- **Surgery:** Majority of planned surgeries completed

---

## 🔍 Key Insights

- Cancer subtypes are nearly equally distributed → Need for **subtype-specific research**
- **Chemotherapy** shows slightly better survival rates (62.19 months)
- **BRAF+ patients** show higher remission counts → Potential for targeted therapy
- Patients **with family history** survive ~1.5–2 months longer
- Projected survival (2030):  
  - With history → **90 months**  
  - Without history → **85 months**
- **Emerging hotspots**: Brazil and India → Priority for resource planning

---

## 💡 Use Cases

- 🔮 **Survival prediction models**  
- 🧬 **Genetic marker correlation analysis**  
- 🧠 **Clustering cancer subtypes**  
- 🌍 **Geo-demographic pattern analysis**  
- 🩺 **Treatment-outcome optimization**

---

## 🧰 Python Code used for Data Cleaning Purpose

```python
#Import libraries 
import pandas as pd
from datetime import datetime

# File path
input_file = "eye_cancer_patients.csv"
output_file = "Eye cancer patients dataset_cleaned.csv"

# Load the dataset
df = pd.read_csv(input_file)

# Normalize 'Gender' column
gender_map = {'M': 'Male', 'F': 'Female', 'Other': 'Other'}
df['Gender'] = df['Gender'].map(gender_map)

# Normalize 'Surgery_Status' column
surgery_status_map = {True: 'Completed', False: 'Not Completed'}
df['Surgery_Status'] = df['Surgery_Status'].map(surgery_status_map)

# Normalize 'Family_History' column
family_history_map = {True: 'Yes', False: 'No'}
df['Family_History'] = df['Family_History'].map(family_history_map)

# Normalize 'Date_of_Diagnosis' to DD:MM:YYYY format
def normalize_date(date_str):
    try:
        return pd.to_datetime(date_str).strftime('%d:%m:%Y')
    except Exception:
        return date_str  # Return original if parsing fails

df['Date_of_Diagnosis'] = df['Date_of_Diagnosis'].apply(normalize_date)

# Save the cleaned dataset
df.to_csv(output_file, index=False)

print("Dataset cleaned and saved to:", output_file)

import pandas as pd

# File path
file_path = "Eye cancer patients dataset_cleaned.csv"

# Load the dataset
df = pd.read_csv(file_path)

# Fill empty cells in 'Genetic_Markers' with 'None'
df['Genetic_Markers'] = df['Genetic_Markers'].fillna('None')

# Save the updated dataset
df.to_csv(file_path, index=False)

