# GoIT
Demonstration projects
1. Decoding the utm_campaign value by creating a temporary function (converting Cyrillic letters to url parameters)
2. The CTE query combines the data from the tables (facebook_ads_basic_daily, facebook_adset, facebook_campaign, google_ads_basic_daily) into a consolidated table for further calculation of the indicators:
- ad_date - the date when the ad was shown on Google and Facebook;
- url_parameters - part of the URL from the campaign link that includes UTM parameters;
- spend, impressions, reach, clicks, leads, value - metrics of campaigns and ad sets on the respective days.
3. A selection is made from the received CTE:
- ad_date - the date of the advertisement;
- utm_campaign - the value of the utm_campaign parameter from the utm_parameters field that meets the following conditions: it is reduced to lower case; if the value of utm_campaign in utm_parameters is 'nan', then it must be empty (i.e. null) in the resulting table;
- total cost, number of impressions, number of clicks, and total Conversion Value on the relevant date for the relevant campaign.
