# GoIT
Analyzing the effectiveness of advertising campaigns (SQL)
1. Decoding the utm_campaign value by creating a temporary function [(converting Cyrillic letters to url parameters)](https://github.com/Andriy-9/GoIT/blob/302d60893d057edf9c3c4764c38064c05ee67289/Demonstration_project_SQL.txt#L1)
2. The [CTE query](https://github.com/Andriy-9/GoIT/blob/302d60893d057edf9c3c4764c38064c05ee67289/Demonstration_project_SQL.txt#L45) combines the data from the tables (facebook_ads_basic_daily, facebook_adset, facebook_campaign, google_ads_basic_daily) into a consolidated table for further calculation of the indicators:
- ad_date - the date when the ad was shown on Google and Facebook;
- url_parameters - part of the URL from the campaign link that includes UTM parameters;
- spend, impressions, reach, clicks, leads, value - metrics of campaigns and ad sets on the respective days.
3. [A selection is made from the received CTE:](https://github.com/Andriy-9/GoIT/blob/302d60893d057edf9c3c4764c38064c05ee67289/Demonstration_project_SQL.txt#L130)
- ad_date - the date of the advertisement;
- utm_campaign - the value of the utm_campaign parameter from the utm_parameters field that meets the following conditions: it is reduced to lower case; if the value of utm_campaign in utm_parameters is 'nan', then it must be empty (i.e. null) in the resulting table;
- total cost, number of impressions, number of clicks, and total Conversion Value on the relevant date for the relevant campaign.

Scoring the respondent questionnaires (Python)
1. The data of the resulting table, consisting of two files, [is cleaned according to the following rules](https://github.com/Andriy-9/GoIT/blob/9a86bae164fc4763e36fc5d047cb9ce8d4dba770/Demonstration_project_Python#L1):
- duplicates of 'applicant_id' have been removed;
- in the 'External Rating' field, fill in the missing values with zeros;
- in the 'Education level' field, fill in the missing values with the text "Average".
2. The industry rating has been added to this DataFrame.
[Rules](https://github.com/Andriy-9/GoIT/blob/becfd94652a78fcf4a6e2bf6c82438e8ca1f368d/Demonstration_project_Python#L32) for creating an industry rating:
- if the applicant's age is between 35 and 55, 20 points are added to the rating;
- if the application was submitted on a weekend, 20 points are added to the rating;
- if the applicant is married, 20 points are added to the rating;
- if the applicant is located in Kyiv or the region, 10 points are added to the rating;
- the 'Score' value is also added to the application (and ranges from 0 to 20 points);
- if the 'External Rating' is greater than or equal to 7, 20 points are added to the rating;
- if the 'External Rating' is less than or equal to 2, 20 points are deducted from the rating.
Conditions of rating formation:
- the rating must be a number from 0 to 100;
- rating is the sum of the application scores for 6 criteria;
- the rating is zero if there is no 'Amount' value or if the 'External Rating' is zero.
3. Only applications with a [rating greater than zero](https://github.com/Andriy-9/GoIT/blob/becfd94652a78fcf4a6e2bf6c82438e8ca1f368d/Demonstration_project_Python#L69) are left in the resulting table, such applications are accepted.
4. The data from the resulting table is [grouped by the week](https://github.com/Andriy-9/GoIT/blob/becfd94652a78fcf4a6e2bf6c82438e8ca1f368d/Demonstration_project_Python#L83) of application submission, and the average rating of accepted applications in each week is displayed.
5. A [graph](https://github.com/Andriy-9/GoIT/blob/becfd94652a78fcf4a6e2bf6c82438e8ca1f368d/Demonstration_project_Python#L90) of the average rating of accepted applications for each week was created.
