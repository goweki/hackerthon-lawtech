# hackerthon-lawtech
An observatory as developed during the Africa Law Tech Festival 2023 

## Trade Data Scrapper Solutions Comparison
Two open source trade data APIs were found.  
Platform one is the [WITS REST API](https://wits.worldbank.org/witsapiintro.aspx?lang=en) and platform two is [UN Comtrade](https://comtrade.un.org/data/doc/API_MBS)

### 1. WITS World Integrated Trade Solution API from the WorldBank
Offers a variety of data, including: 
- a detailed import and export statistic which also includes services and income instead of just goods.
- detailed import and export statistics between countries down to a product level.
It's biggest downside is **data ends in 2020**.
- sometimes earlier
### 2. UN Comtrade
Offers Data on:
- _simple_ import and export statistic which only includes goods.
- _simple_ import and export statistics on product level (country vs world level).
It's biggest downside is **product level data ends in 2017*.

## Data Scrapper Solutions Implementation Guideline
### WITS API
Use example url template: 'http://wits.worldbank.org/API/V1/SDMX/V21/datasource/tradestats-tariff/reporter/usa/year/2000/partner/jpn/product/fuels/indicator/AHS-SMPL-AVRG?format=json'  

Play around with country country codes, year, partner, product and indicator. Further documentation on those can be found [here](https://wits.worldbank.org/witsapiintro.aspx?lang=en). If parameters are not needed just leave them out, e.g. `http://wits.worldbank.org/API/V1/SDMX/V21/datasource/tradestats-development/reporter/usa/year/2020/indicator/BX-GSR-TOTL-CD?format=JSON` for imports and exports, including services and income in 2020 of the USA. 

As the country codes are ISO normalized, it will quite easy to filter out only African countries and map them to a world map. 

### UN Comtrade
The UN Comtrade api is very much query-parameter based. An example of requesting a specific table, for a specific year, for a specific country looks like this: `https://comtrade.un.org/api/getMBSData?series_type=T35.A.V.$&year=2022&country_code=842`

Country codes are not ISO normalized this type, but there is a JSON providing the country name to each country code, meaning one only needs a list of African countries. 

## Similar solutions to the proposed concept
African Trade observatory: https://ato.africa/en
