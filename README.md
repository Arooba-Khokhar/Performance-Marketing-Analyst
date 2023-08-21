# Performance-Marketing-Analyst

**E-commerce websites**

With online sales gaining popularity, tech companies are exploring ways to improve their
sales by analyzing customer behavior and deriving insights about product trends.
Furthermore, e-commerce websites make it easier for customers to find the products that
they require without much scavenging. Therefore, as a part of this assignment, you, as a
Performance Marketing Analyst, are required to extract data and gather insights for an
e-commerce company

Introduction

● Calculate the revenue of each month

● Find the product under each category

● Find the event type

● Find the max brand of each month

● Find the top 10 user


**Total revenue of October**

Find the total revenue generated due to purchases made in October.
SELECT ROUND(SUM(price),2) as TotalRev_October

FROM table

WHERE event_type = 'purchase' AND

date_format(event_time, 'MM') = 10;

We see that the Total Revenue in the month of ‘October 2019’ is xxxx

![image](https://github.com/Arooba-Khokhar/Performance-Marketing-Analyst/assets/14163981/4a8af284-9fe2-4f60-9421-99a837cb3e72)

![image](https://github.com/Arooba-Khokhar/Performance-Marketing-Analyst/assets/14163981/ed17b5fc-bc15-40da-a39b-60e6ddc7a71c)


**Result**

● We observe that the sum of purchases (Revenue) in the month of ‘November
2019’ is higher than that of ‘October 2019’.

● We can infer that the month of November has performed better than October.


Find distinct categories of products. Categories with null category code can be ignored.

SELECT DISTINCT SPLIT(category_code,'\\.')[0] AS Category_List

FROM table;

● We observe 6 different categories present namely; furniture, appliances, accessories, apparel, sport,
stationery.

● The category_code column contained values, which were delimited by ‘.’. We use the SPLIT command to split
and located the first index alone, which contained the main Category.

Find the total number of products available under each category.

SELECT SPLIT(category_code,'\\.')[0] AS Category, COUNT(product_id) AS Total_Product_count

FROM table

GROUP BY SPLIT(category_code,'\\.')[0]

ORDER BY Total_Product_count DESC;


![image](https://github.com/Arooba-Khokhar/Performance-Marketing-Analyst/assets/14163981/fdbfd447-e3d5-491a-9f08-40ebaa46ab6a)


**Result**

● We observe that, ‘appliances’ category has the highest number of cosmetic
products available under it.

● We can see ‘sports’ category has the least cosmetic products under it. This make
sense as sports category would not contain many cosmetic products.


**Max value**

Which brand had the maximum sales in October and November combined?

SELECT brand, ROUND(SUM(price),2) as Total_sales

FROM table

WHERE event_type = 'purchase'

GROUP BY brand

ORDER BY Total_sales desc

LIMIT 5;


![image](https://github.com/Arooba-Khokhar/Performance-Marketing-Analyst/assets/14163981/a494265a-90a6-4633-ac21-63fcfd0502fd)


![image](https://github.com/Arooba-Khokhar/Performance-Marketing-Analyst/assets/14163981/df12b844-762a-47e2-9ea0-1e58df8646ef)



![image](https://github.com/Arooba-Khokhar/Performance-Marketing-Analyst/assets/14163981/4e44854b-4f14-463c-8763-4a31b19b1d9c)


**Top 10 users**

Your company wants to reward the top 10 users of its website with a Golden Customer plan.

SELECT user_id, ROUND(SUM(price),2) as Total_money_spent

FROM table

WHERE event_type = 'purchase'

GROUP BY user_id

ORDER BY Total_money_spent DESC

LIMIT 10;




