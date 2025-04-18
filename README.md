# IS 6813 University of Utah Capstone Portfolio
This repository contains code I developed individually as part of a group capstone project at the University of Utah.

## Getting started
The Spring 2025 capstone project was hosted and sponsored by Swire Coca-Cola. This was a group project in which I collaborated with Andrew Delis, Kleyton Polzonoff, and Nidal Arain—two of whom I had previously worked with during the earlier capstone course (IS 6812).

## The business problem
Swire presented us with a logistics optimization challenge. In a nutshell, they have two delivery options for fulfilling customer orders: third-party delivery services—referred to as Alternate Route to Market (ARTM) or "White Trucks"—and their own delivery fleet, known as "Red Trucks." While using Red Trucks is more expensive, it offers a superior customer experience and is therefore better suited for high-value customers. The core issue Swire faced was determining how to identify these high-value customers — either based on growth potential or other customer characteristics.

## Benefit of a solution
According to Swire, Red Truck deliveries can cost up to eight times more than White Truck deliveries. Historically, Swire used a fixed threshold — 400 gallons of annual order volume — to determine delivery assignments. As you can imagine, relying solely on a fixed threshold likely excludes some high-growth potential customers while unnecessarily assigning costly Red Truck deliveries to others who may not warrant it.

By developing a data-driven approach for fleet assignment, Swire stands to not only reduce delivery costs but also improve service for customers who are truly high-value or have strong growth potential.

## Approach to Data Analysis
The datasets provided by Swire were somewhat challenging to work with. In total, there were four different tables: a transactional dataset, a customer dataset, a cost dataset, and an address mapping dataset. While the volume of data was sufficient, it was limited in terms of timeframe—we only had two years of transactional data. As mentioned earlier, one of the project goals was to identify customers with growth potential. Early on, I realized that time series forecasting might not be the best approach due to the limited timeframe. Instead, focusing on customer characteristics seemed like a more suitable strategy.

With my background in analytics engineering, my primary goal was to engineer as many useful features as possible. I focused on aggregated transactional data and explored the creation of a binary target variable using yearly totals. I also re-aggregated the data to a one-row-per-customer format, which could be helpful for future modeling efforts.

Much of my analysis then focused on examining different cold drink channels to explore potential cost savings. It's worth noting that at this point, we didn't have clear data on the actual monetary impact of Red Truck deliveries. All we knew — based on what Swire shared — was that Red Trucks offered better service. However, there was no quantifiable service quality metric available in the data.

**Group approach:** As a group, our approaches were largely aligned. We aimed to create as many meaningful and usable variables as possible. Ultimately, we incorporated features related to growth and order frequency, such as the RFM score (Recency, Frequency, Monetary), which turned out to be a key driver in our project.

## Modeling
MMy individual modeling approach primarily focused on tree-based classification models. I started by using the original 400-gallon threshold to define a binary target: predicting whether a customer’s next-year volume would be more or less than 400 gallons. I used the previous year's volume along with other customer characteristics as features. Overall, the models performed well; however, as a group, we later decided that this approach didn’t align fully with the project scope.

In addition to machine learning, I explored customer grouping strategies. Specifically, I identified a subset of local market partners with yearly volumes under 400 gallons but consistent ordering patterns (at least one order per month). We grouped these customers by ZIP code to explore opportunities for more efficient delivery routing.

**Group approach:** As a group, we ultimately chose a somewhat unconventional — but very interesting — modeling strategy. We used an unsupervised learning method, specifically clustering, as our primary approach for customer segmentation. The clusters would primarily guide fleet assignment, supported by additional criteria derived from engineered features—such as a high growth potential flag. I thought this was a strong approach, especially considering the data quality challenges. It became clear that simply applying a volume threshold wouldn’t work well for this project.

## Business value of the solution
As mentioned earlier, our group chose not to pursue the machine learning methods I initially worked on. However, we did explore the customer grouping method further and found some promising results. We estimated that Swire could realistically save around $900,000 per year using this method. Still, since it didn’t fully align with the project scope, we kept it in our back pocket as a secondary approach.

**Group solution:** The clustering approach turned out to be quite successful — or at least, we believed so. Using this method, we were able to reassign fleet types for over 4,000 customers, increase the number of Red Truck customers, reduce the total volume delivered by Red Trucks (leading to cost savings), and increase the delivery frequency for Red Truck customers. In short, this meant that Swire could serve more customers at a lower cost while also improving service quality — all key objectives they had set for the project.

## Difficulties faced as a group
The biggest challenge we faced was the data itself. As mentioned before, we couldn’t clearly determine the impact of Red Trucks from the available data. The transactional data was limited to just two years, and some datasets—such as the address information—contained more noise than usable insights.

Additionally, while exploring different modeling approaches, we occasionally struggled with alignment. There were moments when we didn’t fully understand what other group members were trying to achieve with their methods. On top of that, we faced the usual group project hurdles, such as conflicting schedules and timing issues.

## My contribution to the project
From an operational standpoint, I primarily took on an organizational role within the group. I scheduled meetings, made workflow recommendations, and frequently commented on or questioned our approaches to help keep us aligned.

From a work output perspective, as discussed earlier, I contributed heavily to analysis and modeling. However, much of that work wasn’t included in our final proposal, as we ultimately chose a different direction as a team.

## What I learned in the project
Prior to this project, I wasn’t familiar with the RFM (Recency, Frequency, Monetary) framework, and I had limited experience working with customer growth and growth potential. This project gave me the opportunity to gain valuable exposure to those concepts.
