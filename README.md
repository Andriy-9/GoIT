# GoIT
Demonstration project in SQL
1. Decoding the utm_campaign value by creating a temporary function [(converting Cyrillic letters to url parameters)](https://github.com/Andriy-9/GoIT/blob/302d60893d057edf9c3c4764c38064c05ee67289/Demonstration_project_SQL.txt#L1)
2. The [CTE query](https://github.com/Andriy-9/GoIT/blob/302d60893d057edf9c3c4764c38064c05ee67289/Demonstration_project_SQL.txt#L45) combines the data from the tables (facebook_ads_basic_daily, facebook_adset, facebook_campaign, google_ads_basic_daily) into a consolidated table for further calculation of the indicators:
- ad_date - the date when the ad was shown on Google and Facebook;
- url_parameters - part of the URL from the campaign link that includes UTM parameters;
- spend, impressions, reach, clicks, leads, value - metrics of campaigns and ad sets on the respective days.
3. [A selection is made from the received CTE:](https://github.com/Andriy-9/GoIT/blob/302d60893d057edf9c3c4764c38064c05ee67289/Demonstration_project_SQL.txt#L130)
- ad_date - the date of the advertisement;
- utm_campaign - the value of the utm_campaign parameter from the utm_parameters field that meets the following conditions: it is reduced to lower case; if the value of utm_campaign in utm_parameters is 'nan', then it must be empty (i.e. null) in the resulting table;
- total cost, number of impressions, number of clicks, and total Conversion Value on the relevant date for the relevant campaign.
