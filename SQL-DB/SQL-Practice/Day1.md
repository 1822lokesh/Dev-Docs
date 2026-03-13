
# SQL Practice – Day 1

## Create Database

```sql
CREATE DATABASE IF NOT EXISTS Day1;
USE Day1;
````

---

## Create Table: Users

```sql
CREATE TABLE users (
    users_id INT PRIMARY KEY,
    username VARCHAR(30),
    join_date DATE,
    country VARCHAR(30)
);
```

---

## Create Table: Datasets

```sql
CREATE TABLE datasets (
    dataset_id INT PRIMARY KEY,
    seller_id INT,
    dataset_name VARCHAR(20),
    price DECIMAL(8,2),
    file_size INT,
    FOREIGN KEY (seller_id) REFERENCES users(users_id)
);
```

---

## Insert Data into Users

```sql
INSERT INTO users (users_id, username, join_date, country) VALUES
(1, 'Lokesh', '2023-01-15', 'India'),
(2, 'Amit', '2023-03-20', 'India'),
(3, 'John', '2022-11-05', 'USA'),
(4, 'Sara', '2024-02-10', 'UK'),
(5, 'Chen', '2025-09-18', 'China'),
(6, 'Adam', '2026-01-05', 'Japan'),
(7, 'Bob', '2022-02-10', 'UK'),
(8, 'Ket', '2021-07-18', 'AUS');
```

---

## Insert Data into Datasets

```sql
INSERT INTO datasets (dataset_id, seller_id, dataset_name, price, file_size) VALUES
(101, 1, 'Sales Data 2023', 49.99, 500),
(102, 2, 'Customer Analytics', 79.50, 750),
(103, 1, 'Product Inventory', 35.00, 300),
(104, 3, 'Market Research', 125.00, 950),
(105, 4, 'Financial Forecast', 89.99, 650),
(106, 6, 'Social Media Trends', 60.00, 400),
(107, 1, 'Supply-Chain', 45.00, 600),
(108, 3, 'Bitcoin', 120.00, 450),
(109, 7, 'Customer Analytics', 99.99, 330),
(110, 5, 'Social Media Trends', 90.00, 450);
```

---

## Practice Queries

#### 1. Write a query to fetch the dataset_name and price of all datasets available in the Datasets table.

```sql
SELECT dataset_name, price
FROM datasets;
```

---

#### 2. We need to audit our free tier. Write a query to find all datasets where the price is exactly 0.

```sql
SELECT *
FROM datasets
WHERE price = 0;
```

---

#### 3. Write a query to find all users from "India" who joined after '2025-01-01'.

```sql
SELECT *
FROM users
WHERE country = 'India'
AND join_date > '2025-01-01';
```

---

#### 4. A user is looking for a specific file but only remembers it started with "Crypto". Write a query to find the dataset_name of all datasets that begin with the word "Crypto".

```sql
SELECT dataset_name
FROM datasets
WHERE dataset_name LIKE 'Crypto%';
```

---

#### 5. We want to feature our heaviest datasets. Write a query to find the top 3 datasets with the largest file_size_mb, returning their names and sizes.

```sql
SELECT dataset_name, file_size
FROM datasets
ORDER BY file_size DESC
LIMIT 3;
```

---

