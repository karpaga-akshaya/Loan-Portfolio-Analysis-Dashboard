# Customer Loan Portfolio Analysis Dashboard

## 📊 Project Overview
This project demonstrates an end-to-end data analytics workflow using **SQL, Excel, Power BI, and DAX**.  
It analyzes customer loan portfolios, repayment behavior, and risk categories, providing actionable insights through interactive dashboards.

---

## 🛠️ Tools & Technologies
- **SQL** → Data modeling, table creation, joins, and aggregation queries  
- **Excel** → Dataset preparation and initial data storage  
- **Power BI** → Data modeling, relationships, and dashboard creation  
- **DAX** → Custom measures for KPIs and risk scoring  

---

## 📂 Data Model
- **Customers Table** → CustomerID, Name, Age, Gender, Location, Occupation  
- **Loans Table** → LoanID, CustomerID, LoanAmount, DurationMonths, EMI, InterestRate  
- **Repayments Table** → PaymentID, LoanID, PaymentDate, Status  

Relationships:
- Customers ↔ Loans (CustomerID)  
- Loans ↔ Repayments (LoanID)  

---

## 📈 KPIs
- **Total Loan Disbursed** → Sum of LoanAmount  
- **Average EMI** → Average of EMI  
- **Default Rate %** → Percentage of loans in default status  
- **Risk Category** → High-Risk vs Low-Risk customers based on repayment delays  

---

## 📊 Visuals
- **Bar Chart** → Loan distribution by Occupation  
- **Line Chart** → Monthly repayment trends  
- **Map** → Loan performance by Location  
- **Cards** → KPIs (Total Loan Disbursed, Avg EMI, Default Rate %, Risk Category)  

---

## 🧮 Key DAX Measures
```DAX
DefaultRate =
DIVIDE(
    COUNTROWS(FILTER('PaymentID (Repayments)', 'PaymentID (Repayments)'[Status] = "Default")),
    COUNTROWS('PaymentID (Repayments)'),
    0
) * 100

RiskScore =
DIVIDE(
    COUNTROWS(FILTER('PaymentID (Repayments)', 'PaymentID (Repayments)'[Status] = "Delayed")),
    COUNTROWS('PaymentID (Repayments)'),
    0
) * 100

RiskCategory =
IF([RiskScore] > 30, "High-Risk", "Low-Risk")
