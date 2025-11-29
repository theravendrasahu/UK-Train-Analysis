# 📊 UK Train Analysis – Power BI Dashboard

*A compelling (very interesting) data analysis project using UK rail journey data*

---

## 📘 Project Overview

This Power BI project analyzes **31,653 UK train journeys** from January to April 2024.
The dataset includes information about:

* Ticket type & class
* Journey date & time
* Departure & arrival stations
* Ticket prices
* Delay reasons
* Refunds and cancellations

The goal of this dashboard is to deliver clear insights into train performance, passenger behavior, and revenue patterns using powerful data visualization techniques.

---

## 🎯 Key Objectives

The dashboard answers the following business questions:

### 1️⃣ What are the **most popular train routes**?

Visualized using a bar chart of route frequency.

### 2️⃣ What are the **peak travel hours**?

A time-distribution chart highlights when transactions are at their highest.

### 3️⃣ How does **revenue vary** by ticket type and class?

Two donut charts break down revenue across types and classes.

### 4️⃣ What is the **on-time performance**, and what factors contribute to delays?

KPIs show:

* On-Time %
* Delayed %
* Cancelled %
* Total Transactions

A bar chart highlights major delay reasons (weather, technical issues, signal failures, etc.).

---

## 📈 Features of the Dashboard

### 🔹 **KPI Cards**

* Revenue
* On-Time %
* Delayed %
* Cancelled %
* Total Transactions

### 🔹 **Most Popular Routes**

Created using a calculated column:

```DAX
Most Popular Routes =
railway[Departure Station] & " - " & railway[Arrival Destination]
```

Ranked to show the top routes by number of transactions.

### 🔹 **On-Time % Calculation**

Journey Status contains values like *On Time*, *Delayed*, *Cancelled*.

```DAX
OnTime Count =
CALCULATE(
    COUNTROWS(railway),
    UPPER(TRIM(railway[Journey Status])) = "ON TIME"
)

OnTime % =
DIVIDE([OnTime Count], COUNTROWS(railway), 0)
```

### 🔹 **Revenue by Ticket Type & Class**

Simple sum aggregation on `Price`.

### 🔹 **Delay Factors**

Bar chart summarizing reasons for delays.

---

## 🧮 DAX Measures Used

### **Total Revenue**

```DAX
Revenue = SUM(railway[Price])
```

### **Delayed %**

```DAX
Delayed % =
DIVIDE(
    CALCULATE(COUNTROWS(railway), railway[Journey Status] = "Delayed"),
    COUNTROWS(railway)
)
```

### **Cancelled %**

```DAX
Cancelled % =
DIVIDE(
    CALCULATE(COUNTROWS(railway), railway[Journey Status] = "Cancelled"),
    COUNTROWS(railway)
)
```

---

## 📂 Dataset Information

* **Source:** Maven Analytics Public Domain Dataset
* **File Type:** CSV
* **Rows:** 31,653
* **Columns:** 18
* **Date Added:** 15 May 2024
* **Domain:** Transportation, Business, Time Series

---

## 📌 Insights from the Dashboard

### 🔍 Demand Patterns

* The most travelled route was **Manchester → Piccadilly**.
* London-based routes appear heavily in the top rankings.

### 🔍 Peak Times

* Highest travel volume occurs between **6:00 AM – 9:00 AM**.
* A secondary peak appears around **6:00 PM**.

### 🔍 Financial Insights

* Standard class generates the majority of revenue.
* Off-peak tickets contribute strongly to earnings.

### 🔍 Operational Performance

* **On-Time Performance: ~87%**
* Top delay reasons:

  1. **Weather**
  2. **Technical Issues**
  3. **Signal Failure**

---

## 🛠 Tools & Technologies

* **Power BI Desktop**
* **Power Query** for cleaning
* **DAX** for custom KPIs
* **Data Modeling** using relationships, calculated columns, and measures

---

## 📁 Project Structure (For GitHub)

```
UK-Train-Analysis/
│
├── dataset/
│   └── UK_Train_Rides.csv
│
├── pbix/
│   └── UK_Train_Analysis.pbix
│
├── images/
│   └── dashboard_preview.png
│
└── README.md
```

---

## ⭐ What You Will Learn

This project helps you practice:

* Data cleaning in Power Query
* Creating **KPIs** and percentage measures in DAX
* Designing a clean, professional dashboard
* Analysing transportation data
* Storytelling using data

---

## 🚀 Want to Improve This Dashboard?

I can help you add:

* Forecasting charts
* Station-level drill-down
* Monthly trend lines
* Tooltip pages
* AI Insights (Key Influencers, Smart Narrative)

Just tell me!
