![image](https://github.com/user-attachments/assets/8523207d-44d9-4c47-abac-1bfd044e2362)# 🇹🇭 Thailand Election Data Preparation (2023)

> 📊 Google Colab notebook for preparing, exploring, and cleaning Thailand 2023 election data.  
> โปรเจกต์โชว์ตัวอย่างงาน Data Wrangling และ EDA สำหรับพอร์ต Data Analyst

---

## 📌 Motivation

ชุดข้อมูลผลการเลือกตั้งไทย 2566 มีหลายไฟล์/หลายชีท (Excel, CSV)  
✅ เป้าหมายคือรวม → ทำความสะอาด → แปลงให้อยู่ใน *tidy data* พร้อมใช้สำหรับ Dashboard/Analysis

---

## 🎯 Goals

- Import & explore raw election data
- Clean & check missing values
- Normalize into tidy format
- Merge data sources into a single table
- Export cleaned CSV

---

## 🗂️ Data Sources

**Main file**: `ectreport2023.xlsx`

**Key sheets/tables:**
- `result_constituencies_PartyList` → party-list vote results
- `result_constituencies_Candidate` → constituency MP results
- `result_constituencies_status` → turnout data
- `info_province` → province metadata
- `info_party_overview` → party info (name, color, logo)
- `Candidate_Constituency`, `Candidate_PartyList`, `Candidate_PM` → candidate info

---

## 💻 Tech Stack

- Google Colab
- Python 3.x
- pandas
- numpy

---

## 📑 Notebook Workflow

### 1️⃣ Mount Google Drive
เข้าถึงไฟล์ใน Google Drive:
```python
from google.colab import drive
drive.mount('/content/gdrive')
```
### 2️⃣ Import Data
โหลดไฟล์ Excel
แยกหลายชีทเป็น DataFrame
```python
import pandas as pd
dfs = pd.ExcelFile('ectreport2023.xlsx')
dfs.sheet_names
```
### 3️⃣ Explore Database
- ดู Schema, ตรวจสอบ Columns, Types
- ตรวจสอบ Nulls
- ✅ Clean / fillna
- ✅ Map รหัส → ชื่อพรรค/โค้ด/สี
---
✅ ดู Schema, ตรวจสอบ Columns, Types ตัวแปรใน sheet อื่นๆ
---
```python
Schema.head()  
```
![Explore Database Schema](png1.png)
---
✅ ตรวจสอบ Nulls
---
```python
print(result_constituencies_PartyList.isnull().any()) # เช็คค่าว่าง Null
result_constituencies_PartyList.head() 
```
![Explore Database Schema](png2.png)
```python
print(result_constituencies_Candidate.isnull().any()) # เช็คค่าว่าง Null
result_constituencies_Candidate.head()
```
![Explore Database Schema](png3.png)
```python
print(result_constituencies_status.isnull().any()) # เช็คค่าว่าง Null
result_constituencies_status.head()
```
![Explore Database Schema](png4.png)
```python
print(info_province.isnull().any()) # เช็คค่าว่าง Null
info_province.head()
```
![Explore Database Schema](png5.png)
```python
print(Candidate_constituency.isnull().any()) # เช็คค่าว่าง Null
Candidate_constituency.head()
```
![Explore Database Schema](png6.png)
```python
print(Candidate_partyList.isnull().any()) # เช็คค่าว่าง Null
Candidate_partyList.head()
```
![Explore Database Schema](png7.png)
```python
print(Candidate_pm.isnull().any()) # เช็คค่าว่าง Null
Candidate_pm.head()
```
![Explore Database Schema](png8.png)
