# Sales Model Feature Selection
### Code to select 30 features from given number of features

### Key assumptions made
  - There can be any number of features according to the script
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

![Screenshot (381)](https://user-images.githubusercontent.com/77132441/204116512-2c9afe45-85ab-4354-b797-2245bbb1d918.png)

      - It has more than 200 unique features. Onehotencoding them is not appropriate.
      - Feature Engineering to extract only the continent values.
      - And based on the percentage of total data, continent are categorised. If the data ratio is low, it is put to Other category. This is to mainly reduce the dimension of the data. Even with low data points, if all the continent data is used, there will be 6 more features but with this, number of features are reduced.


