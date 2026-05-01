# 📊 Datasets Documentation

This repository contains structured Excel and CSV datasets for hands-on learning.

All datasets are located inside the following directory:

```bash
/ExcelDataset
```

---

## 📁 Dataset Index

| Dataset Name              | File Path                                        | Level        |
| ------------------------- | ------------------------------------------------ | ------------ |
| Books Dataset             | `ExcelDataset/BookInfo.csv`                      | Beginner     |
| Customer Purchase History | `ExcelDataset/Customer-Purchase-History.xlsx`    | Beginner     |
| Inventory Tracking        | `ExcelDataset/Inventory-Tracking.xlsx`           | Beginner     |
| Online Store Orders       | `ExcelDataset/Online-Store-Orders.xlsx`          | Intermediate |
| Product Sales by Region   | `ExcelDataset/Product-Sales-Region.xlsx`         | Intermediate |
| Retail Store Transactions | `ExcelDataset/Retail-Store-Transactions.xlsx`    | Intermediate |
| Ecommerce Sales (England) | `ExcelDataset/EcommerceSalesDatasetEngland.xlsx` | Advanced     |
| Titanic Dataset           | `ExcelDataset/titanic.csv`                       | Advanced     |

---

## 🟢 Beginner Datasets

### 📘 Books Dataset

**File:** `ExcelDataset/BookInfo.csv`

**Overview**
Contains bibliographic information about books.

**Columns**

* ISBN
* BookTitle
* BookAuthor
* YearOfPublication
* Publisher

---

### 🛒 Customer Purchase History

**File:** `ExcelDataset/Customer-Purchase-History.xlsx`

**Overview**
Customer-level purchase transactions.

**Columns**

* CustomerID
* CustomerName
* Product
* ProductCategory
* PurchaseDate
* Quantity
* UnitPrice
* TotalPrice
* PaymentMethod
* ReviewRating

---

### 📦 Inventory Tracking

**File:** `ExcelDataset/Inventory-Tracking.xlsx`

**Overview**
Tracks product stock and supplier information.

**Columns**

* ProductID
* ProductName
* QuantityInStock
* ReorderPoint
* Supplier
* SupplierContact
* LeadTime
* StorageLocation
* UnitCost

---

## 🟡 Intermediate Datasets

### 🧾 Online Store Orders

**File:** `ExcelDataset/Online-Store-Orders.xlsx`

**Overview**
E-commerce order dataset with customer and logistics details.

**Columns**

* OrderID
* Date
* CustomerID
* Product
* Quantity
* UnitPrice
* TotalPrice
* ShippingAddress
* PaymentMethod
* OrderStatus
* TrackingNumber
* ItemsInCart
* CouponCode
* ReferralSource

---

### 🌍 Product Sales by Region

**File:** `ExcelDataset/Product-Sales-Region.xlsx`

**Overview**
Sales performance across different regions and teams.

**Columns**

* Date
* Region
* Product
* Quantity
* UnitPrice
* TotalPrice
* Discount
* PaymentMethod
* Promotion
* Returned
* CustomerName
* ShippingCost
* OrderDate
* DeliveryDate
* StoreLocation
* CustomerType
* Salesperson
* RegionManager

---

### 🏪 Retail Store Transactions

**File:** `ExcelDataset/Retail-Store-Transactions.xlsx`

**Overview**
Point-of-sale transaction records.

**Columns**

* Date
* Time
* StoreID
* Location
* Product
* Quantity
* UnitPrice
* TotalPrice
* PaymentType
* TransactionID
* Cashier
* StoreManager
* TimeOfDay
* DayOfWeek

---

## 🔴 Advanced Datasets

### 📊 Ecommerce Sales (England)

**File:** `ExcelDataset/EcommerceSalesDatasetEngland.xlsx`

**Overview**
Large-scale dataset (~51K rows) for advanced analytics.

**Columns**

* Order ID
* Order Date
* Ship Date
* Aging
* Ship Mode
* Product Category
* Product
* Sales
* Quantity
* Discount
* Profit
* Shipping Cost
* Order Priority
* Customer ID
* Customer Name
* Segment
* City
* State
* Country
* Region
* Months

---

### 🚢 Titanic Dataset

**File:** `ExcelDataset/titanic.csv`

**Overview**
Classic dataset for analysis and data cleaning.

**Columns**

* PassengerId
* Survived
* Pclass
* Name
* Sex
* Age
* SibSp
* Parch
* Ticket
* Fare
* Cabin
* Embarked

---

## ⚙️ Usage Notes

* All datasets are ready for Excel or CSV import
* No preprocessing required for basic practice
* Suitable for formulas, pivot tables, and dashboards

---

## 🎯 Objective

Provide a structured, real-world dataset collection for learning Excel through practical application.
