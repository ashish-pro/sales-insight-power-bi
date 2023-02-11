# sales-insight-power-bi

Instructions to setup mysql on your local computer

SQL database dump is in db_dump.sql file above. Download db_dump.sql file to your local computer and import it.

## Data-Analysis-Using-SQL

**1. Show all customer records**

_SELECT * FROM customers;_


**2. Show total number of customers**

_SELECT count(*) FROM customers;_

**3.Show transactions for Chennai market (market code for chennai is Mark001)**

_SELECT * FROM transactions where market_code='Mark001';_

**4.Show distrinct product codes that were sold in chennai**

_SELECT distinct product_code FROM transactions where market_code='Mark001';_

**5.Show transactions where currency is US dollars**

_SELECT * from transactions where currency="USD"_

**6.Show transactions in 2020 join by date table**

_SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;_

**7.Show total revenue in year 2020,**

_SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";_

**8. Show total revenue in year 2020, January Month,**

_SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");_

**9.Show total revenue in year 2020 in Chennai**

_SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";_

## Dax-Formua-Used-in-Power-BI

**1. Formula to create norm_amount column**

_= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)_
