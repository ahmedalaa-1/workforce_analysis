# 👥 Workforce Analytics

> An HR analytics dashboard analyzing workforce structure, movement,
> compensation, and demographics to give a full picture of headcount
> health, turnover drivers, and payroll cost.

---

## 📌 Project Overview

This project analyzes the workforce of a 500-employee organization
using employee master data, movement (leaver) records, compensation
data, and performance ratings.

The dashboard focuses on understanding who the workforce is made up
of, how it moves (hires, resignations, terminations, retirements),
and where payroll cost is concentrated.

The analysis helps identify:

- Departments with the highest turnover
- The leading causes of employee departure
- Headcount vs. approved budget gaps
- Pay distribution across job grades, cities, and departments
- Workforce demographics (age, gender, tenure, performance)

---

## 🎯 Business Questions

The analysis aims to answer the following questions:

- What is the total headcount, and how many employees are active vs. have left?
- What is the overall turnover rate, and which departments drive it?
- How is headcount distributed across divisions, departments, job grades, and cities?
- Which departments are running below their approved headcount budget?
- How is payroll distributed across cities, departments, and job grades, and what are the salary ranges?
- What does the workforce look like in terms of gender, age, tenure, and performance?
- What are the main reasons employees leave, and how does length of service affect that?

---

## 🗂️ Dataset

The dataset contains employee master, movement, compensation, and
performance-related information.

### Main Data Areas

| Data Area | Description |
|---|---|
| Employee Master | Department, division, job title, job grade, work city |
| Movement | Employment status (Active, Resigned, Terminated, Retired, End of Contract) |
| Compensation | Salary, total payroll, job grade pay bands |
| Demographics & Performance | Gender, age group, tenure group, performance rating |

---

## 🛠️ Tools & Technologies

- Power BI
- DAX
- Power Query
- Figma / Figma Make
- Dashboard Design
- Data Analysis
- Data Visualization

---

# 🔄 Data Preparation

The data was prepared and structured for analysis by:

- Reviewing data quality and consistency across employee records
- Merging employee and department data to build a clean workforce model
- Grouping employees into Age Groups and Tenure Groups
- Calculating DAX measures for Turnover Rate, headcount, and leavers by type
- Building department-level headcount vs. budget comparisons
- Preparing data for the dashboard visualizations

---

# 🧩 Data Model

![Data Model](<data_model/Data model.png>)

### Model Overview

The model is built around **employees** as the central table, linked
to three supporting tables:

- **departments** (1 → *) — connected via `dep_id new key` / `department_id`, providing department, division, cost center, and headcount budget context for each employee.
- **payroll_monthly** (1 → *) — connected via `emp_new_key`, holding monthly salary, deductions, and gross/net pay for each employee.
- **attendance_leave_monthly** (1 → *) — connected via `emp_new_key`, holding monthly attendance rate, days present/absent, early departures, and annual leave data for each employee.

This structure lets the dashboard cross-analyze compensation and
attendance/movement data by department, division, and job grade
without duplicating employee attributes across tables.

---

# 📊 Dashboard

The dashboard consists of **6 analytical pages**:

1. Home
2. Overview
3. Distribution
4. Compensation & Cost
5. Workforce Profile
6. Workforce Movement

---

# 🏠 Page 1 — Home

![Home](<Dashboard/Home.png>)

### Purpose

The Home page gives a top-level snapshot of the workforce and links
out to every other page in the dashboard.

### Key KPIs

| KPI | Result |
|---|---:|
| Total Employees | 500 |
| Active Employees | 458 |
| Leavers | 42 |
| Turnover Rate | 8.40% |
| Total Payroll | 94.27M |

### Employees by Department (Top 5)

| Department | Employees |
|---|---:|
| Operations | 90 |
| Sales | 70 |
| Customer Service | 60 |
| Engineering & Maintenance | 50 |
| Supply Chain | 50 |

### Quick Workforce Summary

- **Highest Turnover Rate:** Human Resources — 20.0%
- **Largest Department:** Operations — 90 Employees
- **Highest Avg. Tenure:** Supply Chain — 6.3 Years

### Key Findings

- The organization has **500** total employees, **458** active and **42** leavers, for an overall turnover rate of **8.40%**.
- Total payroll across the workforce is **94.27M**.
- **Operations** is the largest single department at **90** employees.
- **Human Resources** has the highest departmental turnover rate at **20.0%**, well above the organization-wide average, despite not being one of the larger departments.
- **Supply Chain** employees have the longest average tenure at **6.3 years**.

---

# 📈 Page 2 — Overview

![Overview](<Dashboard/Overview.png>)

### Purpose

This page breaks down the current headcount by employment status and
shows how leavers and headcount are spread across departments.

### Employees by Employment Status

| Status | Employees |
|---|---:|
| Active | 458 |
| Resigned | 21 |
| Terminated | 10 |
| Retired | 7 |

### Employees by Department

| Department | Employees | Share of Leavers |
|---|---:|---:|
| Operations | 90 | 18% |
| Sales | 70 | 14% |
| Customer Service | 60 | 12% |
| Engineering & Maintenance | 50 | 10% |
| Supply Chain | 50 | 10% |
| IT | 40 | 8% |
| Finance | 35 | 7% |
| Human Resources | 30 | 6% |
| Procurement | 25 | 5% |
| Marketing | 20 | 4% |
| Health, Safety & Environment | 20 | 4% |
| Legal & Compliance | 10 | 2% |

### Key Findings

- **Resignation** is the leading cause of departure, accounting for **21** of the **42** total leavers (**50%**), followed by Termination (**10**) and Retirement (**7**).
- **Operations** contributes the largest share of leavers at **18%** of total departures — consistent with it being the largest department by headcount.
- **Human Resources** only makes up **6%** of leavers by count, but combined with its small size (30 employees) this produces the **20.0%** turnover rate seen on the Home page.

---

# 🧩 Page 3 — Distribution

![Distribution](<Dashboard/Distribution.png>)

### Purpose

This page shows how headcount is structured across divisions,
departments, job grades, job titles, and cities — and how actual
headcount compares to approved budget.

### Key KPIs

| KPI | Result |
|---|---:|
| Total Employees | 500 |
| Number of Divisions | 12 |
| Number of Departments | 12 |
| Number of Job Roles | 54 |

### Active Employees vs. Headcount Budget (by Department)

| Department | Active Employees | Headcount Budget |
|---|---:|---:|
| Legal & Compliance | 10 | 11 |
| Marketing | 17 | 22 |
| Health, Safety & Environment | 19 | 23 |
| Procurement | 24 | 28 |
| Human Resources | 24 | 31 |
| Finance | 31 | 40 |

### Employees by Job Grade

| Job Grade | Employees |
|---|---:|
| G02 | 131 |
| G05 | 123 |
| G04 | 90 |
| G03 | 76 |
| G08 | 34 |
| G06 | 26 |
| G07 | 16 |
| G09 | 2 |
| G10 | 2 |

### Employees by City

| City | Employees |
|---|---:|
| Abha | 60 |
| Dammam | 58 |
| Yanbu | 53 |
| Riyadh | 52 |
| Tabuk | 51 |
| Madinah | 50 |
| Makkah | 49 |
| Khobar | 45 |
| Jeddah | 42 |
| Jubail | 40 |

### Top Job Titles by Headcount

| Job Title | Employees |
|---|---:|
| Operations Assistant | 44 |
| Call Center Agent | 34 |
| Sales Representative | 31 |
| Warehouse Keeper | 30 |
| Maintenance Technician | 23 |
| Customer Service Specialist | 20 |

### Key Findings

- The organization spans **12** divisions, **12** departments, and **54** distinct job roles across **500** employees.
- **G02** is the most common job grade with **131** employees, while the senior grades **G09** and **G10** have only **2** employees each.
- Several departments are running below their approved headcount: **Human Resources** has **24** active employees against a budget of **31** (7 open positions), and **Finance** has **31** against **40** (9 open positions).
- **Abha** and **Dammam** are the two largest work locations, with **60** and **58** employees respectively.
- **Operations Assistant** is the single most common job title, with **44** employees.

---

# 💰 Page 4 — Compensation & Cost

![Compensation & Cost](<Dashboard/Compensation &Cost.png>)

### Purpose

This page examines how payroll cost is distributed across cities,
job grades, job titles, and departments.

### Key KPIs

| KPI | Result |
|---|---:|
| Total Payroll | 94.27M |
| Max Salary | 37K |
| Min Salary | 3K |
| Median Salary | 7.58K |

### Total Payroll by Work City

| City | Total Payroll |
|---|---:|
| Dammam | 12.1M |
| Madinah | 10.7M |
| Abha | 10.5M |
| Riyadh | 10.0M |
| Makkah | 9.7M |
| Khobar | 9.6M |
| Yanbu | 8.6M |
| Jeddah | 8.4M |
| Tabuk | 7.7M |
| Jubail | 6.9M |

### Median Salary by Job Grade

| Job Grade | Median Salary |
|---|---:|
| G10 | 35.0K |
| G09 | 32.8K |
| G08 | 25.9K |
| G07 | 18.4K |
| G06 | 14.7K |
| G05 | 11.0K |
| G04 | 7.7K |
| G03 | 5.3K |
| G02 | 4.1K |

### Highest Median-Salary Job Titles

| Job Title | Median Salary |
|---|---:|
| Legal Affairs Director | 37,150.00 |
| Operations Executive Director | 35,400.00 |
| Sales Executive Director | 34,650.00 |
| Procurement Manager | 29,150.00 |
| Chief Accountant | 28,350.00 |
| HR Manager | 28,150.00 |
| Marketing Manager | 26,850.00 |

### Total Payroll by Department

| Department | Total Payroll |
|---|---:|
| Operations | 16.4M |
| Sales | 15.8M |
| Finance | 9.0M |
| Engineering & Maintenance | 8.3M |
| Customer Service | 8.0M |
| IT | 8.0M |
| Supply Chain | 6.8M |
| Procurement | 5.5M |
| Human Resources | 5.0M |
| Health, Safety & Environment | 4.8M |
| Marketing | 3.4M |
| Legal & Compliance | 3.3M |

### Key Findings

- Total payroll is **94.27M**, with individual salaries ranging from **3K** to **37K** and a median of **7.58K**.
- Pay scales consistently with job grade — median salary rises from **4.1K** at G02 to **35.0K** at G10.
- **Dammam** carries the highest payroll cost by city at **12.1M**, even though **Abha** has more employees — pointing to a higher average salary mix in Dammam.
- **Operations** and **Sales** together account for **32.2M** of total payroll (about **34%**), matching their status as the two largest departments.
- The **Legal Affairs Director** role has the highest median salary at **37,150**.

---

# 🧑‍💼 Page 5 — Workforce Profile

![Workforce Profile](<Dashboard/Workforce Profile.png>)

### Purpose

This page profiles the workforce by performance, gender, age, and
tenure.

### Key KPIs

| KPI | Result |
|---|---:|
| Total Employees | 500 |
| Active Employees | 458 |
| Leavers | 42 |
| Avg. Age | 35.11 |

### Performance Distribution

| Rating | Employees |
|---|---:|
| Meets Expectations | 278 |
| Exceeds Expectations | 118 |
| Needs Improvement | 60 |
| Outstanding | 35 |
| Under Review | 9 |

### Employees by Gender

| Gender | Employees |
|---|---:|
| Male | 395 |
| Female | 105 |

### Employees by Age Group

| Age Group | Employees |
|---|---:|
| 30-39 | 276 |
| 40-49 | 114 |
| 20-29 | 103 |
| 50-59 | 7 |

### Employees by Tenure Group

| Tenure Group | Employees |
|---|---:|
| 0-3 Years | 160 |
| 6-9 Years | 150 |
| 3-6 Years | 145 |
| Leaver | 42 |
| 9-10 Years | 2 |
| 10+ Years | 1 |

### Key Findings

- The workforce is predominantly **male** (**395**, about **79%**) versus **female** (**105**, about **21%**).
- Average age is **35.11**, with the **30-39** age group by far the largest at **276** employees (**55.2%**).
- The majority of employees (**278**, **55.6%**) **Meet Expectations**; only **35** are rated **Outstanding** and **60** **Need Improvement**.
- Tenure is fairly evenly split between **0-3 years** (160), **6-9 years** (150), and **3-6 years** (145), with very few employees staying beyond 9 years (only **3** total).

---

# 🔄 Page 6 — Workforce Movement

![Workforce Movement](<Dashboard/Workforce Movement.png>)

### Purpose

This page focuses on turnover — why employees leave, how long they
had been with the company, and which departments are most affected.

### Key KPIs

| KPI | Result |
|---|---:|
| Total Employees | 500 |
| Active Employees | 458 |
| Leavers | 42 |
| Turnover Rate | 8.40% |

### Leavers by Employment Status

| Status | Leavers |
|---|---:|
| Resigned | 21 |
| Terminated | 10 |
| Retired | 7 |
| End of Contract | 4 |

### Leavers by Length of Service

| Tenure Group | Leavers |
|---|---:|
| 0-3 Year | 17 |
| 3-6 Years | 13 |
| 6-9 Years | 11 |
| 9+ Years | 1 |

### Turnover by Department

| Department | Total Employees | Leavers | Turnover Rate |
|---|---:|---:|---:|
| Human Resources | 30 | 6 | 20.00% |
| Marketing | 20 | 3 | 15.00% |
| IT | 40 | 6 | 15.00% |
| Engineering & Maintenance | 50 | 6 | 12.00% |
| Finance | 35 | 4 | 11.43% |
| Sales | 70 | 5 | 7.14% |

### Key Findings

- **Resignation** is the top driver of attrition, accounting for **21** of **42** leavers (**50%**).
- Most leavers (**17** of **42**, about **40%**) had less than **3 years** of tenure, in line with the broader early-tenure risk seen across the workforce.
- **Human Resources** has the highest departmental turnover rate at **20.00%**, despite being a mid-sized department.
- **IT** and **Marketing** follow with turnover rates of **15.00%** each, while **Sales** has the lowest rate among the departments shown at **7.14%**.

---

# 💡 Key Insights

### 1. Turnover Is Concentrated in Smaller/Mid-Sized Departments

**Human Resources** has by far the highest turnover rate at **20.0%**,
followed by **Marketing** and **IT** at **15.0%** each — despite these
being smaller departments than Operations or Sales.

### 2. Resignation Is the Leading Cause of Attrition

**21** of **42** leavers (**50%**) resigned voluntarily — more than
double the next-highest cause, Termination (**10**).

### 3. Early-Tenure Employees Are the Most Likely to Leave

**17** of **42** leavers (about **40%**) had less than **3 years** of
service, consistent with the overall tenure distribution where very
few employees remain past **9 years**.

### 4. Headcount Is Below Budget in Several Departments

**Human Resources** (24/31), **Finance** (31/40), and other
departments are operating below their approved headcount budget,
indicating unfilled positions.

### 5. Pay Scales Consistently with Job Grade and Location

Median salary rises steadily from **4.1K** at G02 to **35.0K** at
G10, and **Dammam** carries the highest payroll cost by city despite
not having the most employees.

### 6. The Workforce Skews Male and Early/Mid-Career

**79%** of employees are male, and **55%** fall in the **30-39** age
group.

---

# 📈 Business Recommendations

Based on the analysis, areas for further investigation and action
include:

- Investigating the root cause of HR's high **20%** turnover rate given its modest size, since resignation appears to be the dominant driver.
- Strengthening onboarding and early-career engagement programs, since most leavers exit within their first **3 years**.
- Reviewing compensation and workload in **Marketing** and **IT**, the next highest-turnover departments after HR.
- Closing headcount gaps in departments running below approved budget (**HR**, **Finance**, **Procurement**) to relieve capacity pressure.
- Reviewing gender representation and considering diversity initiatives, given the workforce is **79%** male.
- Monitoring the **Needs Improvement** and **Under Review** performance segments (**69** employees combined) for targeted coaching.

---

# 📁 Repository Structure

```text
📦 Workforce-Analytics
│
├── 📂 Dashboard
│   └── Workforce Analytics Dashboard.pbix
│
├── 📂 Dataset
│   └── dataset.xlsx
│
├── 📂 Images
│   ├── page-1-home.png
│   ├── page-2-overview.png
│   ├── page-3-distribution.png
│   ├── page-4-compensation-cost.png
│   ├── page-5-workforce-profile.png
│   └── page-6-workforce-movement.png
│
└── 📜 README.md
```
