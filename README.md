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
- Highest attrition by role:  
                       Employees  Attritions  AttritionRate%
JobRole                                                     
Laboratory Technician        261          62       23.754789
Sales Executive              329          58       17.629179
Research Scientist           293          47       16.040956
Sales Representative          84          33       39.285714
Human Resources               52          12       23.076923

- By gender:  
        Employees  Attritions  AttritionRate%
Gender                                       
Female        591          87       14.720812
Male          889         151       16.985377

- By department:  
                        Employees  Attritions  AttritionRate%
Department                                                   
Research & Development        967         133       13.753878
Sales                         450          93       20.666667
Human Resources                63          12       19.047619

- By age group:  
          Employees  Attritions  AttritionRate%
AgeGroup                                       
26-35           611         116       18.985270
18-25           123          44       35.772358
36-45           471          43        9.129512
46-55           228          27       11.842105
55+              47           8       17.021277

- By salary band (₹ per month equivalent scale):  
               Employees  Attritions  AttritionRate%
MonthlyIncome                                       
Upto 5k              753         163       21.646746
5k-10k               444          49       11.036036
10k-15k              150          21       14.000000
15k-20k              133           5        3.759398
20k+                   0           0             NaN

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
│  ├─ HR_Attrition.pbix
│  └─ screenshots/
│     └─ dashboard.png
├─ docs/
│  └─ report.pdf   # (optional)
├─ README.md
├─ LICENSE
└─ .gitignore
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

## 📄 License
MIT — free to use with attribution.

---

*Built with Power BI. Data for demonstration/learning only.*
