# Regression Analysis to Find Public & Private Housing Projects with the Best ROI in the Past 5 Years, by District (2024)

## 1. Introduction
The objective of this analysis is to assess the potential future ROI on public vs private housing projects for someone to purchase for their future residence in 2024.\
\
My analysis aims to measure the selling prices in "Unit Price ($PSF)" of dozens of HDB projects and private condos over the past 5 years (March 2019 to March 2024). I hypothesise that certain desirable HDB projects have, and will continue to, perform comparably to private housing projects of similar size and location.\
\
In addition, I propose that the average annual appreciation of most of Singapore property projects, both public and private, is inferior to the average annual asset appreciation of the S&P 500 index and other assets, so we theorise that it would be more efficient for us to put less total investment quantum into Singapore property, to enable us to diversify our assets across this more stable but lower-performing asset as well as allocating a similar proportion of our portfolio to slightly riskier but higher-performing assets over the long run to prepare us for retirement.


### Project Overview
The project involves the following key steps:

- **Data Sourcing, Cleaning & Transformation**: Obtained and processed source datasets from HDB and URA.
- **Statistical Modelling**: Implemented linear regression models to analyze price trends for thousands of housing projects, calculating yearly price gradients and making future price predictions.
- **Automation**: Developed two Python scripts to automate the analysis process for both private and public housing data, enabling efficient processing of thousands of housing projects.
- **Data Visualisation**: Used libraries like Matplotlib and Plotly to generate visualisations.

## 2. Price Indices

The script `sg_house_prices_sp500.py` can be used to generate graphs of Singapore house pricing indices plotted against the S&P 500 up till Feb 2024, using a baseline as far back as Jan 2009. Almost all baseline dates chosen will show that the S&P 500 appreciates at a much faster rate than any sector of the Singapore housing market. \
\
Sample graph:
![sg-houseprice-s p500-index-graph](https://github.com/letitia/sghousingprices2024/assets/1286070/fffb7f22-a8e1-48a8-b06c-350c6044701a)


## 3. Methodology

I sourced the HDB resale data from HDB and the private condo resale data from URA. This was what the raw data looked like.
Example rows of HDB data ([Source: HDB](https://beta.data.gov.sg/collections/189/datasets/d_ebc5ab87086db484f88045b47411ebc5/view)):
| month | town | flat_type | block | street_name | storey_range | floor_area_sqm | flat_model | lease_commence_date | remaining_lease | resale_price |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| 2019-03 | ANG MO KIO | 4 ROOM | 308A | ANG MO KIO AVE 1 | 04 TO 06 | 94 | Model A | 2012 | 92 years 07 months | 591688 |

Example rows of private condo data ([Source: URA](https://www.ura.gov.sg/property-market-information/pmiResidentialTransactionSearch)):

To analyse the investment potential of each housing project, I consolidated resale transaction data for each property, ensuring a comprehensive dataset for the past 5 years. Employing Linear Regression analysis in Python, I plotted a trend line that best represents the trajectory of the Unit Price per Square Foot (PSF) over time. This trend line, mathematically determined to minimise the distance from all data points, effectively captures the average annual rate of increase—or gradient—in Unit Price PSF. Thus, it offers an indication of how the property's value has appreciated each year, on average, during the specified period.\
\
To measure this number as a percentage of the asset’s original value, I divided the average annual gradient by the value predicted by the regression in the first available month of data.

### Example Graphs
HDB Project:
![Unit Price (PSF) over time for Cantonment Rd (2011)](https://github.com/letitia/sghousingprices2024/assets/1286070/90d525bb-eeb5-4c0e-9c04-656fc145a3bc)


Private Project:
![Unit Price (PSF) over time for Skysuites@Anson](https://github.com/letitia/sghousingprices2024/assets/1286070/1756f36a-2474-4dcc-b222-00ed4df4d95c)


### Limitations / Further Studies
- The study focused on selected districts within Singapore, determined by our preliminary preferences. We excluded areas like Sembawang, Yishun, Tampines, Pasir Ris, Bukit Panjang, Choa Chu Kang, etc that we felt were too far. This means the findings may not represent trends applicable to the broader real estate market across all districts.
  - Within the chosen districts, for HDB I analysed data only from projects that TOP-ed in 1991 or later (this excluded towns such as Marine Parade and Bukit Timah, which only had old flats), whereas I analysed all condos in the chosen districts regardless of age.
- The robustness of data varies across projects, with projects having higher transaction volumes providing more reliable trends. Public housing projects, which generally had more data points due to a higher number of transactions, offered more accuracy compared to private projects with fewer sales.
  - We studied only 130 HDB projects, but each of them had a mean of 240 data points and a median of 150 data points.
  - We studied 1,400 private condos, with a mean of 28 data points and a median of 13 data points.
- For the public dataset, I was unable to filter out the units that were limited by ethnic quota, which means there were some units that sold for artificially lower prices (that I as a Chinese buyer could not qualify for).
- The Unit Price ($PSF) was calculated across all sold units in each housing project, regardless of floor area, project age, or storey range. In practice, the Unit Price can vary widely for flats in the same project depending on the floor area, and our data spanned the smallest units (400 sqft for public, 333 sqft for private) to the largest units (1860 sqft for public all the way up to a staggering 207,000 sqft for private). Our model with only date and unit price may be too simplistic to accurately capture the dynamics of the real estate market. Incorporating additional independent variables such as floor area and remaining lease years into our regression model can significantly enhance its accuracy and predictive power.
- Rental yield was excluded from this analysis, as the primary purpose of this property is to function as the couple's residence. It could be added in a future iteration of this analysis.
- Past data does not predict future performance. External factors, such as regulatory changes or infrastructural developments (e.g., the construction of a new MRT line), can significantly influence market dynamics in ways that past trends may not fully capture. 
- My study did not extend to predicting future housing prices. While I could potentially develop a more sophisticated model that included broader market and macroeconomic indicators—such as Singapore's inflation rate, interest rates, Additional Buyer's Stamp Duty (ABSD) rates, and the overall housing supply—forecasting these variables accurately is challenging. I concluded that the effort required to develop such a predictive model, coupled with the uncertainty surrounding the future values of these indicators, was not justified by the potential benefits this model might offer.


### Comparing public and private datasets
Both datasets use resale data only, so there is no confounding factor of BTO prices or developer prices.\
\
There was much more HDB data available than condo data. For example, HDB data was available all the way back to 1990, whereas condo data was only available for the past 5 years (from March 2019 onward). To simplify and make it a fair comparison, I only used the HDB data for the same timeframe as the condo data.

## 4. Results
[Redacted for privacy reasons]

## 5. Conclusion & Recommendations
[Redacted for privacy reasons]

## 6. License
This project is licensed under the MIT License - see the LICENSE file for details.
