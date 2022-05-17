# Project 2 - Ames Housing Data and Kaggle Challenge


### Problem Statement

As a team at a small real estate company in Ames Iowa we are working to: 
    1. understand what the primary factors are in determining the sale price of a home;
    2. generate estimates for appropriate sale pricing of upcoming homes.

### Data Dictionary
#### Kaggle Model Features
|Feature|Type|Dataset|Description|
|---|---|---|---|
|**Overall Qual Year Built_mod**|float|02_Processing_Kaggle_TopScore|Home Quality Rating multiplied by Year Built with transforms applied|
|**Exter Qual_TA TotRms AbvGrd**|float|02_Processing_Kaggle_TopScore|Total Rooms Above Ground filtered by Exterior Quality Grade (Grade: Average)|
|**Garage Area Year Built**|float|02_Processing_Kaggle_TopScore|Garage Area multiplied by the Year Built|
|**Garage Cars 1st Flr SF**|float|02_Processing_Kaggle_TopScore|Number of Cars the Garage is built for multiplied by First Floor Area|
|**Garage Area^2**|float|02_Processing_Kaggle_TopScore|Garage Area multiplied into itself|
|**Overall Qual Garage Area**|float|02_Processing_Kaggle_TopScore|Home Quality Rating multiplied by Garage Area|
|**Garage Area Foundation_PConc**|float|02_Processing_Kaggle_TopScore|Garage Area filtered by Poured Concrete Foundation|
|**Garage Area Total Bsmt SF**|float|02_Processing_Kaggle_TopScore|Garage Area multiplied by Total Basement Area|
|**Kitchen Qual_TA TotRms AbvGrd**|float|02_Processing_Kaggle_TopScore|Total Rooms Above Ground filtered by Kitchen Quality Grade (Grade: Average)|
|**Overall Qual 1st Flr SF**|float|02_Processing_Kaggle_TopScore|Home Quality Rating multiplied by First Floor Area|
|**Garage Area Mas Vnr Area**|float|02_Processing_Kaggle_TopScore|Garage Area multiplied by Masonry Veneer Area|
|**Overall Qual Exter Qual_TA**|float|02_Processing_Kaggle_TopScore|Home Quality Rating filtered by External Quality Grade (Grade: Average)|
|**Full Bath^2**|float|02_Processing_Kaggle_TopScore|Number of Full Baths multiplied into itself|
|**Year Built Foundation_PConc**|float|02_Processing_Kaggle_TopScore|Year Built filtered by Poured Concrete Foundation|
|**Mas Vnr Area**|float|02_Processing_Kaggle_TopScore|Masonry Veneer Area|
|**Garage Area 1st Flr SF**|float|02_Processing_Kaggle_TopScore|Garage Area multiplied by First Floor Area|
|**Total Bsmt SF Mas Vnr Area**|float|02_Processing_Kaggle_TopScore|Basement Area multiplied by Masonry Veneer Area|
|**Overall Qual TotRms AbvGrd**|float|02_Processing_Kaggle_TopScore|Home Quality Rating multiplied by the Total Number of Rooms Above Ground|
|**Gr Liv Area Garage Cars**|float|02_Processing_Kaggle_TopScore|Above Ground Living Area multiplied by Number of Cars the Garage is built for|
|**Gr Liv Area^2**|float|02_Processing_Kaggle_TopScore|Above Ground Living Area multiplied into itself|
|**Exter Qual_TA**|float|02_Processing_Kaggle_TopScore|Filtering by Exterior Quality Grade (Grade: Average)|
|**Garage Cars Year Built**|float|02_Processing_Kaggle_TopScore|Number of Cars the Garage was built for multiplied by the Year the Home was Built|
|**Mas Vnr Area TotRms AbvGrd**|float|02_Processing_Kaggle_TopScore|Masonry Veneer Area multiplied by the Total Number of Rooms Above Ground|
|**Gr Liv Area Mas Vnr Area**|float|02_Processing_Kaggle_TopScore|Above Ground Living Area multiplied by Masonry Veneer Area|
|**Total Bsmt SF 1st Flr SF**|float|02_Processing_Kaggle_TopScore|Total Basement Area multiplied by First Floor Area|
|**Full Bath**|float|02_Processing_Kaggle_TopScore|Number of Full Baths|
|**Gr Liv Area Year Built**|float|02_Processing_Kaggle_TopScore|Above Ground Living Area multiplied by Year Built|
|**Overall Qual Gr Liv Area**|float|02_Processing_Kaggle_TopScore|Home Quality Rating multiplied by Total Living Area|
|**Overall Qual Full Bath**|float|02_Processing_Kaggle_TopScore|Home Quality Rating multiplied by the Number of Full Baths|
|**Gr Liv Area Full Bath**|float|02_Processing_Kaggle_TopScore|Above Ground Living Area multiplied by the number of Full Baths|
|**Overall Qual Total Bsmt SF**|float|02_Processing_Kaggle_TopScore|Home Quality Rating multiplied by Total Basement Area|
|**Overall Qual Year Built**|float|02_Processing_Kaggle_TopScore|Home Quality Rating multiplied by Year Built|
|**Gr Liv Area TotRms AbvGrd**|float|02_Processing_Kaggle_TopScore|Above Ground Living Area multiplied by the Total Number of Rooms Above Ground|
|**GR Rooms by GR Liv Area**|float|02_Processing_SimplifiedApproach|Number of Above Ground Rooms relative to Above Ground Living Area|
|**Year Remod/Add**|float|02_Processing_SimplifiedApproach|Year of Remodel or Addition|
|**Garage Cars**|float|02_Processing_SimplifiedApproach|Number of Cars the Garage was built for|
|**Year Built**|float|02_Processing_SimplifiedApproach|Year the Home was Built|
|**Gr Liv Area**|float|02_Processing_SimplifiedApproach|Above Ground Living Area|
|**Overall Qual**|float|02_Processing_SimplifiedApproach|Home Quality Rating|

### Summary of Analysis

#### Data

Information on home sales and home qualities for Ames Iowa was retrieved from the Kaggle 'Ames Housing Data' dataset.

#### Methodology

##### Cleaning
1. Null values were identified and variable datatypes were identified and corrected as necessary. 
2. Variables were separated into numerical and non-numerical datatype groups.
3. Non-numerical variables were processed to determine category correlation relative to the target variable
4. Highest correlated variables were identified and downselected for inclusion in cleaned dataset
5. Kaggle competition data was processed to match variables in training dataset
6. Filtered training and Kaggle datasets were output into unique .csv files

##### Processing
1. Filtered training data was pulled in, and polynomial features were created for all variables excepting the target variable
2. Polyfit training data was fed into LASSO for feature selection
3. Top features by absolute value of coefficients were selected according to LASSO results
4. Linear model was created with top features, and evaluated
5. Outliers were identified, but causation remained hidden
6. High Variance Inflation Factor (VIF) features were identified and addressed
7.  Transformations were applied to specific features, including the target, to try to produce a more linear relationship with the target, and models refit accordingly
8.  Kaggle data was processed according to final training data form, and predictions were made using the linear model on the Kaggle data

Specifically we were seeking to identify: 
    - What are the primary factors that determine and enable accurate prediction of home sales prices in Ames, Iowa
	- What model provides us with our best estimate of home values in Ames, and what is its relative performance to a baseline.

### Conclusions & Recommendations

#### Conclusions:
While the model developed is a significant improvement over baseline, it underperforms its peers in the market, and is difficult to ascertain exact impact of features due to coefficients being obscured through LASSO regularization. 

The model does point towards recurring features that appear to have outsized effect, namely: Overall Quality Rating of the Home, Above Ground Living Area, Year Built, Number Car Garage, Year of Remodel, and finally, an inverse relationship with Number of Rooms compared with Above Ground Living Area. This is verified using a substantially simplified model, that while underperforming its more complex cousin, is far more legible and also outperforms the baseline significantly.

#### Recommendations:
1. As a starting position, we can advise clients who are selling their homes that the overall appearance of quality is of top importance in fetching a high price, and that recent remodels are also valuable. Additionally, when performing a remodel, it is advised to prioritize the size of rooms in the house over the total number of rooms. 

2. Investigate further the effect of outliers on the model, and try to determine if there are high leverage features that have not been identified.