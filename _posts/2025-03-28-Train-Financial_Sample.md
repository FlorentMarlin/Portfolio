---
layout: post
title:  "Dataset 'Financial Sample'"
categories: jekyll update
image: /images/train_finance_dashboard_1.png
---

Analysis of <a href='https://learn.microsoft.com/en-us/power-bi/create-reports/sample-financial-download'>Microsoft's 'Financial Sample' dataset</a>.

This study was performed as part of my self-training for Data Analysis and Power BI.

The present post aims at presenting my approach to analyze the dataset.

The present post is broken down into the two following sections:
<ul>
  <li>Exploratory Data Analysis</li>
  <li>Storytelling report</li>
</ul>


<h3>Exploratory Data Analysis</h3>


<h4>Preliminary Analysis</h4>

The dataset has 16 columns and 700 rows.

The dataset appears to show sales data for products, some of which might be bicycles (inferred by the French terms 'Velo' and 'VTT', and by the Spanish terms for the intended road use in column: 'Product').

Records cover a period extending from september 1st 2013 to december 1st 2014. Hence data is available only for a portion of the year 2013.

The records contain information for customer, costs, sales prices, discounts, number of sold units and dates, for a total of 16 features.

The dataset contains no blank data whatsoever.

Data types are inferred by the Excel-file (types: text, numeric, date).

The label of the column 'Sales' has a leading whitespece in the original dataset, which I deleted.

In particular, datetimes are, and components for year, month-name and month-number are pre-extracted.

The column: 'Segment' has 5 distinct values, that I interpret as a category of a given customer, or of a collection of customers...
<ul>
  <li>Government: the customer is a public administration</li>
  <li>Channel Partners: partner-companies of the owner of the dataset</li>
  <li>Enterprise: Large company</li>
  <li>Midmarket: Medium-sized company</li>
  <li>Small Business: Small-sized company</li>
</ul>

The column: 'Country' has 5 values for 5 country names.

The column: 'Product' has 6 values for 6 product names.

The column: 'Discount Band' has 4 values for 4 discount levels.

The order of magnitude of the number of records in the dataset (700) is in line with the number of cross-combinations of values for Segment, Country, Product and Discount Band (5*5*6*4=600), with variants for different dates.

Given the resolution of dates (one row -> the first day of a month) and the amount of sold products on a given row (typically hundreds to thousands), each record is probably an aggregation of sales for one month, and for one combination of sales-parameters.

<h5>Data dictionary</h5>

This is my understanding of the different features in the original dataset:

<ul>
  <li>Segment: Category of business that products were sold to</li>
  <li>Country: Country-category of customer</li>
  <li>Product: Commercial name of sold product</li>
  <li>Discount Band: Category of discount level</li>
  <li>Units Sold: Number of products sold as part of one record</li>
  <li>Manufacturing Price: Manufacturing price of one unitary product</li>
  <li>Sale Price: Selling price of one unitary product</li>
  <li>Gross Sales: Gross revenue (i.e. before discounts) for one aggregation of orders</li>
  <li>Discounts: Cost of discounts for one aggregation of orders</li>
  <li>Gross Sales: Net revenue (i.e. after discounts) for one aggregation of orders</li>
  <li>COGS: Cost of goods sold for one aggregation of orders</li>
  <li>Profit: Profit for one aggregation of orders</li>
  <li>Date: Date for the aggregated record</li>
  <li>Year: Year for the aggregated record</li>
  <li>Month Name: Month name for the aggregated record</li>
  <li>Month Number: Month integer number for the aggregated record</li>
</ul>


<h5>Relations between features</h5>

The following relations between numerical features were found again:
<ul>
  <li>Gross Sales = Units Sold * Sale Price</li>
  <li>Sales = Gross Sales - Discounts</li>
  <li>Profit = Sales - COGS</li>
</ul>


<h5>Analysis of numerical features</h5>

The unit of prices and costs is not determined.

The orders of magnitude of Manufacturing Price and Sale Price vs. e.g. Gross Sales suggest that they are prices per unit sold.

Manufacturing price ranges from 3 to 250. The value '10' has an ocurrence that is twice as high as the othe occurrences of other values, that share similar occurrences.

Calculating the standard deviation of the Manufacturing Price grouped by Product confirms that the Manufacturing Price depends only on the Product (standard deviation equal to zero).

Sale Price ranges from 7 to 350, with identical ocurrences.


Units Sold range from 200 to 4492.5. 36 records have non-integer half-values. It is unexplained why a number of units would have non-integer values, and the question would be forwarded to the owner of the dataset.


The columns 'Year', 'Month Name' and 'Month Number' are verified as being extracted OK from the feature: 'Date'.



<h5>Possible analysis</h5>

The present dataset lends itself to the following types of studies
<ul>
  <li>Analysis of sales performance over categories</li>
  <li>Analysis of sales performance over time</li>
</ul>


<h4>Analysis of revenue</h4>

For the whole activity covered by the dataset (2013-2014):
<ul>
  <li>Revenue: 128 millions</li>
  <li>Profit: 17 millions</li>
  <li>Units output: 1.1 million</li>
  <li>Margin: 13%</li>
</ul>

For the complete year 2014:
<ul>
  <li>Revenue: 92 millions</li>
  <li>Profit: 13 millions</li>
  <li>Units output: 861 000</li>
  <li>Margin: 13%</li>
</ul>


For reference, Giant, the world's largest bicycle designer and manufacturer, has following figures:
<ul>
  <li>Revenue: 1.9 billion (2017)</li>
  <li>Units output: 6.6 million (2017)</li>
  <li>Margin: approx 6.7% (2021)</li>
</ul>

Therefore the dataset might correspond to a larger manufacturer, but the magnitude of the margin is exceptional for an industry.


<h4>Analysis of sales over categories</h4>


<h5>Analysis of sales over customer segments</h5>

Customer segment considered as a category, all other features (Country, Product, Discount Band) summed.

<span class="badge bg-success">Units sold by Segment - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_segment_units.png)
<div class="mt20"></div>

Government represents 42% of all products sold in numbers.

Other segments constitute about 15% of the total each.

<span class="badge bg-success">Sales by Segment - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_segment_sales.png)
<div class="mt20"></div>

Government, Small Business and Enterprise are the dominant contributors to sales. Midmarket and Channel Partners are very small in comparison.

<span class="badge bg-success">Profit by Segment - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_segment_profit.png)
<div class="mt20"></div>

Government is the dominant contributor to profit. Small Business comes second and is three times less. Midmarket and Channel Partners are very small in comparison.

Enterprise makes negative profit.


The negative profit related to segment 'Enterprise' might be a concern, as it offsets the total profit by approx. 4%.

It is also remarkable that the profit associated with segment 'Small Business' (25% of total) is not in line with the proportion of Sales (36%).


<h5>Analysis of sales over countries</h5>


<span class="badge bg-primary">Units sold by Country - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_country_units.png)
<div class="mt20"></div>

Profits have the same magnitude for all five countries. Canada, France and USA form a group with more units sold. Mexico and Germany have slightly less units sold.

<span class="badge bg-primary">Sales by Country - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_country_sales.png)
<div class="mt20"></div>

Sales are almost evenly distributed between the five countries. Mexico has slightly less sales.

<span class="badge bg-primary">Profit by Country - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_country_profit.png)
<div class="mt20"></div>


Profits have the same magnitude for all five countries. France, Germany and Canada form a group with higher profits. USA and Mexico have slightly less profit.


It might be worth taking into account the size of relative markets (e.g. using country population) to derive specific performance for individual countries.

<h5>Analysis of sales over products</h5>


<span class="badge bg-success">Units sold by Product - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_product_unnits.png)
<div class="mt20"></div>

The product 'Paseo' (interpreted as a bike for easy roads and use) represents 30% of all products sold in numbers.

The other 5 products constitute about 14% of the total each.


<span class="badge bg-success">Sales by Product - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_product_sales.png)
<div class="mt20"></div>

The product 'Paseo' contributes to outstanding sales.

<span class="badge bg-success">Profit by Product - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_product_profit.png)
<div class="mt20"></div>

The product 'Paseo' contributes to outstanding profit.

<span class="badge bg-success">Profit by Product - Scatter-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_product_profit_vs_sales.png)
<div class="mt20"></div>

The relation between Profit and Sales is similar for all 6 products, with products 'VTT' and 'Amarilla' producing profit above the average of the whole product range.



<h5>Analysis of sale price</h5>

It is understood that the Sale Price depends on the Product (i.e. type of bike)

With Sale Price (i.e. by product unit) varying by a factor 50 over the dataset for consumer goods (bikes), I want to understand to variation.


<span class="badge bg-success">Count of Sale Price - Matrix</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_sale_price_count_matrix.png)
<div class="mt20"></div>

Each combination of features ( Product ; Segment ; Country ) has one single Sale Price across the dataset, except for the segment 'Government', that has 3 different values of Sale Price.

<span class="badge bg-success">Sale Price - Matrix</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_sale_price_matrix.png)
<div class="mt20"></div>

For all segments except 'Government', ...

... For a given combination of features (Segment ; Country), the Sale Price is identical for all 6 types of Product, which feels NOK.

For reference, for the same segmentation, the Manufacturing Price differs for the 6 types of Product.


For the segment 'Government', the Sale Price varies for a given combination ( Country ; Product ).

For example, for the combination ( 'Government' ; 'USA' ; 'Amarilla' ), the values of Sale Price range from 7 to 350. No correlation of these values can be found with the number of Units Sold, nor can a trend vs. dates be seen. Possibly a logic could be found from data pre-aggregation, i.e. outside of the working dataset.

The Sale Price depends highly on the 'Segment' i.e. the customer: 
<ul>
  <li>Channel Partners: 12</li>
  <li>Midmarket: 15</li>
  <li>Enterprise: 125</li>
  <li>Government: 126 as an average</li>
  <li>Small Business: 300</li>
</ul>

No trend can be seen with the size of the target customer (i.e. there is no continuous trend from Small Business to Midmarket to Enterprise).

Possibly the pricing logic is strategic.


<h5>Analysis of discounts</h5>


<h6>Discounts and margin</h6>

Cumulated discounts amount to 7% of total sales.

I want to study how discounts affect the margin.

I create a column for the percentage of discount per record.


<span class="badge bg-success">Discount percentage - Matrix</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_discount_matrix.png)
<div class="mt20"></div>

When viewing the discount percentage for each combination of features (Discount Band ; Segment ; Country ), while there some variations, the trend is clear: the magnitude of discount depends on the Discount Band:
<ul>
  <li>None: 0% discount</li>
  <li>Low: 2% discount as an average</li>
  <li>Medium: 7% discount as an average</li>
  <li>High: 13% discount as an average</li>
</ul>

<span class="badge bg-warning">Margin percentage vs. Discount percentage - Scatter-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_discount_scatter_1.png)
<div class="mt20"></div>

Mapping the average margin percentage vs. the discount percentage by segmenting by either Segment, or  Country does not show a trend.

<span class="badge bg-success">Margin percentage vs. Discount percentage - Scatter-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_discount_scatter_2.png)
<div class="mt20"></div>

Mapping the average margin percentage vs. the discount percentage by segmenting by (Segment ; Country : Product ) allows to reveal the trend. One linear trend can be seen for each of the five Segments. The average margin percentage decreases linearly with the discount percentage.


<h6>Discounts and units sold</h6>


<span class="badge bg-success">Units sold vs. Discount percentage - Scatter-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_units_discount_scatter.png)
<div class="mt20"></div>

Mapping the number of units sold vs. the discount percentage by segmenting by Month allows to reveal a soft trend. Though is there is scatter, the general trend is the number of units sold increases with the level of discount percentage. The positive trend is in fact generated by the end-of-year months: September, October, November and December.

<span class="badge bg-secondary">Number of sales records vs. Discount percentage - Scatter-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_units_count_discount_scatter.png.png)
<div class="mt20"></div>

Mapping the number of sale records vs. the discount percentage by segmenting by Month allows to reveal a soft trend. Though, by month, there are either 35 or 70 sales records, the mathematical trend is the number of sales records increases with the level of discount percentage.


Since the months with the most sales (either in terms of units sold, or in terms of sales records) are the end-of-year months: September, October, November and December, it may be argued that the season is driving sales, and not the level of discounts.

Factually, in the dataset, high sales are correlated with higher discounts. Causality might not be provable.


<h4>Analysis of sales over time</h4>

Data is only available for the last third of year 2013. Hence a comparison between 2013 and 2014 is only possible for a partial year.

For one given year, the magnitude of sales, and the fact that they are already aggregated, allow a representative comparison between months.

<h5>Analysis of time of year</h5>

The analysis of the time of year is performed at the level of the month.

Since the year 2013 is incomplete in the dataset, the comparison between month is performed whiel separating years 2013 and 2014.


<span class="badge bg-success">Sales - Bar-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_month_sales_2013.png)
<div class="mt20"></div>


For 2013, the month of October has the largest revenue.


![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_month_sales_2014.png)
<div class="mt20"></div>

For 2014, the months of October and December have the largest revenues.


<span class="badge bg-success">Count of sales - Bar-chart</span>

Given the pre-aggregated nature of the dataset, this may or may not show the popularity of sales at moments of the year.

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_month_sales_count_2013.png)
<div class="mt20"></div>

For 2013, the month of October has the largest number of sales records.

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_month_sales_count_2014.png)
<div class="mt20"></div>

For 2014, the months of October and December and June have the largest number of sales records.

<span class="badge bg-success">Units sold - Bar-chart</span>

For 2013, the month of October has the largest number of units sold.

For 2014, the months of October and December and June have the largest number of units sold.


The trend observed for several figures would hint on busy Q4's, if it wasn't for the poor performance of month of November 2014.

<h5>Analysis of evolution</h5>

<span class="badge bg-secondary">Sales - Line-chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_time_sales.png)
<div class="mt20"></div>

A line-chart shows that sales fluctuate, with up's and down's from one month to another. No visible trend can be seen.

The month of November 2014 shows a specific drop in all figures: Sales (Gross and Net, COGS, Profit, Discounts).

The superimposition of the partial year 2013 with the complete year 2014 only highlights the steady performance of the month of October. 



<h3>Dashboard</h3>

My one-page dashboard aims at providing macroscopic sales figures, allow to study the segmentation of sales, and view the evolution of performance over time.

The bar-chart for segmentation display values for one figure (or more than one, in which case bars are gouped), dynamically with the parameter selected by the user in the associated slicer.

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_dashboard_1.png)
<div class="mt20"></div>

<h3>Storytelling report</h3>

I chose to focus on the decrease in sales for November 2014, with the aim to showing its causes.

Possible explanations a priori for November 2014 are:
<ul>
  <li>Specific behaviour of the customers in terms of segment</li>
  <li>Specific behaviour of the customers in terms of country</li>
  <li>Specific behaviour of the sold products</li>
  <li>Time of year</li>
  <li>Specific discounts</li>
  <li>Specific sale prices</li>
  <li>Specific internal costs</li>
  <li>Specific marketing</li>
</ul>



<span class="badge bg-secondary">Sales by Segment - 100% Stacked-area chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_time_sales_segment.png)
<div class="mt20"></div>

The distribution of sales by Segment remains stable, with only little fluctuations, for the studied period - The month of November has no specific behaviour.

<span class="badge bg-secondary">Sales by Country - 100% Stacked-area chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_time_sales_country.png)
<div class="mt20"></div>

The distribution of sales by Country remains stable, with only little fluctuations, for the studied period - The month of November has no specific behaviour.

<span class="badge bg-success">Sales by Product - 100% Stacked-area chart</span>

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_time_sales_product.png)
<div class="mt20"></div>

The month of November has a particularly large proportion of product 'Paseo', i.e. the money-maker: 75% of sales, while it never goes above 50% for other months.


<span class="badge bg-secondary">Average Sale Price - Line-chart</span>

As seen before, the Sale Prices for the different products vary. In particular they are shuffled over products and over time in the dataset.

Notably, the Sale Price averaged over all products remains absolutely constant over the period.

![webjeda cards jekyll theme]({{site.baseurl}}/images/train_finance_time_sale_price_paseo.png.png)
<div class="mt20"></div>

Viewing the evolution of the Sale Price along the period, discrimated by Product, allows to see the specific sharp increase in Sale Price for the Product 'Paseo', and for November 2014 (x4 vs. previous month).

This increase in Sale Price of the money-making product might have acted as a deterrent, and might explain the drop in Sales for November 2014.

It does not explain why other products of the range suffer from a drop in sales at the same month. However, the drop in sales of product 'Paseo' is steeper than for the other products.







