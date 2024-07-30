# Project_3_Final

## Project 3 Instructions / Directions

- Instructions for [project 3](https://bootcampspot.instructure.com/courses/5432/pages/23-final-project-overview?module_item_id=1201422) provided by the course instructors.

For the Final Project, you will work with your group to collaboratively solve or analyze a problem using advanced ML methodologies. In your solution, you will incorporate transformer models, natural language processing (NLP) techniques, and other tools acquired throughout the course, in addition to at least one new technology that we haven’t covered together.

Here are the specific requirements:

- Identify a problem worth solving or analyzing.
- Find a dataset or datasets that are sufficiently large enough to effectively train a ML model or neural network with a high degree of accuracy to ensure that your results are reliable.
- Evaluate the trained model(s) using testing data. Include any calculations, metrics, or visualizations needed to evaluate the performance.
- You must use at least two of the following:
- scikit-learn (chosen)
- Keras (chosen)
- TensorFlow (chosen)
- Hugging Face
- spaCy or Natural Language Toolkit (NLTK)
- LangChain
- OpenAI
 Our Team chose to use the first thee listed above.

You must use one additional library or technology NOT covered in class.  We chose Windows 11 PyTorch running in Visual Studio with the following steps:
- Install and configure PyTorch on Windows 11 (follow instructions provided by PyTorch).
    - This will enable GUP use by Python.
- Update GPU in Visual Studio:
    - This will enable GPU graphics use wihin Visual Studio
    - Select setting from File-->Preferences-->Settings
    - Search for GPU
    - Set GPU Acceleration = on
    - Check Custom Glyphs
    - Check Enable Images

## Project Overview 

Traffic Accidents, is the selected focus for our project.  Specifically, we're focused on the accidents that occur in the state of Colorado.  Our dataset is one from Kaggle, the "US-Accidents: A Countrywide Traffic Accident Dataset".  [Data Source for Accidents](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents).
Our dataset has 7.7 million records, covering 49 states, omitting just Hawaii.  However, analysis reveals that there isn't any data for Alaska either. This dataset was initially published in 2016 by Sobhan Moosavi, a Data Scientist at Lyft, Inc.  Sobhan's CV can be obtained at [Dictionary](https://smoosavi.org/datasets/us_accidents).  The dataset contains crash data starting from February, 2016 through March, 2023. The data is generated continously via multiple APIs that provide streaming traffic event data from serveral enties such as US and state department of transportation, law enforcement agencies, traffic cameras, and traffic sensors within road networks. [Accidents Data](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents). 

## Project Ideation:  
Traffic Safety, is the selected focus for our project.  Specifically, we're focused on the accidents that occur in the state of Colorado.  
Using traffic data captured by various entities, including the US and state departments of transportation, law enforcement agencies, traffic cameras, and traffic sensors within the road networks, provided by Kaggle. Our Goals for this project are:

     o  Determine the best model configurations to predict crashes.
     o  Identify the different classifications of crashes and potential impact within each classification. 

Ultimately, using our model(s) here,  CODOT could identify road improvement prospects for improved safety

## Data Cleanup (TBD - AVA)


Determine the best model configurations to predict crashes and identify the different classifications of crashes and potentially the impact within each. 

- Project ideation - Complete 7/22

- Data fetching - Complete 7/22

- Data exploration - Complete 7/26

- Data transformation - Complete 7/26

- Data analysis - Complete 7/27

- Data cleaning and preprocessing - Complete 7/27

- Testing ML models - Complete 7/27 

- Integrate AI tools into the project for deployment - Complete 7/27

- Creating documentation - Complete 7/29

- Creating the presentation - Complete 7/30


## Questions, Analysis and Summary
### Goal 

-Goals: 
 - Analyze all 90,885 Colorado crashes that were collected from February 2016 to March 2023.
    - Our analysis included all Colorado traffic crash data, our accuracy predictions were based on Weather, County and Street.
 - Identify the different classifications of crashes and potential impact within each classification.
    - The data dictionary for our data set can be found at [Dictionary](https://smoosavi.org/datasets/us_accidents). Crashes are classified by the "severity" column shows the severity of the accident, a number between 1 and 4, where 1 indicates the least impact on traffic (i.e., short delay as a result of the accident) and 4 indicates a significant impact on traffic (i.e., long delay). Our analysis used "severity" to identify a crash

## Analysis Approach

The analysis was broken into multiple steps with a Jupyter notebook for each step.
- Step1_build_base_data.ipynb
- Step2_analyze_weather_and_county_data
- Step3_analyze_street_and_county_data

    Step duration is calculated (see Duration in each step detail below)

### Jupyter notebook: step1_build_base_data.ipynb Duration: 0:00:02.046045

- Set start time
- Import the data
- Extract relevant columns
- Create DataFrame that containes only Colorado
- Update CO_crashes_df with numeric county code
- Update Weather_Conditions and combine duplicates
- Write data to Resources/result_files/step1_build_base_data.csv file
- Calculate Duration

### Jupyter notebook: step2_analyze_weather_and_county_data: Duration: 0:00:39.391312

- Set start time
- Import system
- Setup PyTorch Environment and test it
- Load the CSV file containing Colorado crash data for analysis
- Drop Street from the crash data (not used)
- Display the first five rows of the Crashes DataFrame
- Preprocess "Weather_Condition" column (one-hot encoding)
- Tain - Test - Split Calculations
- Create a StandardScaler and scale X values
- Create the shared layers of the model
- Create branchs for Weather and County prediction
- Create the Dense/Karas/Tensorflow model
- Fit the model
- Evaluate the model with the testing data
- Print the accuracy
- Calculate Duration

### Jupyter notebook: step3_analyze_street_and_county_data:

- Set start time
- Import the data
- What top 30 streets have the most accidents?
- Store the street names of the top 30 with accidents in a list.
- get top30 streets with accidents in CO and store in a dataframe called top30_df
- extract relevant columns and display 'em
- reset the index of relevant_df
- find and display severity counts (accidents by severity)
- find and display county counts (accidents by county)
- Update CO_crashes_df with numeric county code
- find and display severity counts (accidents by severity)
- Preprocess Street Data - Encode top 30 streets by accidents
- display column, null, and Dtype info for encoded street data
- set street to analyze with pvalue <.05
- find and display encoded counts (0 = row without an accident; 1 = row with accident)
- define X and create train - test - split
- Create the shared layers of the model
- Branch for street prediction
- Create the model
- Fit the model
- Evaluate the model with the testing data
- Print the accuracy
- Calculate Duration

## Data Sources
- Clean and Consistent
- Inconsistent and Duplicative
- Standardization Approach

TBD


## Result/Conclusion
Our accuracy predictions:

- Weather Accuracy: 0.35014522075653076
- County Accuracy: 0.14039257168769836
- Street Accuracy: 0.9916666746139526


## Future Considerations
