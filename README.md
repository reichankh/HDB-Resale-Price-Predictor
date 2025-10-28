# Beyond the Flat: What Really Drives HDB Resale Value 
<img width="500" height="500" alt="pinnacle_logo1" src="https://github.com/user-attachments/assets/eed3075d-dbfb-4505-9e55-ded4a7772fe3" />

<p style="color:#6a737d; font-style:italic;">
  Presented By:  Rei, Alina, Daniel, Leon, Nigel, Tiffany (Pinnacle Ventures)
</p>


## Description
HDB resale value today goes beyond traditional factors like distance to the nearest MRT station or remaining lease. The model incorporates a wider mix of micro factors (e.g., floor area, block height, proximity to amenities - mall/hawker centre, distance to nearest popular primary schools, neighbourhood affluency) and macro drivers (e.g., inflation (CPI), household income (MHI), GDP growth, upcoming MRT station).

The product combines multiple factors into a single resale price prediction, presenting HDB values in a holistic way. It provides buyers and agents with credible insights to support confident and data-driven decisions.

## Streamlit App Link
Click on the link for interactive demo
https://hdb-resale-price-predictor-micro-macro-features.streamlit.app/

## Data Dictionary
Below is a summary of the data used and their descriptions:

| Column Name	| Description	| Data Type |
| --- | --- | --- | 
| resale_price | the property's sale price in Singapore dollars | Integer |
| demand* | Based off the 1room_sold to studio_apartment_sold and given weightage | Float |
| age_at_sale*  | Taken as transaction year minus lease commencement  | Integer |
| max_floor_lvl | The highest floor in the block | Integer |
| lease_commence_date | When the block’s lease began | Integer |
| Month | Month of the transaction | Integer |
| Tranc_Year  | The year which the transaction happened | Integer |
| affluent_index* | It is the combination of the ranking of the average price by town, ranking the floor category and ranking the flat type. | Float |
| hdb_age  | Number of years from lease_commence_date to present year | Integer |
| floor_area_sqm  | The size of the apartment that was transacted in square meters | Integer |
| amenity_proximity_score* | It is the sum of the average distances between the nearest Mall and Hawker | Float |
| transport_proximity_score* | It is the sum of the average distances between the nearest MRT and Bus Stop | Float |
| amenities_within_1km* | The total number of amenities (Malls and Hawkers) within 1km | Integer |
| avg_subs_sch* | It is the average subscription rate of the schools in the same town | Float |
| num_top_sch* | It is the total number of top schools in the town. And top schools is based off if the subsriptions of a school exceed 200% | Integer |
| mrt_development*| Ranking the development of an MRT station. The rankings are 5 if MRT in development, 4 MRT was built within 2 years, 3 if within 5 years, 2 if within 7 years and 1 for the rest | Integer |
| CPI* | Consumer Price Index by Year | Float |
| GDPM* | Gross Domestic Product by Quarter | Float |
| MHI* | Median Household Income by Quarter | Float|

## ML Model Results
4 ML models (LightGBM, CatBoost, Random Forest, Extra Trees) were built to learn and predict the HDB resale prices.

Below is an overview of the models and their performance outcomes:

<table style="border:1px solid #d0d7de; border-collapse:collapse; width:100%;">
  <thead>
    <tr>
      <th style="padding:6px 10px;">Model</th>
      <th style="padding:6px 10px;">Train Accuracy</th>
      <th style="padding:6px 10px;">Test Accuracy</th>
      <th style="padding:6px 10px;">RMSE</th>
      <th style="padding:6px 10px;">Runtime</th>
    </tr>
  </thead>
  <tbody>
<tr style="background:#fff3cd;"> <!-- Light yellow highlight -->
      <td><strong>LightGBM</strong></td>
      <td><strong>99.61%<strong></td><td><strong>97.02%<strong></td><td><strong>S$24,622<strong></td><td><strong>12.5s<strong></td>
    </tr>
    </tr>
    <tr>
      <td style="padding:6px 10px;">CatBoost</td>
      <td style="padding:6px 10px;">97.06%</td>
      <td style="padding:6px 10px;">96.58%</td>
      <td style="padding:6px 10px;">S$26,371</td>
      <td style="padding:6px 10px;">52.3s</td>
    </tr>
    <tr>
      <td style="padding:6px 10px;">Random Forest</td>
      <td style="padding:6px 10px;">99.52%</td>
      <td style="padding:6px 10px;">96.58%</td>
      <td style="padding:6px 10px;">S$26,372</td>
      <td style="padding:6px 10px;">22.9s</td>
    </tr>
        <tr>
      <td style="padding:6px 10px;">Extra Trees</td>
      <td style="padding:6px 10px;">100.00%</td>
      <td style="padding:6px 10px;">96.70%</td>
      <td style="padding:6px 10px;">SS$26,047</td>
      <td style="padding:6px 10px;">4.8s</td>
    </tr>
  </tbody>
</table>
 
LightGBM achieved the best balance of train and test accuracy, model discrepancies and runtime. It delivered a strong predictive performance with no significant overfitting.


## Conclusion
Our analysis shows that remaining lease, MRT proximity, flat size and type, storey level, neighbourhood affluence, and proximity to popular schools are key drivers of HDB resale prices, with premiums seen in CBD areas and locations with strong MRT access. Macro factors such as inflation (CPI), household income (MHI), economic growth (GDP), and government policies also influence market demand and pricing trends.

The model combines these micro and macro insights into a data-driven price estimate, giving buyers, sellers, and agents credible guidance for make confident decisions. 
As the market continues to evolve, incorporating new data sources such as news and sentiment trends can further improve forecast accuracy and capture changes in buyer behaviour.
