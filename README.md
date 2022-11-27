# Sales Model Feature Selection
### Code to select 30 features from given number of features

### Key assumptions made
  - There can be any number of features according to the script.
  - Name of these features must not be changed. These data must be collected under the same name. This is because those features are dropped by the name of the feature.
      - 'ID', 'Company_ID', 'Company_Name', 'Firstname', 'Surname', 'Address','Postcode', 'Phone'
  - For other features, feature name is not considered, any name can be chosen.

### Procedure
  - First the .csv file is read.
  - Duplicates are checked and if present removed.
  - Missing values are checked and dropped or filled under few criterias.
      - Frist distinguish the columns that have missing values.
      - If they are continuous varaibles, missing values are filled with median values.
      - If they categorical, they are dropped since predicting categorical variables may attain with false results. For this date-time values are considered too.
  - Then the different types of features are categorized. Mainly, here it has object, datetime and continous data types.
      - First objects data are seperated.
      - It comes with datetime data too since they are read as strings.
      - Seperate datetime, and object with regex.
  - Dealing with categorical variables
      - Only one type of categorical variables is identified.

      - ![Screenshot (381)](https://user-images.githubusercontent.com/77132441/204116512-2c9afe45-85ab-4354-b797-2245bbb1d918.png)

      - It has more than 200 unique features. Onehotencoding them is not appropriate.
      - Feature Engineering to extract only the continent values.
      - And based on the percentage of total data, continent are categorised. If the data ratio is low, it is put to Other category. This is to mainly reduce the dimension of the data. Even with low data points, if all the continent data is used, there will be 6 more features but with this, number of features are reduced.
      - ![image](https://user-images.githubusercontent.com/77132441/204116738-d8144024-7ac6-462c-a6f1-f46f847d1e21.png)
      - The onehotencoder is used to encode the data and first column is dropped since dummy variables are created.

  - Dealing with date-time data
      - To take decisions on date-time features, information about the features is low.
      - Therefore user can go with datetime data or without datetime data.
      - But assumptions can be made if moving forward with date-time data.
          - Since we are dealing with sales prediction model, sales depends on seasonal patterns depends on the domain which the sales are being made.
          - Therefore date-time data may have an effect here.
          - Since it is evaluated every 2 weeks, yearly seasonality is not considerable.
          - Monthly and daily seasonality can occur.
          - Script mainly works with monthly seasonality(Ex: April and December sales can be more compared to other months)
          - But there are 20 features of date-time data.
          - All the features cannot be selected since significances of the variables with dependent variables are unknown.
          - Only one variable cannot be used, it can tends to feature biasness.
          - Cannot go with one generalized feature, for each record months, hour, minutes are totally different.
          - Therefore random feature from datetime data can be selected for every 2 weeks.
          - If the dependent variable is available, significances can be measured and can be selected or dropped based on the significance level.
          
  - Dealing with continuous data
       - Lot of features are from continuous data.
       - Mulitcollinearity which is having high correlation between independent varibales, can be an issue for sale predictions.
       - Therefore, multicollinearity is removed by dropping columns which have high correlations.
       - After that, as an alternative method, Principal Component analysis was done. But from 179 features, at above 100 features are needed to cover up the 80% variance.
       ![image](https://user-images.githubusercontent.com/77132441/204117272-134236b9-b5c8-43ce-a921-0d070c29f563.png)

       - Therefore, rather than going with PCA, variance ratio is considered to select the continuous variables.
       - First required variables with highest variance is selected for the final model since higher variance features are good for model building.
       
       
 ### Notebook Link
 
  - https://colab.research.google.com/drive/1j46SX1sP8jJB_pxFDPsswWoOqLkpP2Ur?usp=sharing




