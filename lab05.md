# Lab 5: Measure Customer Adoption and Engagement

# Lab Overview
## Introduction
In this lab, you will return to Dynamics 365 Customer Insights - Data (CI-D) to measure how customers are adopting and engaging with ColorCloud products after their initial onboarding journey. So far in the workshop, you have built journeys that support Maya Novak from newsletter subscription, through purchase and onboarding, to first-use feedback. Now you will use CI-D measures to quantify customer behavior and identify the most valuable early adopters.

You will create four measures: **OrderCount**, **RegistrationCount**, **TotalUsageHours**, and **TotalRevenue**. Together, these measures will help you understand how often customers purchase, whether they register their products, how actively they use them, and how much revenue they generate. You will then use these measures in a CI-D segment called **HighValueEarlyAdopters** to identify customers who show strong early engagement and value.

## Objectives
By the end of this lab, you will be able to:
- Create CI-D measures based on transactional, registration, telemetry, and revenue data
- Review measure results at the unified customer profile level
- Build a CI-D segment using multiple measures
- Identify high-value early adopters for future activation


# Exercise 1: Create the OrderCount measure
In this exercise, you will create a measure that counts how many orders each customer has placed.

**Step 1. Open Customer Insights - Data**
- Open the CI-D environment you verified in Lab 1 and used in Labs 3 and 4
- In the left navigation, go to Insights > **Measures**

**Step 2. Create a new measure**
- At the top command bar, click on **+ New**
- Choose **Build your own**

**Step 3. Enter measure details**
- Name the measure **OrderCount**
- Enter a description, for example: Counts the number of orders placed by each customer
- Confirm that the measure is created at the customer level

**Step 4. Select the source table**
- Choose the table that contains order or transaction records, for example **Transactions : eCommerce**
- Select the attribute that uniquely identifies an order record

**Step 5. Configure the calculation**
- Choose the aggregation type **Count**
- Make sure the measure counts the number of transaction records related to each customer
- If needed, review and confirm the relationship path that connects transactions to the unified customer profile

**Step 6. Save and run the measure**
- Click **Save**
- Then click **Run**
- Wait until the measure starts processing

**Step 7. Verify the measure**
- Back in the Measures overview, verify that **OrderCount** has Status Queued, Refreshing, or Successful
- If successful, open the measure and review the output preview

**Expected outcome**

You have created a CI-D measure named **OrderCount** that counts the number of orders placed by each customer.


# Exercise 2: Create the RegistrationCount measure
In this exercise, you will create a measure that counts how many product registrations each customer has completed.

**Step 1. Create a new measure**
- In CI-D, stay in Insights > **Measures**
- At the top command bar, click on **+ New**
- Choose **Build your own**

**Step 2. Enter measure details**
- Name the measure **RegistrationCount**
- Enter a description, for example: Counts the number of products registered by each customer

**Step 3. Select the source table**
- Choose the table that contains product registration records, for example **ProductRegistrations**
- Select the attribute that uniquely identifies a registration record

**Step 4. Configure the calculation**
- Choose the aggregation type **Count**
- Make sure the measure counts the number of registration records related to each customer
- If needed, review and confirm the relationship path between registrations and the unified customer profile

**Step 5. Save and run the measure**
- Click **Save**
- Then click **Run**
- Wait until the measure starts processing

**Step 6. Verify the measure**
- Back in the Measures overview, verify that **RegistrationCount** has Status Queued, Refreshing, or Successful
- If successful, open the measure and review the output preview

**Expected outcome**

You have created a CI-D measure named **RegistrationCount** that counts the number of products registered by each customer.


# Exercise 3: Create the TotalUsageHours measure
In this exercise, you will create a measure that sums the number of hours customers have used their ColorCloud products.

**Step 1. Create a new measure**
- In CI-D, stay in Insights > **Measures**
- At the top command bar, click on **+ New**
- Choose **Build your own**

**Step 2. Enter measure details**
- Name the measure **TotalUsageHours**
- Enter a description, for example: Sums the total usage hours recorded for each customer

**Step 3. Select the source table**
- Choose the table that contains telemetry or usage summary records, for example **TelemetrySummary**
- Select the attribute that stores product usage hours

**Step 4. Configure the calculation**
- Choose the aggregation type **Sum**
- Make sure the measure sums usage hours across all relevant records for each customer
- If needed, review and confirm the relationship path between telemetry records and the unified customer profile

**Step 5. Save and run the measure**
- Click **Save**
- Then click **Run**
- Wait until the measure starts processing

**Step 6. Verify the measure**
- Back in the Measures overview, verify that **TotalUsageHours** has Status Queued, Refreshing, or Successful
- If successful, open the measure and review the output preview

**Expected outcome**

You have created a CI-D measure named **TotalUsageHours** that sums the total product usage hours for each customer.


# Exercise 4: Create the TotalRevenue measure
In this exercise, you will create a measure that sums the total revenue generated by each customer.

**Step 1. Create a new measure**
- In CI-D, stay in Insights > **Measures**
- At the top command bar, click on **+ New**
- Choose **Build your own**

**Step 2. Enter measure details**
- Name the measure **TotalRevenue**
- Enter a description, for example: Sums the total revenue generated by each customer

**Step 3. Select the source table**
- Choose the table that contains transaction or sales records, for example **Transactions : eCommerce**
- Select the attribute that stores the monetary amount for each order

**Step 4. Configure the calculation**
- Choose the aggregation type **Sum**
- Make sure the measure sums revenue across all relevant order records for each customer
- If needed, review and confirm the relationship path between transactions and the unified customer profile

**Step 5. Save and run the measure**
- Click **Save**
- Then click **Run**
- Wait until the measure starts processing

**Step 6. Verify the measure**
- Back in the Measures overview, verify that **TotalRevenue** has Status Queued, Refreshing, or Successful
- If successful, open the measure and review the output preview

**Expected outcome**

You have created a CI-D measure named **TotalRevenue** that sums the total revenue generated by each customer.


# Exercise 5: Build the HighValueEarlyAdopters segment
In this exercise, you will combine the four measures into a CI-D segment that identifies customers who are showing strong early adoption and engagement.

**Step 1. Go to Segments**
- In CI-D, go to Insights > **Segments**

**Step 2. Create a new segment**
- At the top command bar, click on **+ New** > Build your own
- Click on Edit details next to Untitled segment
- Name the segment **HighValueEarlyAdopters**
- Enter a description, for example: Customers with strong early adoption and engagement based on orders, registrations, usage, and revenue
- Add tags that help identify the purpose of the segment, for example:
  - Adoption
  - Engagement
  - High Value
- Click on Done in the right bottom corner

**Step 3. Add measure-based conditions**
- In the right navigation, switch to the **Measures** tab
- Add **OrderCount** to the segment logic canvas and set the condition to identify customers with at least one order
- Add **RegistrationCount** to the same rule and set the condition to identify customers with at least one product registration
- Add **TotalUsageHours** to the same rule and set the condition to identify customers with meaningful product usage, for example greater than or equal to 100
- Add **TotalRevenue** to the same rule and set the condition to identify customers with strong revenue contribution, for example greater than or equal to 500

**Step 4. Review the segment logic**
- Confirm that the logic is built with **AND** conditions so that customers must satisfy all four measure thresholds
- Review the segment definition to make sure it reflects the intended high-value early adopter audience

**Step 5. Save and run the segment**
- Click **Save**
- Then click **Run**
- Wait until the segment starts processing

**Step 6. Verify the segment**
- Back in the Segments overview, verify that **HighValueEarlyAdopters** has Status Queued, Refreshing, or Successful
- If successful, confirm that you can see Members for the segment
- Optionally open the segment and review the Segment members preview at the bottom

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/data/measures) to learn more about Measures in CI-D

**Expected outcome**

You have created a CI-D segment named **HighValueEarlyAdopters** that uses **OrderCount**, **RegistrationCount**, **TotalUsageHours**, and **TotalRevenue** to identify customers who show strong early product adoption and engagement.


# Lab Summary
In this lab, you used CI-D to move from journey orchestration into customer measurement and analysis. You created four measures to quantify orders, product registrations, usage, and revenue, and then combined them into a segment that identifies high-value early adopters.

Consider where this lab fits in Maya Novak’s experience:
- Maya has already subscribed, purchased, onboarded, activated her product, and shared feedback
- CI-D can now measure whether she behaves like a strong early adopter
- The **OrderCount**, **RegistrationCount**, **TotalUsageHours**, and **TotalRevenue** measures help quantify that behavior
- The **HighValueEarlyAdopters** segment can now be used for further analysis, activation, or future journeys

You are now ready to continue with the next step of the workshop in **Lab 6: AI-Powered Customer Insights**.
