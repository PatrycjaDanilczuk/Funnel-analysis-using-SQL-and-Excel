# Funnel analysis using SQL and Excel

## Project description 
Create a useful sales funnel chart for top 3 countries (by the overall number of events) and provide analysis. Use SQL and Excel functionality. Use 6 types of events in this analysis.

_Funnel analysis is one of the most often used techniques in product analysis and is a great way to learn more about certain processes, commonly used in e-commerce, sales, conversion & customer engagement analysis. 
It can be used for other processes as well, typically it helps visualize a linear journey or a process, especially in cases when there are clear steps a user needs to take in order to reach some goal: 
register, purchase subscription or buy a product._

_Funnel is primarily about the development (a linear movement towards a desired result) in a specified process. Funnel analysis usually involves analyzing each step in the customer journey and checking clickthrough 
rates and drop off rates at each step. Also in cases where you are comparing several different funnels you may also be interested in total conversion rate: overall performance metric defining how good funnel 
is in converting your customers to reach your specified goal._

## Dataset description
Use raw_events table hosted in BigQuery project. Data in raw_events table captures a lot of events from users based on their timestamps (user_pseudo_id, event_name, event_timestamp, event_date, event_value_in_usd, user_id, user_first_touch_timestamp, category, mobile_model_name, mobile_brand_name, operating_system, language, is_limited_ad_tracking, browser, browser_version, country, medium, name, traffic_source, platform, total_item_quantity, purchase_revenue_in_usd, refund_value_in_usd, shipping_value_in_usd, tax_value_in_usd, transaction_id, page_title, page_location, source, page_referrer, campaign).

## Steps applied

**Step1:** Creating SQL query to retrieve the necessary data applying the following logic:
1.	Creating unique events CTE – 1 unique event per user_pseudo_id at each step of the funnel to eliminate duplicated data, by selecting first event occurrence for each event per user using ROW_NUMBER() function; using min() in this case was not enough to receive first event only.

  	_If we want to see how many users have gone to the checkout the one user who may have gone back and forth to checkout for 8 times can be dangerous when building a funnel chart as it can overrepresent
how many users in total get to the checkout._

3.	Creating subquery for filtering top 3 countries.
   
4.	Filtering out 6 events: page_view, view_item, add_to_cart, add_shipping_info, add_payment_info, purchase.
   
6.	Creating CTE for total number of events per each event, creating rank column to add event order.
   
8.	Creating CTE for 1st, 2nd and 3rd top country.
   
10.	Creating final table showing number of events per 3 top countries  by category.
    
The SQL code can be accessed here

**Step2**: Providing analysis charts and actionable insights in Excel

The analysis can be accessed [here](https://github.com/PatrycjaDanilczuk/Funnel-analysis-using-SQL-and-Excel/blob/main/Funnel_analysis_raw%20events.xlsx)
