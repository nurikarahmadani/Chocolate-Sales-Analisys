# Chocolate-Sales-Analisys
The data analysis for this project was completed using SQL, while the visualization was implemented with Power BI.

## Database Preparation
```sql
CREATE DATABASE choco_db

CREATE TABLE choco_sales(
	sales_person VARCHAR(100),
	country VARCHAR(100),
	product_name VARCHAR(100),
	trank_date DATE,
	amount VARCHAR(100),
	boxes_shipped INT
)

BULK INSERT choco_sales
FROM 'C:\Users\NURIKA RAHMADANI\OneDrive - Balikpapan Cerdas\Data Analyst\Project\Chocolate Sales\Chocolate_Sales.csv'
WITH(
	FORMAT = 'CSV',
	FIRSTROW = 2,
	FIELDTERMINATOR = ',',
	ROWTERMINATOR = '\n',
	CODEPAGE = '1252'
)

SELECT * FROM choco_sales
WHERE 
	sales_person IS NULL
	OR country IS NULL
	or product_name IS NULL
	or trank_date IS NULL
	or amount IS NULL
	or boxes_shipped IS NULL

UPDATE choco_sales
SET amount = REPLACE(amount,'$','')

UPDATE choco_sales
SET amount = REPLACE(amount,',','')

ALTER TABLE choco_sales
ALTER COLUMN amount INT
```
