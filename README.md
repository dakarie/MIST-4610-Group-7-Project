# MIST 4610 Group 7 Project Submission

## Team Number and Members
- **Team Number:** Group 7
- **Members:**
  - Wilson Nguyen (https://github.com/dakarie/MIST-4610-Group-7-Project/blob/main/README.md)
  - Akshaya Ezhil
  - Justen Newsom
  - Shahil Patel
  - Josh Gershon

## Scenario Description
[Provide a detailed description of the scenario you are modeling. This should include the context of your data model and any relevant discussions with your team or instructor.]

## Data Model
![Data Model](https://github.com/user-attachments/assets/3a41b1c8-8421-435d-9f42-adc8c6933221)

[Explain your data model here. Describe the relationships between the entities and what kind of data your database supports.]

## Data Dictionary

#### Table: **Products_has_Promotions**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| Products_ProductID      | Foreign key referencing the ProductID in the Products table                 | INT         |      |        | FK (ref_Products)   |
| Promotions_PromotionID  | Foreign key referencing the PromotionID in the Promotions table              | INT         |      |        | FK (ref_Promotions) |

---

#### Table: **Products**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| ProductID              | Unique identifier for each product                                          | INT         |      |        | PK                  |
| ProductName            | Name of the product                                                        | VARCHAR     | 255  |        |                     |
| ProductPrice           | Price of the product                                                       | DECIMAL     | 10,2 |        |                     |
| Menu_MenuID            | Foreign key referencing the MenuID in the Menu table                        | INT         |      |        | FK (ref_Menu)       |
| Inventory_InventoryID  | Foreign key referencing the InventoryID in the Inventory table              | INT         |      |        | FK (ref_Inventory)  |

---

#### Table: **Inventory**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| InventoryID            | Unique identifier for each inventory item                                   | INT         |      |        | PK                  |
| StockQuantity          | Quantity of the product in stock                                            | INT         |      |        |                     |
| LastUpdated            | Timestamp of when the inventory was last updated                           | TIMESTAMP   |      |        |                     |

---

#### Table: **Menu**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| MenuID                 | Unique identifier for each menu category                                    | INT         |      |        | PK                  |
| Category               | Category of the menu (e.g., Breakfast, Beverages)                           | VARCHAR     | 100  |        |                     |

---

#### Table: **Promotions**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| PromotionID            | Unique identifier for each promotion                                        | INT         |      |        | PK                  |
| PromotionName          | Name of the promotion                                                      | VARCHAR     | 255  |        |                     |
| DiscountPercentage     | Percentage discount offered by the promotion                                | DECIMAL     | 5,2  |        |                     |
| StartDate              | Start date of the promotion                                                | DATE        |      |        |                     |
| EndDate                | End date of the promotion                                                  | DATE        |      |        |                     |

---

#### Table: **Products_has_CustomerOrder**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| Products_ProductID      | Foreign key referencing the ProductID in the Products table                 | INT         |      |        | FK (ref_Products)   |
| CustomerOrder_Customer_OrderID | Foreign key referencing the Customer_OrderID in the CustomerOrder table | INT         |      |        | FK (ref_CustomerOrder) |
| Quantity               | Quantity of the product ordered                                            | VARCHAR     | 45   |        |                     |

---

#### Table: **Customer_Payments**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| PaymentID              | Unique identifier for each payment                                          | INT         |      |        | PK                  |
| OrderID                | Foreign key referencing the OrderID in the CustomerOrder table              | INT         |      |        | FK (ref_CustomerOrder) |
| PaymentAmount          | Amount paid for the order                                                  | DECIMAL     | 10,2 |        |                     |
| PaymentDate            | Date of the payment                                                        | DATE        |      |        |                     |
| PaymentMethod          | Method of payment (e.g., Credit Card, Cash)                                | ENUM        |      |        |                     |

---

#### Table: **Customers**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| CustomerID             | Unique identifier for each customer                                         | INT         |      |        | PK                  |
| CustomerName           | Name of the customer                                                       | VARCHAR     | 255  |        |                     |
| CustomerEmail          | Email address of the customer                                              | VARCHAR     | 255  |        |                     |
| CustomerPhoneNumber    | Phone number of the customer                                               | VARCHAR     | 20   |        |                     |

---

#### Table: **Location**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| LocationID             | Unique identifier for each location                                         | INT         |      |        | PK                  |
| StoreName              | Name of the store                                                          | VARCHAR     | 255  |        |                     |
| Address                | Address of the store                                                       | VARCHAR     | 255  |        |                     |
| City                   | City where the store is located                                            | VARCHAR     | 100  |        |                     |
| State                  | State where the store is located                                           | VARCHAR     | 50   |        |                     |
| ZipCode                | Zip code of the store                                                      | VARCHAR     | 10   |        |                     |

---

#### Table: **Employees**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| EmployedID             | Unique identifier for each employee                                         | INT         |      |        | PK                  |
| EmployeeName           | Name of the employee                                                       | VARCHAR     | 255  |        |                     |
| Location_LocationID    | Foreign key referencing the LocationID in the Location table                | INT         |      |        | FK (ref_Location)   |

---

#### Table: **Mobile_App_Account**
| Column Name            | Description                                                                 | Data Type   | Size | Format | Key?                |
|------------------------|-----------------------------------------------------------------------------|-------------|------|--------|---------------------|
| AppID                  | Unique identifier for each mobile app account                               | INT         |      |        | PK                  |
| CustomerID             | Foreign key referencing the CustomerID in the Customers table               | INT         |      |        | FK (ref_Customers)  |
| DeviceType             | Type of device used for the app (e.g., iOS, Android)                        | ENUM        |      |        |                     |
| Application            | Version of the mobile application                                          | VARCHAR     | 50   |        |                     |

---

### Notes:
- **PK**: Primary Key
- **FK**: Foreign Key
- **ref_TableName**: Indicates the table being referenced by the foreign key.

## Ten Queries
1. **Query 1:**
   - **Description:** [Describe the query in natural language.]
   - **Justification:** [Explain why this query is relevant from a managerial perspective.]
   - **SQL Code:**
     ```sql
     [Insert SQL code here]
     ```
   - **Query Response:**
     ```
     [Insert query response here]
     ```

2. **Query 2:**
   - **Description:** [Describe the query in natural language.]
   - **Justification:** [Explain why this query is relevant from a managerial perspective.]
   - **SQL Code:
     ```sql
     [Insert SQL code here]
     ```
   - **Query Response:**
     ```
     [Insert query response here]
     ```

## Database Information
- **Database Name:** `[Your Database Name]`
- **Key Tables:** `[Table 1]`, `[Table 2]`, `[Table 3]`
- **Stored Procedures:** All queries are implemented as stored procedures named `TP_Qx` (where `x` is the query number). See the [Queries Section](#ten-queries) for details.
