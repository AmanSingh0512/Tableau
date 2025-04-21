# Telecom Customer Churn Analysis (Databel)

This project analyzes customer churn using a fictional dataset from a Telecom provider called Databel. The dataset includes 29 columns with one row per customer.

According to Investopedia, the churn rate (also known as the rate of attrition) is the percentage of customers who stop doing business with a company. Since it’s generally easier to retain existing customers than to acquire new ones, reducing churn is a key focus for many businesses. Churn can be calculated in different ways depending on the industry, but a basic formula is the number of customers lost divided by the total number of customers.

DATA CHECK

The first step of the analysis was a data validation. We created two calculated fields:

Number of Customers: COUNT of ‘Customer ID’

Number of Unique Customers: COUNTD of ‘Customer ID’

This was to ensure there were no duplicate entries. Both counts returned 6687, confirming that all customer IDs are unique.

CALCULATING CHURN

To calculate churn, we used the ‘Churn Label’ column, which has values “Yes” or “No” to indicate whether a customer churned. We converted this into a binary column named ‘Churned’:

sql
Copy
Edit
IF [Churn Label] == “Yes” THEN 1 ELSE 0 END
We then calculated:

Number of Churned Customers: SUM of the ‘Churned’ column

Churn Rate: Number of Churned Customers / Number of Customers

INVESTIGATING CHURN REASONS

We explored the reasons behind churn by creating a column chart sorted in descending order. The top 3 churn reasons were:

Competitor made better offer

Competitor had better device

Attitude of service provider

DIGGING DEEPER INTO CHURN CATEGORIES

The churn reasons are grouped under a column called ‘Churn Category’. For example, reasons like “Extra data charges” and “Price too high” fall under the “Price” category. After visualizing, it was revealed that 44.82% of churn was due to competitor-related reasons.

USING MAPS FOR FURTHER EXPLORATION

Databel suspected competitors' aggressive promotions in specific states may have affected churn. A map was created in Tableau to visualize churn rate by state. California (CA) had the highest churn rate: 63.24% (43 out of 68 customers).

ANALYZING DEMOGRAPHICS

Churn among senior citizens was found to be approximately 10% higher than the average churn rate of 38.22%. We then created age bins and a combo chart to visualize customer distribution and churn rate by age bracket. It showed that customers aged 70 and above had the highest churn rate, although they represent a smaller portion of the customer base.

INSPECTING GROUPS

Databel offers group contracts with discounted rates for households. We analyzed whether being in a group leads to lower phone bills and reduced churn. The analysis showed that:

Monthly Charges are lower for customers in groups

Groups of 6 had the lowest churn rate However, over 75% of customers (5166) were not part of any group.

PARAMETERS

To make the dashboards interactive for stakeholders, we created a dynamic parameter called ‘Pick Metric’ with options like:

Avg Monthly Charge

Number of Customers

Number of Churned Customers

Avg Customer Service Calls

Using this, it became evident that customers in groups had significantly lower churn rates (<10%).

CHURN RATE BY PLAN

Databel suspected that customers without unlimited data plans were more likely to churn. A text table comparing churn rates showed that customers with unlimited plans actually churned more. Further analysis showed that customers on unlimited plans but using less than 5 GB per month were more likely to churn.

CHURN RATE BY INTERNATIONAL CALLS

Databel wanted to understand the impact of international call usage and international plans on churn. The analysis found that:

Customers who had an international plan but didn’t make international calls had the highest churn rate

This group also had the highest average monthly charge

CHURN RATE BY CONTRACT TYPE

We added contract type to the analysis and found that:

Month-to-month customers are much more likely to churn

Most of them pay via Direct Debit (1141 out of 1796)

This group also had a high average of 1.47 customer service calls per person

OVERVIEW DASHBOARD

We built four dashboards to present our findings. The first is an overview dashboard that shows key metrics such as number of customers, churn rate, and churn reasons.

AGE BRACKETS & GROUP DASHBOARD

The second dashboard focuses on age and group membership. Using filters and parameters, the dashboard showed that:

Customers not in a group with an account length of 12 months or less have a 53% churn rate Encouraging these customers to switch to longer-term contracts could reduce churn.

PAYMENT METHOD & CONTRACT DASHBOARD

The third dashboard combines contract and payment methods with customer service call data. It uses a scatterplot and KPI cards. We found that:

Customers on month-to-month contracts who pay via Direct Debit have a high number of service calls (1.47) This suggests a potential issue with this payment setup that needs attention.

INTERNATIONAL AND DATA PLAN DASHBOARD

The fourth dashboard analyzes international and data plans. The analysis showed:

Customers not on unlimited plans but using less than 5 GB per month are paying $4.34 extra in data charges This added cost may be contributing to higher churn.

SUMMARY

Finally, we combined all four dashboards into a Tableau Story to summarize our analysis and provide actionable insights for reducing churn at Databel.








