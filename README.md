# MIST 4610 Group 7 Project One Submission

# Team Number and Members
- **Team Number:** Group 7
- **Members:**
  - Wilson Nguyen (https://github.com/dakarie/MIST-4610-Group-7-Project/blob/main/README.md)
  - Akshaya Ezhil
  - Justen Newsom (https://github.com/justennewsom/MIST-4610-Group-7-Project-1/tree/main)
  - Shahil Patel
  - Josh Gershon

# Scenario Description
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


# Data Model
![Data Model](https://github.com/user-attachments/assets/3a41b1c8-8421-435d-9f42-adc8c6933221)

### Overview
This database system is designed to manage and track various aspects of Dunkin’ Donuts operations across multiple locations in Georgia. It aims to streamline store management, improve customer service, and enhance operational efficiency.

### Key Areas Tracked
- **Products and Promotions**: Tracks discounts and promotions applied to specific products.
- **Inventory Management**: Monitors stock levels and updates to ensure efficient stock management.
- **Menu Organization**: Categorizes products to help organize offerings by type or category.
- **Customer Orders and Payments**: Manages customer orders and payment details, linking them to specific customers and payment methods.
- **Customer Information**: Stores customer details and mobile app usage to enhance customer service.
- **Store and Employee Management**: Tracks store locations and employee assignments to aid in operational management.

### Entity Relationships
- **Products** are linked to **Promotions** through the `Products_has_Promotions` table.
- **Inventory** levels are monitored and updated in the `Inventory` table.
- **Menu** items are categorized in the `Menu` table.
- **Customer Orders** and **Payments** are tracked in the `CustomerOrder` and `Customer_Payments` tables.
- **Customer** details and app usage are managed in the `Customers` and `Mobile_App_Account` tables.
- **Store Locations** and **Employee** assignments are recorded in the `Location` and `Employees` tables.

This integrated database system supports efficient operations and improved customer service across all locations.

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

# Ten Queries
1. **Query 1: (Simple)**
   - **Description:** Compute the average revenue per order type by grouping all customer payments based on how the order was placed — either In-Store, Mobile, or Drive-Thru.
   - **Justification:** This information helps management understand which ordering channels generate more value per transaction. If one type (e.g., In-Store) consistently brings in higher averages, it may be worth increasing staffing during peak in-store hours or promoting that experience. Alternatively, if mobile orders are underperforming, this could signal the need for better app UX, exclusive mobile offers, or technical improvements.
   - **SQL Code:**
     ```sql
     SELECT 
         co.OrderType,
         AVG(cp.PaymentAmount) AS AvgPayment
     FROM 
         CustomerOrder co
     JOIN Customer_Payments cp ON co.Customer_OrderID = cp.OrderID
     GROUP BY 
         co.OrderType;
     ```
   - **Query Response:**
     ```
     OrderType     | AvgPayment
     ------------- | -----------
     In-Store      | 3.850000
     Mobile        | 3.071429
     Drive-Thru    | 3.125000
     ```

2. **Query 2: (Simple)**
   - **Description:** Lists the names of customers who placed orders during active promotion periods, along with the order date and the name of the promotion that was running at the time.
   - **Justification:** This query helps management evaluate how effective promotions are at driving customer engagement. By identifying who places orders during promotions, managers can:
- Track which deals generate the most activity
- Target responsive customers for future campaigns
- Optimize promotion timing and product bundles
   - **SQL Code:**
     ```sql
     SELECT DISTINCT 
         c.CustomerName, co.OrderDate, pr.PromotionName
     FROM 
         CustomerOrder co
     JOIN Customers c ON co.CustomerID = c.CustomerID
     JOIN Products_has_CustomerOrder phco ON co.Customer_OrderID = phco.CustomerOrder_Customer_OrderID
     JOIN Products p ON phco.Products_ProductID = p.ProductID
     JOIN Products_has_Promotions php ON p.ProductID = php.Products_ProductID
     JOIN Promotions pr ON php.Promotions_PromotionID = pr.PromotionID
     WHERE 
         co.OrderDate BETWEEN pr.StartDate AND pr.EndDate;
     ```
   - **Query Response:**
     ```
      | CustomerName  | OrderDate  | PromotionName |
      |---------------|------------|---------------|
      | Emma Johnson  | 2025-03-14 | Spring Deal   |
      | Amelia King   | 2025-03-14 | Spring Deal   |
      | Sophia Green  | 2025-03-17 | Tea Time      |
      | Mila Baker    | 2025-03-17 | Tea Time      |
      | James Carter  | 2025-03-17 | Tea Time      |
      | Olivia Brown  | 2025-03-18 | Tea Time      |
      | Liam Smith    | 2025-03-18 | Tea Time      |
     ```
     
3. **Query 3: (Complex)**  
   - **Description:** Lists customers whose total spending is above the average payment amount across all customers.
   - **Justification:** Identifying high-spending customers helps managers recognize and reward top buyers, target them for exclusive deals or loyalty perks, and focus marketing efforts on customers who provide the greatest financial value to the business.
   - **SQL Code:**
     ```sql
     SELECT 
       c.CustomerName,
       SUM(cp.PaymentAmount) AS TotalSpent
     FROM 
       Customers c
     JOIN CustomerOrder co ON c.CustomerID = co.CustomerID
     JOIN Customer_Payments cp ON co.Customer_OrderID = cp.OrderID
     GROUP BY 
       c.CustomerID
     HAVING 
      	TotalSpent > (SELECT AVG(PaymentAmount) FROM Customer_Payments);
     ```
   - **Query Response:**
     ```
      | CustomerName    | TotalSpent |
      |-----------------|------------|
      | Emma Johnson    | 5.75       |
      | Liam Smith      | 4.00       |
      | Olivia Brown    | 8.50       |
      | Sophia Green    | 6.00       |
      | Benjamin Young  | 4.50       |
      | Elijah Adams    | 3.50       |
      | Mila Baker      | 3.50       |
     ```
     
4. **Query 4: (Simple)**  
   - **Description:** Calculates the total revenue generated per store location by summing all customer payments linked to orders from that location.
   - **Justification:** Understanding how much revenue each store location generates is essential for financial planning, inventory management, and identifying top-performing branches. This helps managers make informed decisions about resource allocation, staff scheduling, and localized marketing strategies.
   - **SQL Code:**  
     ```sql
     SELECT 
         l.StoreName, 
         SUM(cp.PaymentAmount) AS TotalRevenue
     FROM 
         Customer_Payments cp
     JOIN CustomerOrder co ON cp.OrderID = co.Customer_OrderID
     JOIN Customers c ON co.CustomerID = c.CustomerID
     JOIN Mobile_App_Account maa ON c.CustomerID = maa.CustomerID
     JOIN Location l ON l.LocationID IN (1, 2) 
     GROUP BY 
         l.LocationID;
     ```
   - **Query Response:**  
     ```
     | StoreName         | TotalRevenue |
     |-------------------|--------------|
     | Dunkin Athens     | 47.00        |
     | Dunkin Peachtree  | 47.00        |
     ```

5. **Query 5: (Simple)**  
   - **Description:** Displays all products whose current stock quantity is below the average inventory level across all products.
   - **Justification:** This query helps managers identify understocked products so they can prioritize reordering or replenishing. Keeping an eye on inventory levels ensures that high-demand items are always available and helps avoid lost sales due to stockouts.

   - **SQL Code:**  
     ```sql
     SELECT
         p.ProductName, i.StockQuantity
     FROM
         Products p
     JOIN Inventory i ON p.Inventory_InventoryID = i.InventoryID
     WHERE i.StockQuantity <
         (SELECT AVG(StockQuantity) FROM Inventory);  
     ```
   - **Query Response:**  
     ```
     | ProductName   | StockQuantity |
     |---------------|---------------|
     | Glazed Donut  | 100           |
     | Hash Browns   | 90            |
     | Muffin        | 40            |
     | Hot Chocolate | 130           |
     ```
     
6. **Query 6: (Complex)**  
   - **Description:** Displays the names, emails, and total spending of customers whose total purchase amount is greater than the average of all customer spending.
   - **Justification:** This query helps managers identify high-value customers who are spending more than the average shopper. These individuals are ideal candidates for VIP programs, personalized rewards, or targeted upselling, making this a powerful tool for loyalty management and promotional planning.
   - **SQL Code:**  
     ```sql
     SELECT
         c.CustomerName,
         c.CustomerEmail,
         SUM(cp.PaymentAmount) AS TotalSpent
     FROM
         Customers c
     JOIN CustomerOrder co ON c.CustomerID = co.CustomerID
     JOIN Customer_Payments cp ON co.Customer_OrderID = cp.OrderID
     GROUP BY
         c.CustomerID
     HAVING
         SUM(cp.PaymentAmount) > (
             SELECT AVG(TotalSpent)
             FROM (
                 SELECT SUM(cp.PaymentAmount) AS TotalSpent
                 FROM Customer_Payments cp
                 JOIN CustomerOrder co ON cp.OrderID = co.Customer_OrderID
                 GROUP BY co.CustomerID
             ) AS CustomerSpending
         );
     ```
   - **Query Response:**  
     ```
     | CustomerName  | CustomerEmail              | TotalSpent |
     |-------------- |----------------------------|------------|
     | Emma Johnson  | emma.johnson@example.com   | 5.75       |
     | Liam Smith    | liam.smith@example.com     | 4.00       |
     | Olivia Brown  | olivia.brown@example.com   | 8.50       |
     | Sophia Green  | sophia.green@example.com   | 6.00       |
     | Benjamin Young| benjamin.young@example.com | 4.50       |
     ```
7. **Query 7: (Complex)**  
   - **Description:** Displays the names, order count, and total spending of customers who have placed two or more orders and whose total spend is above the average single payment value.
   - **Justification:** This query helps identify consistently active and high-value customers — the ones who come back frequently and spend more than average. These customers are ideal candidates for loyalty rewards, exclusive offers, or early product access, helping build long-term customer relationships.
   - **SQL Code:**  
     ```sql
     SELECT
       c.CustomerName,
       COUNT(DISTINCT co.Customer_OrderID) AS OrderCount,
       SUM(cp.PaymentAmount) AS TotalSpent
     FROM
       Customers c
     JOIN CustomerOrder co ON c.CustomerID = co.CustomerID
     JOIN Customer_Payments cp ON cp.OrderID = co.Customer_OrderID
     GROUP BY
       c.CustomerID
     HAVING
       OrderCount >= 2 AND TotalSpent > (SELECT AVG(PaymentAmount) FROM Customer_Payments );
     ```
   - **Query Response:**
      ```
      | CustomerName | OrderCount | TotalSpent |
      |--------------|------------|------------|
      | Emma Johnson | 2          | 5.75       |
      | Liam Smith   | 2          | 4.00       |
      ```


8. **Query 8: (Complex)**  
   - **Description:** Finds orders that contain only promotional items — meaning every product in that order was part of an active promotion at the time of purchase.
   - **Justification:** This query helps management understand how often customers exclusively buy discounted items, which can indicate:
- Customer price sensitivity
- Promotion over-reliance
- Need to balance discounts with full-price sales
This insight is useful for marketing teams when designing promotions and assessing if promos are encouraging bundled buying or just deal-hunting.
   - **SQL Code:**  
     ```sql
     SELECT
       co.Customer_OrderID,
       c.CustomerName,
       COUNT(*) AS PromoItemsOnly
     FROM
       CustomerOrder co
     JOIN Customers c ON co.CustomerID = c.CustomerID
     JOIN Products_has_CustomerOrder phco ON co.Customer_OrderID = phco.CustomerOrder_Customer_OrderID
     JOIN Products p ON phco.Products_ProductID = p.ProductID
     WHERE NOT EXISTS (SELECT 1
       FROM Products p2
       WHERE p2.ProductID = phco.Products_ProductID
     AND NOT EXISTS (SELECT 1 FROM Products_has_Promotions php
       WHERE php.Products_ProductID = p2.ProductID)
     )
     GROUP BY
       co.Customer_OrderID
     HAVING COUNT(*) > 0;
     ```
   - **Query Response:**
      ```
      | Customer_OrderID| CustomerName    | PromoItemsOnly|
      |-----------------|-----------------|---------------|
      | 1               | Emma Johnson    | 1             |
      | 13              | Amelia King     | 1             |
      | 2               | Liam Smith      | 1             |
      | 14              | Logan Wright    | 1             |
      | 7               | Sophia Green    | 1             |
      | 15              | Mila Baker      | 1             |
      | 8               | James Carter    | 1             |
      | 16              | Olivia Brown    | 1             |
      | 18              | Liam Smith      | 1             |
      | 9               | Isabella Hall   | 1             |
      | 19              | Emma Johnson    | 1             |
      | 10              | Benjamin Young  | 1             |
      ```

9. **Query 9: (Complex)**  
   - **Description:** Returns customers whose names contain repeating letters (e.g., "Emma", "Charlotte") and who have made at least one order with a total spend over $2. Also calculates the average amount spent per order.
   - **Justification:** This query combines pattern-based filtering (REGEXP) with customer behavior analytics. It's useful for discovering unique name-based segments of customers who are also meaningfully engaged — making it ideal for creative, personalized promotions or campaigns that stand out with name-based targeting.
   - **SQL Code:**  
     ```sql
     SELECT
       c.CustomerName,
       COUNT(DISTINCT co.Customer_OrderID) AS OrderCount,
       SUM(cp.PaymentAmount) AS TotalSpent,
       ROUND(SUM(cp.PaymentAmount) / COUNT(DISTINCT co.Customer_OrderID), 2) AS AvgPerOrder
     FROM
       Customers c
     JOIN CustomerOrder co ON c.CustomerID = co.CustomerID
     JOIN Customer_Payments cp ON cp.OrderID = co.Customer_OrderID
     WHERE
       c.CustomerName REGEXP '(.)\\1'
     GROUP BY
       c.CustomerID
     HAVING
       OrderCount >= 1 AND TotalSpent > 2;
     ```
   - **Query Response:**
      ```
      | CustomerName    | OrderCount | TotalSpent | AvgPerOrder|
      |-----------------|------------|------------|------------|
      | Emma Johnson    | 2          | 5.75       | 2.88       |
      | Sophia Green    | 1          | 6.00       | 6.00       |
      | Charlotte Scott | 1          | 3.25       | 3.25       |
      ```

     
10. **Query 10: (Complex)**  
     - **Description:** Calculates the total revenue per product across each store location, allowing you to see which products earn the most money at each location.
     - **Justification:** This query is essential for product performance analysis by location. It helps managers:
- Determine which products are driving the most sales at each store
- Identify regional favorites
- Make inventory, pricing, and promotional decisions tailored to each location

     - **SQL Code:**  
       ```sql
       SELECT
         l.StoreName,
         p.ProductName,
         SUM(phco.Quantity * p.ProductPrice) AS TotalRevenue
       FROM
         CustomerOrder co
       JOIN Products_has_CustomerOrder phco ON co.Customer_OrderID = phco.CustomerOrder_Customer_OrderID
       JOIN Products p ON phco.Products_ProductID = p.ProductID
       JOIN Customers c ON co.CustomerID = c.CustomerID
       JOIN Mobile_App_Account maa ON c.CustomerID = maa.CustomerID
       JOIN Location l ON l.LocationID IN (1, 2) -- or tie via employees if preferred
       GROUP BY
         l.StoreName, p.ProductID
       ORDER BY
         TotalRevenue DESC;
       ```
     - **Query Response:**  
       ```
        | StoreName         | ProductName   | TotalRevenue |
        |------------------|----------------|--------------|
        | Dunkin Athens    | Green Tea      | 11           |
        | Dunkin Peachtree | Green Tea      | 11           |
        | Dunkin Athens    | Chai Latte     | 9            |
        | Dunkin Peachtree | Chai Latte     | 9            |
        | Dunkin Athens    | Iced Coffee    | 5            |
        | Dunkin Peachtree | Iced Coffee    | 5            |
        | Dunkin Athens    | Muffin         | 4.5          |
        | Dunkin Peachtree | Muffin         | 4.5          |
        | Dunkin Athens    | Glazed Donut   | 3.75         |
        | Dunkin Peachtree | Glazed Donut   | 3.75         |
        | Dunkin Athens    | Cold Brew      | 3.5          |
        | Dunkin Peachtree | Cold Brew      | 3.5          |
        | Dunkin Athens    | Hot Chocolate  | 3.25         |
        | Dunkin Peachtree | Hot Chocolate  | 3.25         |
        | Dunkin Athens    | Hash Browns    | 3            |
        | Dunkin Peachtree | Hash Browns    | 3            |
       ```
     
# Query Information

- **Database Name:** `al_Group_21484_G7`
- **Additional Information :** z


| Maxtrix Of Query Features       | Query 1 | Query 2 | Query 3 | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 |
|-------------------------------|---------|---------|---------|---------|---------|---------|---------|---------|---------|----------|
| Multiple Table Join            |     ✔    |   ✔     |     ✔    |   ✔      |    ✔     |     ✔    |      ✔   |    ✔     |   ✔      |   ✔       |
| Traditional Subquery           |         |         |     ✔    |         |     ✔    |      ✔   |      ✔   |      ✔   |    ✔     |          |
| Correlated Subquery            |         |         |         |         |         |     ✔    |         |      ✔   |         |          |
| GROUP BY                       |    ✔     |         |    ✔     |     ✔    |         |    ✔     |   ✔       |     ✔    |     ✔    |      ✔    |
| GROUP BY with HAVING           |         |         |    ✔     |         |         |       ✔  |   ✔      |      ✔   |      ✔   |          |
| Multi-Condition WHERE          |         |   ✔      |         |         |     ✔    |         |    ✔     |      ✔   |       ✔  |      ✔    |
| Built-in Functions (e.g., AVG) |       ✔  |         |    ✔     |    ✔     |   ✔      |     ✔    |   ✔      |      ✔   |   ✔      |    ✔      |
| Calculated Field               |         |         |         |         |         |         |        |         |       ✔  |      ✔    |
| REGEXP                         |         |         |         |         |         |         |         |         |    ✔     |          |
| NOT EXISTS                     |         |         |         |         |         |         |         |    ✔     |         |          |


