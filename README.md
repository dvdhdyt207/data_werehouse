
# 📊 Superstore Data Warehouse Project

## 🗂️ Project Description

This project builds a **Data Warehouse** system based on the *Superstore Order* dataset to support business analysis. The ETL process is performed using **Pentaho Data Integration (Kettle)**, data is stored in **MySQL**, and data visualization is done using **Microsoft Power BI**.

The dataset covers order transactions from **2011–2014**, with shipping processes extending to **2015**.

---

## 🛠️ Tools & Technologies

- **Pentaho Data Integration (PDI)**: For Extract, Transform, Load (ETL) processes
- **MySQL**: As the OLAP database to store the data warehouse
- **Power BI**: For visualization and reporting
- **Dataset**: Sample Superstore (CSV format)

---

## 🏗️ Data Warehouse Structure

### ✅ Dimension Tables

| Table Name     | Description                           |
|----------------|---------------------------------------|
| `dim_customer` | Stores customer information           |
| `dim_product`  | Stores product information            |
| `dim_location` | Stores shipping location (country, city, state) |
| `dim_time`     | Stores time information (date, month, year, quarter, etc.) |
| `dim_shipping` | Stores shipping method                |
| `dim_priority` | Stores order priority levels          |

### ✅ Fact Table

| Table Name   | Description                                             |
|--------------|---------------------------------------------------------|
| `fact_order` | Stores transactional data including sales, profit, quantity, shipping cost, and foreign keys to all dimensions |

---

## 🔄 ETL Flow

1. **Extract**: Extract data from Superstore Order CSV file
2. **Transform**: Cleanse data, generate unique keys for dimensions, convert date fields
3. **Load**:
   - Load dimension tables first
   - Then populate the fact table (`fact_order`) using the corresponding foreign keys

All transformations and jobs are managed using **Pentaho PDI (Kettle)**.

---

## 📈 Power BI Visualizations

The dashboard includes:

- Sales by year, month, and quarter
- Profit by region and product category
- Shipping performance by shipping mode
- Order priority analysis vs revenue
- Interactive customer location map

---

## 📁 Folder Structure (optional)

```bash
SuperstoreDW/
├── data/
│   └── superstore_orders.csv
├── pentaho/
│   ├── dim_customer.ktr
│   ├── dim_time.ktr
│   ├── fact_order.ktr
│   └── main_job.kjb
├── sql/
│   ├── create_tables.sql
│   └── insert_sample.sql
├── powerbi/
│   └── dashboard.pbix
└── README.md
```

---

## ⚙️ How to Run This Project

1. **Import Data**: Ensure MySQL is running, then run `create_tables.sql`
2. **Run ETL**: Open Pentaho Spoon and run `main_job.kjb` to execute the full ETL process
3. **Visualization**: Open `dashboard.pbix` with Power BI

---

## 📝 Notes

- Ensure date formats in source data are consistent with `dim_time` structure
- Verify data type compatibility between foreign keys to avoid errors in fact table creation (e.g., `VARCHAR(8)` for `order_date` if `date_key` is also `VARCHAR(8)`)

---

## 👤 Author

**Name**: [Your Name]  
**Email**: [Your Email]  
**Major**: Computer Science / Information Systems  
**Topic**: Data Warehouse and Business Intelligence
