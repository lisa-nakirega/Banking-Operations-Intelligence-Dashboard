# Banking Operations Intelligence Dashboard

## Project Overview

This project demonstrates how Business Intelligence can be used to monitor and improve banking operations through interactive dashboards, operational KPIs, and data-driven insights.

**Status:** 🚧 In Progress

## Tools
- Power BI
- SQL Server
- Microsoft Excel
- GitHub

## Project Objective

To build an interactive dashboard that enables banking management to monitor employee productivity, branch performance, SLA compliance, operational trends, and overall service efficiency.

## Technical Highlights

- Designed a dimensional data model using a star schema.
- Created fact and dimension tables following BI best practices
- Reduced data redundancy through dimensional modeling.
- Designed a banking operations database from business requirements.
- Built a scalable SQL Server database for Power BI.

# 🗄️ Database Design

## Overview

The Banking Operations Intelligence Solution uses a **Star Schema**, a dimensional modeling technique commonly used in Business Intelligence (BI) and data warehousing.

The database separates descriptive business information into **dimension tables** while storing operational business events in a central **fact table**. This design minimizes data redundancy, improves query performance, and provides an efficient structure for reporting and dashboard development in Power BI.

---

## Why a Star Schema?

A Star Schema was selected because it is optimized for analytical workloads rather than transactional systems.

### Benefits

- Reduces duplicate data by storing descriptive information only once.
- Improves SQL query performance.
- Simplifies Power BI relationships.
- Supports scalable reporting and dashboard development.
- Aligns with industry-standard Business Intelligence practices.

---

## Database Architecture

```text
                  DimDate
                     │
                     │
DimCustomer ───┐     │
               │     │
DimProduct ────┼──► FactCases ◄── DimEmployee
               │            │
               │            │
               └────────────┘
                 DimBranch
```

---

# Dimension Tables

## 📍 DimBranch

Stores branch information used for geographical and operational analysis.

**Primary Key**

- BranchID

**Business Purpose**

Allows management to compare operational performance across different branches and identify workload distribution.

---

## 👥 DimEmployee

Stores employee information for staff processing account maintenance requests.

**Primary Key**

- EmployeeID

**Business Purpose**

Supports employee productivity analysis, workload allocation, and operational performance reporting.

---

## 👤 DimCustomer

Stores customer demographic information used for segmentation and reporting.

**Primary Key**

- CustomerID

**Business Purpose**

Enables customer segmentation based on customer type, occupation, location, and other demographic characteristics.

---

## 🏦 DimProduct

Stores information about banking products.

**Primary Key**

- ProductCode

**Business Purpose**

Allows analysis of operational cases by banking product, category, and product characteristics.

---

## 📅 DimDate

Stores calendar information for every date used in the project.

**Primary Key**

- DateKey

**Business Purpose**

Supports time-based analysis including:

- Daily trends
- Monthly reporting
- Quarterly reporting
- Year-over-Year comparisons
- Weekday vs Weekend analysis

---

# 📊 Fact Table

## FactCases

The **FactCases** table is the central table of the data warehouse.

Each record represents **one account case** processed by the operations team.

Rather than storing descriptive information repeatedly, the table references dimension tables through foreign keys.

### Foreign Keys

| Foreign Key | References |
|-------------|------------|
| CustomerID | DimCustomer |
| ProductCode | DimProduct |
| BranchID | DimBranch |
| EmployeeID | DimEmployee |
| OpenedDateKey | DimDate |
| ClosedDateKey | DimDate |

---

# Database Design Decisions

## Primary Keys

Each dimension table contains a Primary Key that uniquely identifies every record.

Examples include:

- BranchID
- EmployeeID
- CustomerID
- ProductCode
- DateKey

Primary Keys prevent duplicate records and provide the foundation for table relationships.

---

## Foreign Keys

The FactCases table uses Foreign Keys to establish relationships with dimension tables.

This approach:

- Maintains referential integrity.
- Eliminates duplicate descriptive data.
- Improves consistency across reports.
- Simplifies SQL joins.

---

## Why a Date Dimension?

Instead of storing raw dates inside the FactCases table, the project uses a dedicated Date Dimension.

This allows reporting by:

- Day
- Month
- Quarter
- Year
- Day of Week
- Weekend Indicator

This design follows common Business Intelligence and Kimball dimensional modeling practices.

---

# Expected Business Insights

The database has been designed to answer operational business questions such as:

- Which branches process the highest number of account maintenance cases?
- Which employees process the most cases?
- Which banking products generate the highest operational workload?
- What percentage of cases exceed their SLA?
- Which queues experience the highest backlog?
- How does operational workload change over time?
- Which customer segments generate the highest number of cases?

---

# Technical Highlights

- SQL Server relational database
- Star Schema dimensional model
- Primary and Foreign Key relationships
- Optimized for analytical reporting
- Designed for Power BI integration
- Business-oriented data model supporting operational analytics
