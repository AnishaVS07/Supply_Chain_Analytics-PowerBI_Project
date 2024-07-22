## Supply Chain Analytics - PowerBI Project

This Power BI dashboard optimizes supply chain performance and enhances stakeholder engagement by 40%. It features real-time data visualization, performance metrics, and interactive reports to support data-driven decision-making.



![PBI-BP](https://github.com/user-attachments/assets/389f1425-f3ee-47f8-8709-7771407c4467)


![PBI-IM](https://github.com/user-attachments/assets/89cd7b98-998f-453b-8734-520e2278dc94)


![PBI-SM](https://github.com/user-attachments/assets/b3df2f99-c0e7-40a8-a858-278e76c540a8)


![PBI-DM](https://github.com/user-attachments/assets/bb06ceb3-9768-4d93-bfd5-bbaa35f63422)

I)  **PROJECT DESCRIPTION**

The project provides a real-world dataset focusing on supply chain analytics. So have to help solve key shipment and inventory management challenges, analyze supply chain inefficiencies, and create insightful dashboards to inform business stakeholders about potential problems and propose structural business improvements.

II) **METHODOLOGY**

~ Business demand analysis

* Requirements: Create dashboard to analyze the business problem and improve the supply chain’s efficiency

* Method: descriptive, exploratory and diagnostic analysis

* Tools used: Python (Data preprocessing, data cleaning, EDA, inventory segmentation); Power BI (Dashboard)

**$ Sales Manager**: Overview and keep track of customer’s demand and product sales

=> Dashboard of overall business performance including sales, profit, orders, customers, best product,...

**$ Inventory Manager**: Control the inventory flow including order fulfillment, storing and distribution

=> Dashboard of inventory management including warehouse inventory, number of orders from customer, storing cost,...

**$ Shipping Manager**: Overseeing daily shipping and distribution operations to customers

=> Dashboard of shipping management including orders, location, timing, delay shipping,...

Overall target is to create an interactive dashboard to summarize the research of the problem of the supply chain and suggest the solution.

III) **DATA PREPROCESSING**

~ Data overview

The dataset provides three data tables including order_and_shipment, inventory and fulfillment. After examining the data fields, I noticed that the dataset generally represents the following key information

* Customer: General information about customers including identifiers and addresses

* Order: Information about the order including date of order, product and quantity ordered, order value

* Shipment: Shipping information including shipping date, shipping mode

* Product: Specific information about the ordered item including product name, product category, product department

* Warehouse Inventory: Information on inventory management for each product name including monthly inventory, warehouse location, storage costs, order fulfillment

~ Data cleaning

* Drop unnecessary columns (Order Item ID, Order Time)

* Fix the datatype of the columns

* Remove special characters in Customer Country column

* Check for missing value

* Check for duplicate value

- Inconsistency of Product Name between order and inventory table: There are 5 product names that appear in the inventory table but not in the order table. This means that these are items that are in the company's inventory but have not been ordered by the customer. So it's impossible to dêtrmine which product category and product department those product names belong to. After investigating carefully, I decided to keep these product names as they account for a considerable amount of storage cost

- Negative and unusual large shipping time: The Shipping Time = Shipment Date - Order Date has some negative values. Thís is due to the error in recording since the Shipment Date < Order Date. There are also unusually large values. Normally, in the United States, standard shipping within the same country might take anywhere from 2 to 7 business days. International standard shipping can take longer, often ranging from 1 to 4 weeks. I decided to take this information as a reference and drop the shipping time values that < 0 and > 28

*Feature creation*

1) Create Date time feature from day, month, year feature

2) Create Shipment feature to show which order is late or on time

   - Shipping Time = Shipment Date - Order Date

   - Delay Shipment = Late if Shipment Day - Schedule < Shipping Time and vice versa

   - Late Shipment Rate = Total of late order / Total number of order

3) Create Business performance feature

   - Net Sales = Gross sales - Discount * Gross sales

   - Unit Price = Gross sales / Order Quantity

   - Profit margin = Total Profit / Total Net sales

   - Storage cost = Inventory cost per unit * Warehouse inventory
     
IV) **EXPLORATORY DATA ANALYSIS**

In the EDA, I focus on analyzing the characteristics, behaviors, pattern and trends based on these criterions:

Questions:

*Business Performance*

1. What are the total net sales, profit and profit margin by the company?

2. What are the average net sales and profit per month?

3. How do the net sales and profit change over time?

4. How do the number of orders change over time?

5. How do the average order quantity and average unit price change over time?

6. Which product departments account for the majority of net sales and number of orders?

*Customer*

1. How was the distribution of customers by country and market?

2. How many customers does the company have over time?

3. Are there any patterns or trends of buying behavior over time?

*Product*

1. Which product categories and product names are most preferred?

2. Which product categories and product names are most profitable?

*Inventory*

1. Which product departments account for the majority of warehouse inventory and storage cost?

2. How is the inventory cost per unit distributed by the product department?

3. How do the warehouse inventory and storing costs change over time?

4. Which product names and product departments account for the majority of storing cost?

5. What is the average of the average fulfillment order?

6. What is the average order fulfillment of each product department?

*Shipment*

1. Which warehouses are orders shipped from?

2. Which shipment modes are preferred by customers?

3. What is the shipping time for each shipment mode?

4. What is the late shipment rate by product department and market?

5. How does the late shipment rate fluctuate over time?

**_Insights from Business Performance_**

1. Net Sales and Profit have increased year-over-year from 2015 to 2017.
   
2. The net profit margin fluctuated between 60% and 70%.
   
3. The top 5 product departments by number of orders are Fan Shop, Apparel, Golf, Footwear, and Outdoors.
   
4. The majority of orders are shipped via Standard Class (It is by far the most common shipment mode), followed by 
Second Class, First Class and Same Day.

5. The USA has the highest number of orders by country, followed by Mexico, France, Germany, Australia and others.
   
6. The Fan Shop and Apparel product categories have the highest number of orders. Number of orders and order 
quantity both increased from 2015 to 2016.

**_Insights from Inventory Management_**

1. Warehousing inventory and storage costs have increased each year from 2015-2017,Inventory levels and storage 
costs vary across different product departments, with Apparel and Fan Shop showing higher values followed by 
Book Shop, Discs Shop, Fan Shop and Fitness.

2. The top 3 products by inventory cost per unit are Hirzl Men's Hybrid Golf Glove, Nike Women's Legend V-Neck TShirt, and Merrell Women's Grassbow Sport Waterproof Hik.

3. Apparel, Fan Shop, and Golf have the highest storage costs, while Fitness has the lowest.
   
4. The total warehouse inventory is 67,554 units with an average order fulfillment time of 4 days.Total inventory cost 
per unit is 4.95K, and storage cost is 81.75K.

**_Insights from Shipment Management_**

1. Delays are visible across various departments, with the Fan Shop, Fitness, and Discs Shop showing the highest ontime delivery rates. While Technology, Apparel, Footwear, Golf and Outdoors have more late than on-time

2. Most countries have more on-time than late shipments, but some like USA, Mexico, France, Germany, and Brazil 
show significant late shipments, indicating potential issues in the logistics chain in these regions.
  
3. Certain products like TaylorMade Women's RBZ SL Rescue have very high late shipment rates near 100%. Followed 
by products like Men's gala suite, and Stiga Master Series have higher late shipment rates.

4. The late shipment rate shows an increasing trend over the years, peaking around 0.53 in 2015 Quarter 1 January and 
around 0.51 in 2017 Quarter 3 September and gradually decreased to 0.40 in 2017 Quarter 4 December.
  
5. The report covers orders from 01/01/2015 to shipments on 03/01/2015 and beyond. First Class is the first shipment 
mode listed. Puerto Rico is the first warehouse country listed. Total shipment schedule days is 74,869.

A supply chain will consist of three main components: suppliers - company - customers.

The supply chain starts with the suppliers who provide the products that the e-commerce company will sell. These could include manufacturers, distributors, or wholesalers. Supplier relationships, quality control, and timely deliveries are crucial in this supplier network. Here, we will be interested in average order fulfillment

Once the products are received from suppliers, they are stored in warehouses. Inventory management systems track stock levels, reorder points, and storage locations. Efficient warehousing and inventory management helps prevent stock outs while minimizing excess inventory. Here, we will learn more about storage cost, warehouse inventory and warehouse country

Once customers place orders, the e-commerce platform's order processing team verifies details, product availability, and shipping preferences before transmitting the information to the warehouse. There, staff pick and securely pack items from storage locations, ensuring accuracy and speed to meet customer expectations. The packed orders are then transferred to shipping partners, who may include couriers or carriers, with various options chosen to align with customer delivery expectations. So, in this section, we will need to focus on delayed shipment, delivery system as well as return and canceled order. However, the data set will only give us information about delayed shipment.

Overall, for the whole supply chain to work efficiently, demand forecasting plays a significant role in supply chain optimization. Historical sales data, customer trends, and market insights can help forecast demand accurately, reducing stockouts and excess inventory. We will also consider the demand and supply of the products.

