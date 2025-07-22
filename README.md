# 📦 AI-Driven End-to-End Supply Chain Analytics Project

---

## 🚀 Project Overview

We simulate a scenario for **Atlique Mart**, a growing organic food manufacturer expanding into the US and India, and tackle classic order fulfillment and inventory problems using an integrated AI stack. If you're seeking practical experience with workflow automation, AI analytics, and supply chain KPIs—all in one project—this is the repository for you!

---

## 🏆 Why This Project Stands Out

- **Real-World Data Simulation:** Automates email-based data ingestion (mirroring actual business flows).
- **Modern AI Tooling:** Leverages N8N (workflow automation), Supabase (PostgreSQL cloud DB), and Quadratic (AI spreadsheet analytics).
- **Prompt-Driven Analytics:** Enables natural language queries, business Q&A, and on-the-fly KPI calculations with no-code/low-code AI.
- **Supply Chain Domain Depth:** Teaches must-know supply chain metrics (e.g., OTIF, fill rates, reliability) using hands-on data.
- **Portfolio-Ready:** Clean, production-like pipeline you can showcase to employers—demonstrates both technical and domain expertise.

---


## 🧰 Project Architecture

```text
            [Email Inbox with CSVs]
                      ↓
          +------------------------+
          |        N8N            |
          |  Automates email → CSV|
          |  Converts to JSON     |
          |  Uploads to Supabase  |
          +------------------------+
                      ↓
         +-------------------------+
         |     Supabase DB        |
         | (PostgreSQL on Cloud)  |
         +-------------------------+
                      ↓
         +-------------------------+
         |       Quadratic         |
         | AI Spreadsheet + Prompts|
         | Merge, Clean, Analyze   |
         +-------------------------+


- **Data Entry:** Supply chain data arrives as CSV attachments via email (mimics real-world vendor/customer workflows).
- **Automation:** N8N monitors a Gmail inbox, processes the attachments, cleans/transforms data, and inserts into PostgreSQL (cloud-hosted via Supabase).
- **AI Analytics:** Quadratic connects directly to the database; all analytics and KPIs are performed via prompt-driven, Python-powered spreadsheets.
- **Visualization & Q&A:** Business users can ask questions in plain English and receive both tabular and visual insights instantly.

---

## 💡 Key Technologies Used

- **N8N**: Open-source, agentic workflow automation (https://n8n.io/)
- **Supabase**: Managed PostgreSQL cloud database (https://supabase.com/)
- **Quadratic**: AI spreadsheet with natural language and code-based analytics (https://www.quadratichq.com/)
- **Python & Pandas**: Used within Quadratic for advanced data processing and transformation
- **Open Exchange Rates API**: For real-time currency conversion (USD/INR)

---

## 🏢 Business Problem & Domain

**Atlique Mart** is facing order management and inventory issues as it scales to new geographies. Supermarkets in India and the US report order fulfillment delays and discrepancies. The COO wants to leverage *AI-powered analytics* to identify bottlenecks, monitor KPIs, and improve supply chain reliability **before scaling further**.

This scenario is modeled after real supply chain challenges faced by growing manufacturers globally.

---

## 📈 Supply Chain KPIs Implemented

| KPI                        | Description                                                      | Business Impact                                         |
|----------------------------|------------------------------------------------------------------|---------------------------------------------------------|
| **Total Orders**           | Unique order count                                               | Demand tracking, sales pipeline                         |
| **Line Fill Rate**         | % of order lines delivered in full                               | Measures order completeness at item level               |
| **Volume Fill Rate**       | % of total quantity delivered                                    | Ensures bulk fulfillment, reduces shortages             |
| **On-Time Delivery %**     | % of orders delivered on or before agreed delivery date          | Tracks delivery reliability                             |
| **In-Full Rate**           | % of orders with all items delivered in correct quantity         | Tracks delivery accuracy                                |
| **OTIF**                   | % of orders delivered on time AND in full                        | Gold-standard supply chain reliability metric           |
| **Reliability**            | Alias for OTIF, often used in contracts/SLAs                     | Customer retention, negotiation leverage                |

---

## 🔄 Step-by-Step Workflow

### 1. **Email Data Ingestion**
- CSV files with sales and order line data are sent as attachments (India/US branches).
- Files: `india_aggregate.csv`, `india_orderline.csv`, `usa_aggregate.csv`, `usa_orderline.csv`

### 2. **N8N Automation**
- Workflow monitors Gmail for subject ("daily sales"), filters relevant emails, extracts attachments.
- Parses CSVs, converts dates/formats as required, maps fields to DB schema.
- Inserts data into **Supabase PostgreSQL** using secure API.

### 3. **Database Modeling**
- Star schema: Fact tables (orders, order_lines), dimension tables (customers, products, dates, targets).
- Setup scripts provided in `/docs/setup_supabase.pdf`

### 4. **Quadratic AI Analytics**
- Connects to Supabase with DB credentials.
- Uses supplied prompts to:
    - Pull tables (dim/fact)
    - Generate a date dimension (`dim_date`)
    - Pull currency rates (USD/INR) with Open Exchange Rates API
    - Merge/clean all data into a denormalized summary
    - Calculate KPIs & generate charts using plain English prompts

### 5. **Business Insights (Prompt-Driven)**
- Ask questions like:
    - "Show me monthly on-time performance by city"
    - "Who are the top 5 customers by order value and OTIF?"
    - "Compare volume fill rates between India and USA"
- AI generates charts, tables, and code automatically.

---

## 📋 Sample Prompts & Insights

```text
Calculate the line fill rate, volume fill rate, on-time delivery %, in-full %, and OTIF for each city and product over the past quarter.
