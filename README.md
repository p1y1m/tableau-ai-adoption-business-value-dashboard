# Tableau AI Adoption & Business Value Analytics

**Author:** Pedro Yanez Melendez

> **Data note:** The dataset used in this repository is non-production data created for portfolio analysis and does not contain employer, client, or production information.

This project presents an enterprise-oriented **Tableau Public analytics solution for AI adoption and business value monitoring**. It connects user activity, organizational adoption, target attainment, tool utilization, cost, estimated value, and operational indicators into a single analytical dashboard.

The implementation focuses on practical Tableau skills: data connection, calculated fields, distinct-count logic, filters, continuous date analysis, KPI design, departmental comparisons, scatter analysis, mark encoding, reference lines, number formatting, dashboard composition, and publication through Tableau Public.

## Live Dashboard

**Tableau Public:**  
https://public.tableau.com/app/profile/pedro.yanez/viz/AIAdoptionAnalytics/Dashboard1

**GitHub repository:**  
https://github.com/p1y1m/tableau-ai-adoption-business-value-dashboard

---

## Project Objectives

The dashboard was designed to answer questions such as:

- How is AI adoption evolving over time?
- How many users are active in the selected reporting period?
- What percentage of the user population is actively adopting AI?
- Which departments are closest to or furthest from their adoption targets?
- How do AI tools compare in terms of total cost and estimated business value?
- Which tools sit above or below average cost and average value?
- How can executive KPIs and detailed analytical views be combined in one Tableau dashboard?

---

## Final Dashboard KPIs

For the selected reporting period, the dashboard displays:

| KPI | Value |
|---|---:|
| Active Users | **307** |
| Adoption Rate | **95.9%** |
| Estimated Value | **$141K** |

These KPIs are presented together with the underlying trend, departmental comparison, and tool-level cost/value analysis.

---

## Dashboard Components

### 1. Active Users KPI

The Active Users card measures the distinct number of active users for the selected month.

The KPI uses:

- `User ID`
- `Active Flag`
- `Month`
- `COUNTD`
- single-period filtering
- large-number KPI formatting

---

### 2. Adoption Rate KPI

The Adoption Rate KPI calculates the proportion of distinct users classified as active.

The calculated field used in Tableau is:

```tableau
COUNTD(
    IF [Active Flag] = 1
    THEN [User ID]
    END
)
/
COUNTD([User ID])
```

The result is formatted as a percentage and displayed as an executive KPI.

---

### 3. Estimated Value KPI

The Estimated Value KPI aggregates:

```tableau
SUM([Estimated Value USD])
```

The result is formatted using:

- Currency (Custom)
- 0 decimal places
- Thousands `(K)`
- `$` prefix

This produces a compact executive value such as **$141K**.

---

### 4. Monthly Active Users

The time-series worksheet tracks active-user evolution across the analysis period.

Main Tableau operations include:

- `Month` on Columns
- `User ID` aggregated as `COUNTD`
- `Active Flag = 1`
- continuous monthly date axis
- line mark
- axis and label formatting

This view makes it possible to inspect adoption growth over time rather than relying only on a single-period KPI.

---

### 5. Adoption Rate by Department

A horizontal bar chart compares adoption performance across departments.

The view uses departmental adoption measures together with target-gap information to provide a ranking-oriented view of organizational adoption.

Departments represented in the analytical dataset include areas such as:

- Finance
- Operations
- IT
- Supply Chain
- Customer Service
- Marketing
- Sales
- Procurement
- HR
- Legal

The dashboard also includes a **Gap vs Target (pp)** encoding to highlight differences between actual adoption and target adoption.

---

### 6. AI Value vs Cost by Tool

The scatter plot compares AI tools using:

- **X-axis:** `SUM(Total Cost USD)`
- **Y-axis:** `SUM(Estimated Value USD)`
- **Size:** `SUM(Messages)`
- **Color:** `Tool Category`
- **Label:** `Tool`

The view includes enterprise tools and internal AI agents, including:

- ChatGPT Enterprise
- Microsoft Copilot
- Gemini Enterprise
- Claude Enterprise
- Internal Support Agent
- Internal Sales Agent

This visualization provides a compact way to compare cost, value, usage volume, and tool category simultaneously.

---

## Average Cost and Average Value Reference Lines

Two table-level reference lines were added to the scatter plot:

- **Avg. Cost**
- **Avg. Value**

Together they divide the visualization into four analytical regions.

This makes it easier to distinguish tools that are:

- above average value / below average cost
- above average value / above average cost
- below average value / below average cost
- below average value / above average cost

The reference lines were configured from Tableau's **Analytics** pane and applied at **Table** scope.

---

## Analytical Dataset

The primary analytical source is:

```text
AI_Adoption_Advanced_Tableau_Dataset.csv
```

A separate reference file is used for field interpretation:

```text
AI_Adoption_Data_Dictionary.csv
```

The analytical dataset contains fields across several functional areas, including:

### Time and Keys

- Month
- Year
- Quarter
- Month Name
- Month Index
- User Month Key
- Department Month Key
- Activity ID

### User and Organization

- User ID
- Employee Label
- Department
- Business Unit
- Role Level
- Location
- Hire Date

### AI Adoption and Lifecycle

- Active Flag
- New User Flag
- Retained User Flag
- Reactivated User Flag
- Churned User Flag
- First Active Month
- Adoption Stage
- AI Maturity Score
- AI Champion
- Training Status
- AI Training Date
- License Tier

### Usage

- Sessions
- Messages
- Days Active
- Active Minutes
- Input Tokens
- Output Tokens
- User Month Messages
- Department Month Messages

### Cost and Value

- Usage Cost USD
- License Cost USD
- Total Cost USD
- Estimated Hours Saved
- Estimated Value USD
- ROI Pct
- User Month Cost USD
- User Month Value USD
- User Month ROI Pct
- Monthly Budget USD
- Budget Variance USD

### Quality, Governance, and Operations

- Satisfaction Score
- Successful Response Pct
- Policy Compliance Pct
- Sensitive Data Incidents
- Escalations
- Automation Runs
- Avg Response Time Sec

### Department-Level Adoption

- Department Headcount
- Department Active Users
- Department Adoption Rate Pct
- Adoption Target Pct
- Adoption Target Gap Pct
- Active User Target
- Message Target
- Hours Saved Target
- Satisfaction Target

---

## Tableau Techniques Demonstrated

This repository documents practical use of:

- Tableau Public web authoring
- data-source connection
- dimension and measure handling
- discrete vs. continuous dates
- `COUNTD`
- `SUM`
- calculated fields
- date filtering
- boolean / flag filtering
- percentage formatting
- custom currency formatting
- sorting by measure
- line charts
- horizontal bar charts
- scatter plots
- mark labels
- color encoding
- size encoding
- legends
- reference lines
- table-level analytical scope
- KPI worksheets
- tiled dashboard containers
- fixed dashboard sizing
- axis formatting
- worksheet title cleanup
- dashboard publication
- Tableau Public sharing

---

## Manual Build Documentation

The repository includes:

```text
Tableau_AI_Adoption_Dashboard_Build_Walkthrough_GitHub.docx
```

This is a **127-page visual build walkthrough** documenting the manual Tableau work from start to finish.

It includes the actual build sequence across:

1. Tableau Public setup
2. data connection
3. source inspection
4. Monthly Active Users construction
5. Adoption Rate by Department construction
6. AI Value vs Cost by Tool construction
7. axis and number formatting
8. average-cost reference line
9. average-value reference line
10. Active Users KPI
11. Adoption Rate KPI
12. Estimated Value KPI
13. dashboard composition
14. title standardization
15. final formatting
16. publishing and sharing

The document intentionally preserves intermediate states, configuration dialogs, corrections, and final formatting decisions so the implementation process can be reviewed visually.

---

## Repository Structure

```text
tableau-ai-adoption-business-value-dashboard/
│
├── README.md
├── AI_Adoption_Advanced_Tableau_Dataset.csv
├── AI_Adoption_Data_Dictionary.csv
├── Tableau_AI_Adoption_Dashboard_Build_Walkthrough_GitHub.docx
└── supporting project files
```

The live visualization is hosted in Tableau Public rather than being limited to a static image export.

---

## Reproducing the Analysis in Tableau

A high-level reconstruction sequence is:

1. Open Tableau Public.
2. Connect `AI_Adoption_Advanced_Tableau_Dataset.csv`.
3. Keep the data dictionary as a separate reference source.
4. Create the Monthly Active Users worksheet.
5. Apply `Active Flag = 1`.
6. Aggregate `User ID` using `COUNTD`.
7. Use continuous `Month` for the trend.
8. Create the departmental adoption worksheet.
9. Configure the departmental ranking and target-gap encoding.
10. Create the value-vs-cost scatter plot.
11. Map Total Cost USD, Estimated Value USD, Messages, Tool Category, and Tool to the appropriate shelves and Marks properties.
12. Add Avg. Cost and Avg. Value reference lines at Table scope.
13. Create the three KPI worksheets.
14. Add the KPI worksheets to a horizontal dashboard container.
15. Add the analytical worksheets beneath the KPI layer.
16. Standardize axes, titles, percentage formatting, and currency formatting.
17. Publish the workbook to Tableau Public.
18. Validate the public interactive view.

For the detailed manual sequence, use the 127-page walkthrough included in the repository.

---

## Technology Stack

- **Tableau Public**
- **Tableau Calculated Fields**
- **CSV**
- **Data Visualization**
- **Business Intelligence**
- **Analytics**
- **GitHub**

---
