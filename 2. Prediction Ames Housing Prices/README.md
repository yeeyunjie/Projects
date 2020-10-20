Project 2: Prediction of Housing Prices in Ames,Iowa
---

### Problem Statement

With a large amount of collected data about characteristics of houses in Ames, we would like to find out the underlying reasons and motivations for an important consideration
of every house owner: **Cost of House**. One way of doing so is train a model that takes these features as inputs, where it recognizes and weighs the influence of fed features
on our resultant output which in particular is the `SalePrice` and provide predictions of houses that share the same characterisitics. Therefore we aim to derive the **optimum model**
that gives the **most accurate predictions** when compared to the actual house prices in our past data. With such a versatile model, it would be helpful and viable to a wide range of
consumers as it not only provides an accurate prediction of housing prices for home buyers but also equip home sellers with the knowledge on maximizing their profit margins through
leveraging on certain qualities that strongly influence housing prices.

### Executive Summary
Cleaning and analyzing the given data have formed the biggest bulk of this project as the features chosen as inputs have a large influence on the output of the model. The huge presence 
of null values has warranted the removal of several features that would not have meaningful contributions to our target variable `SalePrice` since most of the values are missing. Through
 the analysis of over 50 features, several important variables stood out in terms of its correlation with our target variable and such features include `Overall Qual`, `Gr Liv Area` and
 interestingly the number of `Garage Cars`. The strong correlations established warranted our attention on several outliers which would have skewed our model significantly and therefore 
were carefully selected and removed. After imputing numerical values and encoding categorical values on selected features, the same set of modified and regularized variables were fed into 
several models with different parameters in hopes of deriving the optimal model which gives us predictions that are the closest to the actual data through the metrics such as root mean 
square error(RMSE). Ultimately, the optimal model which gives us the **lowest RMSE and highest r2 score** was the **Lasso model**. This optimized model would be highly versatile due to 
its applicability to both home owners and sellers who are either looking to **minimize their expenditure on such a necessity** or to **maximize their profits when selling their properties.** 


### Data Dictionary
#### Data Dictionary for `df_train`: <br>

|Feature|Type|Dataset|Description|
|---|---|---|---|
|id|int|entire_df|Id number| 
|pid|int|entire_df|Parcel identification number| 
|ms_subclass|onject|entire_df| Type of dwelling | 
|ms_zoning |object|entire_df|general zoning classification of the sale| 
|lot_frontage|float|entire_df|Linear feet of street connected to property|
|lot_area|int|entire_df|Lot size in square feet|
|street|object|entire_df|Type of road access to property| 
|lot_shape|object|entire_df|Type of alley access to property|
|land_contour|object|entire_df|Flatness of the property| 
|lot_config|object|entire_df|Lot configuration| 
|land_slope|object|entire_df|Slope of property|
|neighborhood|object|entire_df|Physical locations within Ames city limits| 
|condition_1|object|entire_df|Proximity to various conditions| 
|condition_2|object|entire_df|Proximity to various conditions| 
|bldg_type|object|entire_df|Type of dwelling| 
|house_style|object|entire_df|Style of dwelling| 
|overall_qual|int|entire_df|Rates the overall material and finish of the house|  
|overall_cond|int|entire_df|Rates the overall condition of the house |
|year_built|int|entire_df|Original construction date|  
|year_remod/add|int|entire_df|Remodel date | 
|roof_style|object|entire_df|Type of roof| 
|roof_matl|object|entire_df|Roof material| 
|exterior_1st|object|entire_df|Exterior covering on house| 
|exterior_2nd|object|entire_df|Exterior covering on house (if more than one material)| 
|mas_vnr_type|object|entire_df|Masonry veneer type|
|mas_vnr_area|float|entire_df|Masonry veneer area in square feet|
|exter_qual|object|entire_df|Evaluates the quality of the material on the exterior| 
|exter_cond|object|entire_df|Evaluates the present condition of the material on the exterior| 
|foundation|object|entire_df|Type of foundation| 
|bsmt_qual|object|entire_df|Evaluates the height of the basement|
|bsmt_cond|object|entire_df|Evaluates the general condition of the basement |
|bsmt_exposure|object|entire_df|Refers to walkout or garden level walls| 
|bsmtfin_type_1|object|entire_df|Rating of basement finished area| 
|bsmtfin_sf_1|float|entire_df|Type 1 finished square feet|
|bsmtfin_type_2|object|entire_df|Rating of basement finished area| 
|bsmtfin_sf_2|float|entire_df|Type 2 finished square feet|
|bsmt_unf_sf|float|entire_df|Unfinished square feet of basement area|
|total_bsmt_sf|float|entire_df|Total square feet of basement area|
|heating|object|entire_df|Type of heating |
|heating_qc|object|entire_df|Heating quality and condition |
|central_air|object|entire_df|Central air conditioning| 
|electrical|object|entire_df|Electrical system| 
|1st_flr_sf|int|entire_df|First Floor square feet|  
|2nd_flr_sf|int|entire_df|Second floor square feet|  
|low_qual_fin_sf|int|entire_df|Low quality finished square feet|  
|gr_liv_area|int|entire_df|Above grade (ground)living area square feet| 
|bsmt_full_bath|float|entire_df|Basement full bathrooms|
|bsmt_half_bath|float|entire_df|Basement half bathrooms|
|full_bath|int|entire_df|Full bathrooms above grade|
|half_bath|int|entire_df|Half baths above grade | 
|bedroom_abvgr|int|entire_df|Bedrooms above grade|  
|kitchen_abvgr|int|entire_df|Kitchens above grade|  
|kitchen_qual|object|entire_df|Kitchen quality |
|totrms_abvgrd|int|entire_df|Total rooms above grade | 
|functional|object|entire_df|Home functionality |
|fireplaces|int|entire_df|Number of fireplaces | 
|fireplace_qu|object|entire_df|Fireplace quality |
|garage_type|object|entire_df|Garage location |
|garage_yr_blt|float|entire_df|Year garage was built|
|garage_finish|object|entire_df|Interior finish of the garage| 
|garage_qual|object|entire_df|Garage quality |
|garage_cond|object|entire_df|Garage condition |
|paved_drive|object|entire_df|Paved driveway| 
|wood_deck_sf|int|entire_df|Wood deck area in square feet|  
|open_porch_sf|int|entire_df|Open porch area in square feet|  
|enclosed_porch|int|entire_df| Enclosed porch area in square feet| 
|3ssn_porch|int|entire_df|Three season porch area in square feet|
|screen_porch|int|entire_df|Screen porch area in square feet| 
|pool_area|int|entire_df|Pool area in square feet| 
|misc_val|int|entire_df|Miscellaneous feature not covered in other categories|  
|mo_sold|int|entire_df|Month Sold (MM)|
|yr_sold|int|entire_df|Year Sold (YYYY)|
|sale_type|object|entire_df|Type of sale| 
|saleprice|int|entire_df|Sale price|
|car_area|float|entire_df|Interaction term of Garage Car and Garage Area|

### Conclusion/Recommendations
Based on the findings, we can draw several conclusions: <br>

1) Several important determining features of cost of houses:
- There are several features that have displayed a strong correlation and influence on our predictor variable and the top 5 features to look out for are `gr_liv_area`, `overall_qual`, `total_bsmt_sf`,`bsmtfin_sf_1` and `year_built`
- Higher cost of houses associated with larger houses
- Extended to both categorical(`kitchen_qual` and `neighborhood`) and numerical features
2) Versatility of model: Provision of accurate **quantitative increment** in housing prices for every unit change in the variables included.
- The use of a regularized linear regression model, Lasso, to weigh and highlight the impact of several important features on the cost of houses. 
3) Inclusion of most features results in a model with low bias and high variance with regards to houses in Ames,Iowa
- Strongly generalizable to houses in Ames, Iowa

Limitations of model: <br>

1) Biasness of features collected:
- Inclusion of subjective features such as `overall_qual` and `kitchenqual` reduces the reproducibility of predictions obtained
2) Exclusion of current housing challenges:
- Influx of university students and employees increases the population size over the years, leading to a lack of space and reducetion in the number of houses built and thus the trend that has been seen in the past few years might not be relevant to the future if such considerations are not taken into account.