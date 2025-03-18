# MIST 4610 Group 7 Project Submissio

## Team Number and Members
- **Team Number:** Group 7
- **Members:**
  - Wilson Nguyen (https://github.com/dakarie/MIST-4610-Group-7-Project/blob/main/README.md)
  - Akshaya Ezhil
  - Justen Newsom
  - Shahil Patel
  - Josh Gershon

## Scenario Description
Our client owns and operates multiple Dunkin’ Donuts locations across Georgia and requires a comprehensive database system to manage and track various aspects of their business operations. The client has enlisted students from MIST 4610 to design and implement a database solution that will help streamline store management, improve customer service, and enhance operational efficiency.

The database will track the following key areas:
1. **Customer Information**  
2. **Mobile App Integration**  
3. **Store Locations**  
4. **Employee Management**  
5. **Promotions and Discounts**  
6. **Menu and Inventory Management**  
7. **Order Tracking**  
8. **Payment Processing**  


## Data Model
![Data Model](https://github.com/user-attachments/assets/3a41b1c8-8421-435d-9f42-adc8c6933221)

[Explain your data model here. Describe the relationships between the entities and what kind of data your database supports.]

# Data Dictionary

### Table: CustomerOrder

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| Customer_OrderID     | Unique identifier for each customer order        | INT       |      |        | PK   |
| CustomerID           | Identifier linking to the customer               | INT       |      |        | FK   |
| OrderDate            | Date of the order                                | DATE      |      | YYYY-MM-DD |      |
| OrderTime            | Time of the order                                | TIME      |      | HH:MM:SS |      |
| OrderType            | Type of order (In-Store, Mobile, Drive-Thru)     | ENUM      |      |        |      |

### Table: Customer_Payments

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| PaymentID            | Unique identifier for each payment               | INT       |      |        | PK   |
| OrderID              | Identifier linking to the order                  | INT       |      |        | FK   |
| PaymentAmount        | Amount paid                                      | DECIMAL   | 10,2 |        |      |
| PaymentDate          | Date of the payment                              | DATE      |      | YYYY-MM-DD |      |
| PaymentMethod        | Method of payment (Cash, Credit, Debit, MobilePay) | ENUM      |      |        |      |

### Table: Customers

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| CustomerID           | Unique identifier for each customer              | INT       |      |        | PK   |
| CustomerName         | Full name of the customer                        | VARCHAR   | 255  |        |      |
| CustomerEmail        | Email address of the customer                    | VARCHAR   | 255  |        |      |
| CustomerPhoneNumber  | Phone number of the customer                     | VARCHAR   | 20   | (999)999-9999 |      |

### Table: Employees

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| EmployeeID           | Unique identifier for each employee              | INT       |      |        | PK   |
| EmployeeName         | Full name of the employee                        | VARCHAR   | 255  |        |      |
| Location_LocationID  | Identifier linking to the location               | INT       |      |        | FK   |

### Table: In_Store_Promotions

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| Promotions_PromotionID | Identifier linking to the promotion             | INT       |      |        | PK, FK |
| Location_LocationID  | Identifier linking to the location               | INT       |      |        | PK, FK |

### Table: Inventory

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| InventoryID          | Unique identifier for each inventory item        | INT       |      |        | PK   |
| StockQuantity        | Quantity of stock available                      | INT       |      |        |      |
| LastUpdated          | Timestamp of the last update                     | TIMESTAMP |      | YYYY-MM-DD HH:MM:SS |      |

### Table: Location

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| LocationID           | Unique identifier for each location              | INT       |      |        | PK   |
| StoreName            | Name of the store                                | VARCHAR   | 255  |        |      |
| Address              | Physical address of the store                    | VARCHAR   | 255  |        |      |
| City                 | City where the store is located                  | VARCHAR   | 100  |        |      |
| State                | State where the store is located                 | VARCHAR   | 50   |        |      |
| ZipCode              | ZIP code of the store                            | VARCHAR   | 10   |        |      |

### Table: Menu

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| MenuID               | Unique identifier for each menu category         | INT       |      |        | PK   |
| Category             | Category of the menu item                        | VARCHAR   | 100  |        |      |

### Table: Mobile_App_Account

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| AppID                | Unique identifier for each mobile app account    | INT       |      |        | PK   |
| CustomerID           | Identifier linking to the customer               | INT       |      |        | FK   |
| DeviceType           | Type of device (iOS or Android)                  | ENUM      |      |        |      |
| AppVersion           | Version of the mobile app                        | VARCHAR   | 50   |        |      |

### Table: Products

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| ProductID            | Unique identifier for each product               | INT       |      |        | PK   |
| ProductName          | Name of the product                              | VARCHAR   | 255  |        |      |
| ProductPrice         | Price of the product                             | DECIMAL   | 10,2 |        |      |
| Menu_MenuID          | Identifier linking to the menu category          | INT       |      |        | FK   |
| Inventory_InventoryID| Identifier linking to the inventory item         | INT       |      |        | FK   |

### Table: Products_has_CustomerOrder

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| Products_ProductID   | Identifier linking to the product                | INT       |      |        | PK, FK |
| CustomerOrder_Customer_OrderID | Identifier linking to the customer order | INT       |      |        | PK, FK |
| Quantity             | Quantity of the product ordered                  | VARCHAR   | 45   |        |      |

### Table: Products_has_Promotions

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| Products_ProductID   | Identifier linking to the product                | INT       |      |        | PK, FK |
| Promotions_PromotionID | Identifier linking to the promotion             | INT       |      |        | PK, FK |

### Table: Promotions

| Column Name          | Description                                      | Data Type | Size | Format | Key? |
|----------------------|--------------------------------------------------|-----------|------|--------|------|
| PromotionID          | Unique identifier for each promotion             | INT       |      |        | PK   |
| PromotionName        | Name of the promotion                            | VARCHAR   | 255  |        |      |
| DiscountPercentage   | Discount percentage offered by the promotion     | DECIMAL   | 5,2  |        |      |
| StartDate            | Start date of the promotion                      | DATE      |      | YYYY-MM-DD |      |
| EndDate              | End date of the promotion                        | DATE      |      | YYYY-MM-DD |      |

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

- **Database Name:** `al_Group_21484_G7`

| Query Complexity Feature       | Query 1 | Query 2 | Query 3 | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 |
|-------------------------------|---------|---------|---------|---------|---------|---------|---------|---------|---------|----------|
| Multiple Table Join            |         |         |         |         |         |         |         |         |         |          |
| Traditional Subquery           |         |         |         |         |         |         |         |         |         |          |
| Correlated Subquery            |         |         |         |         |         |         |         |         |         |          |
| GROUP BY                       |         |         |         |         |         |         |         |         |         |          |
| GROUP BY with HAVING           |         |         |         |         |         |         |         |         |         |          |
| Multi-Condition WHERE          |         |         |         |         |         |         |         |         |         |          |
| Built-in Functions (e.g., AVG) |         |         |         |         |         |         |         |         |         |          |
| Calculated Field               |         |         |         |         |         |         |         |         |         |          |
| REGEXP                         |         |         |         |         |         |         |         |         |         |          |
| NOT EXISTS                     |         |         |         |         |         |         |         |         |         |          |

