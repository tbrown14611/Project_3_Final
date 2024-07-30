# Project_3_Final - Ava

We focused on three parameters from the dataset: ‘***Weather***,’ ‘***County***,' and ‘***Street***. '

We cleaned the data, starting with:

 
* Dropping unnecessary columns,
* Dropping null values and duplicates,
* Combining similar parameters for better accuracy,
* Convert County names to County Codes

We primarily used LabelEncoder and OneHotEncoder to encode data.

For instance,
***OneHotEncoder*** used for:

        Weather_Condition

***LabelEncoder*** used for:

        ID

For the street, we retrieved the top 30 stats with accidents and ran the correlation relationship for the top 30 streets.
