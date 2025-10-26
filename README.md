# MIST4610-Group-Project
This project is the creation of a complex data model for our class's data management group project. 

**Group 2**

Team Members:

[Daniel Ferrer](https://github.com/djferrer25-maker)

Ian Martin

[Noila Rahimjon](https://github.com/noilar)

[Oraa Raysoni](https://github.com/oraaraysoni-beep)

Sisira Gudi

# Problem Description:

The task at hand is to model and build a relational database for the general workings of an e-commerce company, "PuzzleVerse." The central goal is to track the company's product catalog, customer sales, and artist collaborations. The model must support all core business functions, from managing customer orders and payments to tracking product designs and custom requests.
We are interested in accurately modeling these relationships, generating sample data to populate the entities and their attributes, and formulating 10 functioning queries on this data to provide valuable business insights about PuzzleVerse's operations.

# Data Model:

Our data model, "PuzzleVerse," is structured to support all facets of this custom puzzle business, using essential entities and their relationships to correctly support different areas of the business such as sales, product management, and customer relations.
First off, the Customers entity represents our customer base. Within this entity, we have the primary key (idCustomers), as well as the customer's name, email, and phone number. A customer can have multiple shipping addresses, so the Customers table is linked via a one-to-many relationship to the Addresses table, which stores the street, city, state, and zip for each address.
Customers place Orders, which form a one-to-many relationship where one customer can have multiple orders. The Orders entity contains its own primary key (idOrders), a foreign key from Customers, and attributes such as the OrderDate, TotalCost, and Status. Each order is also linked to one or more Payments in a one-to-many relationship.
Since each order can consist of multiple products, we introduce the Order_Items table. This associative entity links Orders and Products in a many-to-many relationship. Within the Order_Items table is its own primary key (idOrder_Items), as well as two foreign keys pulled from the Orders and Products tables. It also tracks the quantity of each product and the UnitPriceAtSale to capture the price at the time of purchase.
The Products entity is central to our catalog. Each product has a primary key (idProducts), a name, a piece count, and a standard unit price. Each product's artwork is designed by an Artist, forming a one-to-many relationship. The Artists table stores the artist's name, email, and pay rate. To allow for a rich product page, each product can also have multiple images, linking it to the Product_Images table. Furthermore, Products and Categories have a many-to-many relationship, joined by the Products_Categories table, allowing a puzzle to be listed under "Animals" and "Landscapes" simultaneously.
Finally, the Custom_Order_Requests entity manages our custom puzzle service. This table links a Customer and an Employee (who manages the request) to a potential Product. This entity tracks the approval status, image link, and description for each custom design.

# Data Model: 
<img width="974" height="945" alt="project" src="https://github.com/user-attachments/assets/a0982940-b574-48a3-9fda-83483fc0e6ca" />

# Data Dictionary: 

Table: **Customers:**

<img width="896" height="193" alt="image" src="https://github.com/user-attachments/assets/3139354d-826e-4544-9183-17c6aa225dee" />

Table: **Artists:**

<img width="686" height="145" alt="image" src="https://github.com/user-attachments/assets/3598c1a7-cf52-4b9e-b3c7-25c227604aa1" />

Table: **Orders:**

<img width="831" height="169" alt="image" src="https://github.com/user-attachments/assets/fc69705b-3958-4eef-a0ab-de29866e7a01" />

Table: **Adresses:**

<img width="754" height="193" alt="image" src="https://github.com/user-attachments/assets/57bee603-f9dc-4764-a076-8a09d8d5d744" />

Table: **Products:**

<img width="891" height="217" alt="image" src="https://github.com/user-attachments/assets/99f50fd3-04b1-4ad8-91d0-f15e72fd1900" />

Table: **Order Items:**

<img width="756" height="145" alt="image" src="https://github.com/user-attachments/assets/740389dc-d363-464c-9739-8a911d3dd265" />

Table: **Payments:**

<img width="839" height="169" alt="image" src="https://github.com/user-attachments/assets/26e81efe-4533-49bd-b6ba-d2436f7b6a35" />

Table: **Product Images:**

<img width="794" height="145" alt="image" src="https://github.com/user-attachments/assets/bb05b095-9e16-4456-a235-5187c9132034" />

Table: **Product Categories:**

<img width="656" height="73" alt="image" src="https://github.com/user-attachments/assets/95e0f2ff-0926-4cbb-b5a5-ba277d382064" />

Table: **Categories:**
		
<img width="678" height="97" alt="image" src="https://github.com/user-attachments/assets/32cb7537-bf74-49bd-8c02-0c9abfb394ee" />

Table: **Customer_Order_Request**: 

<img width="986" height="289" alt="image" src="https://github.com/user-attachments/assets/25c946b9-cc8e-42fc-aefc-d4f5bbd5a616" />

Table: **Employees**: 

<img width="666" height="169" alt="image" src="https://github.com/user-attachments/assets/fb949e56-09c2-4c0b-b623-90aae8b78cfe" />

# Queries: 

<img width="1900" height="265" alt="image" src="https://github.com/user-attachments/assets/d3577b6b-eb16-4648-a33e-81bae775c760" />

Query 1 (Simple):
Retrieve all of the order information for customer #1, including the idOrder, OrderDate, TotalCosts, Status, and Notes.

<img width="517" height="382" alt="Screenshot 2025-10-26 at 4 57 38 PM" src="https://github.com/user-attachments/assets/d65a834c-7556-4c92-ab0e-d408957bd5e1" />


Query #1 retrieves all orders placed by a specific customer. It allows managers to track a customer's complete purchase history and understand their buying habits. By analyzing these orders, the customer service team can handle inquiries more effectively, and the marketing team can identify loyal clients. By leveraging this query, managers can improve customer retention and enhance the overall shopping experience. Tracking individual purchase patterns also helps in tailoring marketing efforts, such as sending targeted discounts or personalized follow-ups to repeat buyers.


Query 2 (Simple):
Which custom design orders are currently awaiting review?

<img width="598" height="467" alt="Screenshot 2025-10-26 at 4 58 16 PM" src="https://github.com/user-attachments/assets/e7af1252-66cd-4439-8eec-13997808fdc4" />


Query #2 retrieves all records from the Custom_Order_Requests table that have a 'Pending' status. It provides an immediate, actionable list of all new requests that have not yet been processed. This query is essential for the design consultant (Employee) as it functions as their daily work queue. By identifying all pending orders, managers can allocate resources efficiently, ensure timely customer communication, and prevent any orders from being overlooked, which is critical for maintaining customer satisfaction.


Query 3 (Complex): 
Which customers registered with a Gmail account?

<img width="478" height="471" alt="Screenshot 2025-10-26 at 4 58 57 PM" src="https://github.com/user-attachments/assets/84824b4a-8d8f-4562-b387-4b000da9489f" />


Query #3 retrieves the names and contact information of customers whose email addresses match the '@gmail.com' pattern. It allows managers to segment their customer base by email provider. By utilizing this query, the marketing team can create exclusive offers for a specific customer group or analyze the composition of their audience. This segmentation strategy helps improve marketing effectiveness and build stronger customer relationships.


Query 4 (Simple): 
Which orders had a total cost greater than $100?

<img width="415" height="470" alt="Screenshot 2025-10-26 at 4 59 26 PM" src="https://github.com/user-attachments/assets/4cf5460f-50f1-4f1b-936a-354943642971" />


Query #4 retrieves all orders where the TotalCost exceeds $100. This query helps managers instantly identify the most significant transactions in the system. By identifying these high-value orders, managers can prioritize them for fulfillment, flag them for special review, or analyze what common products are driving up the total cost. This aids in developing effective pricing and promotional strategies.


Query 5 (Simple):
What is our complete product catalog, sorted from most to least expensive?

<img width="411" height="556" alt="Screenshot 2025-10-26 at 5 00 13 PM" src="https://github.com/user-attachments/assets/598abc89-2265-42eb-91dd-6e23f608a1b9" />


Query #5 retrieves the entire product list, ordered by UnitPrice in descending order. It provides a clear overview of the product catalog's price range. This query allows managers to analyze the pricing strategy at a glance, identify premium items, and ensure the catalog is well-balanced between high- and low-end products.


Query 6 (Complex):
What is the total lifetime revenue generated by each customer?

<img width="753" height="576" alt="Screenshot 2025-10-26 at 5 00 54 PM" src="https://github.com/user-attachments/assets/b7ab8de8-103f-458e-bb88-671bf42c7fd8" />


Query #6 joins the Customers and Orders tables and uses a GROUP BY to calculate the sum of TotalCost for each customer. This query identifies the most valuable clients (VIPs) based on their lifetime spending. By leveraging this data, managers can make data-driven decisions on customer relationship management. It allows them to focus retention efforts on top clients and build tiered loyalty programs.


Query 7 (Complex):
What are our top 3 best-selling products by total units sold?

<img width="646" height="450" alt="Screenshot 2025-10-26 at 5 01 24 PM" src="https://github.com/user-attachments/assets/171b373c-3bff-4570-9fc0-ece5714b0334" />


Query #7 calculates the total quantity sold for each product by joining Order_Items and Products. It then retrieves only the top 3 best-selling items. This is an essential query for inventory and marketing managers. It provides clear insight into product popularity, which informs decisions on what to re-stock, what to feature on the homepage, and where to focus advertising budgets.


Query 8 (Complex): 
Which products in the catalog have never been included in an order?

<img width="627" height="452" alt="Screenshot 2025-10-26 at 5 03 02 PM" src="https://github.com/user-attachments/assets/92affe36-c2f1-4f12-8e61-08babecefd6e" />


Query #8 retrieves all products from the Products table that do not have a corresponding entry in the Order_Items table. It helps managers recognize low-demand or overlooked items. By using this query, managers can make data-driven decisions to either discontinue these unpopular products to save on warehousing, bundle them with best-sellers, or run targeted clearance promotions to recover costs.


Query 9 (Complex): 
What is the average total cost per order each month?

<img width="784" height="388" alt="Screenshot 2025-10-26 at 5 03 51 PM" src="https://github.com/user-attachments/assets/93fabe5c-db5a-4c4b-9dd9-5dc0ecbe565e" />


Query #9 calculates the average TotalCost of all orders, grouped by the month and year they were placed. This provides a clear view of spending trends over time. This data is critical for financial forecasting. It allows managers to track if customers are spending more or less on average as seasons change and to measure the effectiveness of sitewide promotions on increasing the average order value.


Query 10 (Complex):
What percentage of total payments came from each payment method?

<img width="1198" height="423" alt="Screenshot 2025-10-26 at 5 04 23 PM" src="https://github.com/user-attachments/assets/8d3552a1-4042-472c-bd00-1e075ce58103" />


Query #10 calculates the total revenue collected from each payment method and uses a subquery to display that amount as a percentage of all revenue. By analyzing this data, managers can understand customer payment preferences. This informs decisions about which payment integrations (e.g., PayPal, Apple Pay) are most important to maintain or add, and it helps in analyzing transaction fee costs.


# Datebase Information
**Name of database:**
ns_osr89909

Name of Data Model:
Project














