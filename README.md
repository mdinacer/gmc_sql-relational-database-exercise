# SQL Relational Database Exercise

## Create the Relational Model

### Step 1: Create Tables with Constraints

```sql
-- Product Table
CREATE TABLE Product (
    Product_id     VARCHAR2(20) PRIMARY KEY,
    Product_Name   VARCHAR2(20) NOT NULL,
    Price          NUMBER CHECK (Price > 0)
);

-- Customer Table
CREATE TABLE Customer (
    Customer_id    VARCHAR2(20) PRIMARY KEY,
    Customer_Name  VARCHAR2(20) NOT NULL,
    Customer_Tel   NUMBER
);

-- Orders Table
CREATE TABLE Orders (
    Customer_id    VARCHAR2(20),
    Product_id     VARCHAR2(20),
    Quantity       NUMBER,
    Total_amount   NUMBER,
    CONSTRAINT fk_customer FOREIGN KEY (Customer_id)
        REFERENCES Customer(Customer_id),
    CONSTRAINT fk_product FOREIGN KEY (Product_id)
        REFERENCES Product(Product_id)
);
```

### Step 2: Required Modifications

#### Add Category column to PRODUCT table
```sql
ALTER TABLE Product
ADD Category VARCHAR2(20);
```

#### Add OrderDate column to ORDERS table with SYSDATE default
```sql
ALTER TABLE Orders
ADD OrderDate DATE DEFAULT SYSDATE;
```
