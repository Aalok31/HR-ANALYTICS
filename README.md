# HR Attrition Analytics (Power BI)

This project analyzes employee attrition using a public-style HR dataset and an interactive Power BI dashboard.

## 🔎 Executive Summary
- **Employees:** 1480
- **Attritions:** 238
- **Attrition Rate:** 16.08%
- **Average Age:** 36.92 years
- **Average Monthly Income:** 6.50k
- **Average Years at Company:** 7.01

**Key signals**


### 📌 Attrition by Job Role
| Job Role               | Employees | Attritions | Attrition Rate (%) |
|-------------------------|-----------|------------|---------------------|
| Laboratory Technician   | 261       | 62         | 23.75%             |
| Sales Executive         | 329       | 58         | 17.63%             |
| Research Scientist      | 293       | 47         | 16.04%             |
| Sales Representative    | 84        | 33         | **39.29%**         |
| Human Resources         | 52        | 12         | 23.08%             |

---

### 📌 Attrition by Gender
| Gender | Employees | Attritions | Attrition Rate (%) |
|--------|-----------|------------|---------------------|
| Female | 591       | 87         | 14.72%             |
| Male   | 889       | 151        | 16.99%             |

---

### 📌 Attrition by Department
| Department              | Employees | Attritions | Attrition Rate (%) |
|--------------------------|-----------|------------|---------------------|
| Research & Development   | 967       | 133        | 13.75%             |
| Sales                    | 450       | 93         | 20.67%             |
| Human Resources          | 63        | 12         | 19.05%             |

---

### 📌 Attrition by Age Group
| Age Group | Employees | Attritions | Attrition Rate (%) |
|-----------|-----------|------------|---------------------|
| 18–25     | 123       | 44         | **35.77%**         |
| 26–35     | 611       | 116        | 18.99%             |
| 36–45     | 471       | 43         | 9.13%              |
| 46–55     | 228       | 27         | 11.84%             |
| 55+       | 47        | 8          | 17.02%             |

---

### 📌 Attrition by Salary Band (₹ per month)
| Salary Band | Employees | Attritions | Attrition Rate (%) |
|-------------|-----------|------------|---------------------|
| Upto ₹5k    | 753       | 163        | **21.65%**         |
| ₹5k–10k     | 444       | 49         | 11.04%             |
| ₹10k–15k    | 150       | 21         | 14.00%             |
| ₹15k–20k    | 133       | 5          | 3.76%              |
| ₹20k+       | 0         | 0          | —                  |

## 📊 Dashboard
The dashboard surfaces:
- Overall KPIs (Employee Count, Attritions, Attrition Rate, Avg. Age, Avg. Salary, Avg. Tenure)
- Donut: Attrition by Education Field
- Bars: Attrition by Age Group, Salary Band, Tenure (Years at Company), Age
- Matrix: Job Role × Age Group
- Stacked bars: Attrition by Job Role, Department & Gender

> *Screenshot and `.pbix` file included in this repo.*

## 🧮 DAX Measures (selected)
```DAX
Employees = COUNTROWS(Employees)

Attritions =
CALCULATE(
    COUNTROWS(Employees),
    Employees[Attrition] = "Yes"
)

Attrition Rate % =
DIVIDE([Attritions], [Employees])

Average Age = AVERAGE(Employees[Age])

Average Monthly Income = AVERAGE(Employees[MonthlyIncome])

Average Years at Company = AVERAGE(Employees[YearsAtCompany])

Attritions by Category =
VAR _attr =
    CALCULATE([Attritions], ALLEXCEPT(Employees, Employees[Category]))
RETURN _attr
```

## 🗂 Repository Structure
```
hr-attrition-analytics/
├─ data/
│  └─ HR_Analytics.csv
├─ dashboard/
│  ├─ DASHBOARD.pbix
│  └─ screenshots/
│     └─ dashboard.png 
├─ README.md


```

## 🚀 How to Use
1. Clone/download this repository.
2. Open **`dashboard/HR_Attrition.pbix`** in Power BI Desktop.
3. Update the data source path to `data/HR_Analytics.csv` if prompted.
4. Refresh to reproduce visuals.

## ✅ Insights & Recommendations
- Focus retention efforts on **Sales** and **R&D**, especially roles: *Sales Executive*, *Lab Technician*, *Research Scientist*.
- Early-career groups (**18–35**) and **lower salary bands (≤ 10k)** are high-risk segments.
- **Overtime** and **frequent travel** likely correlate with attrition—consider policies addressing workload and travel.
- Targeted learning paths and career progression can reduce exits in junior roles.


---

*Built with Power BI. Data for demonstration/learning only.*
