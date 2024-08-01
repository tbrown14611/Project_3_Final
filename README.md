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

PyTorch Test Run produced the following results based on the following code:

#GPU 
b = torch.ones(4000,4000).cuda() # Create matrix on GPU memory
start_time = timer() 
for _ in range(1000): 
    b += b 
elapsed_time = timer() - start_time 

print('GPU time = ',elapsed_time)

#CPU
a = torch.ones(4000,4000) # Create matrix on CPU memory
start_time = timer()
for _ in range(1000):
    a += a
elapsed_time = timer() - start_time

Results:
    GPU time =  0.007673599990084767
    CPU time =  2.526412000064738

## Project Overview 

Traffic Accidents, is the selected focus for our project.  Specifically, we're focused on the accidents that occur in the state of Colorado.  Our dataset is one from Kaggle, the "US-Accidents: A Countrywide Traffic Accident Dataset".  [Data Source for Accidents](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents).
Our dataset has 7.7 million records, covering 49 states, omitting just Hawaii.  However, analysis reveals that there isn't any data for Alaska either. This dataset was initially published in 2016 by Sobhan Moosavi, a Data Scientist at Lyft, Inc.  Sobhan's CV can be obtained at [Dictionary](https://smoosavi.org/datasets/us_accidents).  The dataset contains crash data starting from February, 2016 through March, 2023. The data is generated continously via multiple APIs that provide streaming traffic event data from serveral enties such as US and state department of transportation, law enforcement agencies, traffic cameras, and traffic sensors within road networks. [Accidents Data](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents). Shown below is a graph of the data by state prior to our extraction of the state of Colorado data.


![US_Accidents_Feb2016_Mar2023](/Resources/images/CrashesByState.png)

## Project Ideation:  
Traffic Safety, is the selected focus for our project.  Specifically, we're focused on the accidents that occur in the state of Colorado.  
Using traffic data captured by various entities, including the US and state departments of transportation, law enforcement agencies, traffic cameras, and traffic sensors within the road networks, provided by Kaggle. Our Goals for this project are:

     o  Determine the best model configurations to predict crashes.
        o Determine the best model to analyze all 90,885 Colorado crashes that were collected from February 2016 to March 2023.
        o Analyze all Colorado traffic crash data, and record accuracy calculations for Weather, County and Street.
     
     o  Identify the different classifications of crashes and potential impact within each classification. 

Ultimately, using our model(s) here,  CODOT could identify road improvement prospects for improved safety


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
               Contains Colorado only
               Update County to numeric
               Calculate P values for streets
               Encode top 30 streets by accidents

- Inconsistent and Duplicative
              Remove duplicates from Weather Conditions


### Traffic Analysis by Street and County 

In this analysis, tenserflow was the model used to attempt accident prediction, where severity was assigned the model's X value.  Street name and county name were used to identify where the accident occurred and both were the tenserflow 'y' values (y_street and y_county).  Initially all streets in Colorado were considered for analysis, however, after finding out that the number of unique Colorado streets contained in the data that had accidents was 4,744, it was decided to reduce the analysis down to the streets that fell in the top5 to top30 with the most accidents. This reduced the volume of data accordingly to 51.8%, 47.6%, 44%, 40% and 31.8% for the top30, top20, top15, top10, and top5 respectively. These groups became the groups of primary focus. Each group was iteratively processed by first encoding the streets through onehot encoding, producing a column for each street in the group, and splitting the data into test and train datasets that were fitted to the nueron network model.  The accuracy results for each group of streets is listed below, all extremely low.

#### Top 5 to 30 streets by # of accidents - accuracy score

![Top_Street_Groups](/Resources/images/Top_Street_Groups.png)

Given at the time, the team had one week left to improve the above accuracy, the sentiment was beginning to lean towards focusing on write-up and presentation rather than spend more time on model optimization.  Nonetheless, one more analysis was pursued.  This involved applying a p-value test to the top 30 group with the results as shown below.  

#### Top 30 streets by # of accidents and pvalue correlating severity and street

The result showed several streets (13) to investigate further, focusing only on those with a pvalue less than .05% and greater than 0.

![The best 13 street amoung top30 with valid pvalues ](/Resources/images/Best_pvalues_ofTop30.png)



![Top13 with pvalues less than .05 ](/Resources/images/Pvalues_Less.05_Top30.png)


To analyze each of these individually through the same model, the model unit# for street output was changed to 1 from multiple values earlier, and the activation to "sigmoid" from "softmax".  Likewise, the loss for street output was changed to binary crossenthropy from catagorical.    

Nearly in all cases, the accuracy improved from low teens to low thirties up to low 80's to high 90's.  This seemed too good and over-fitting became suspect.  
Therefore, value counts were analyzed for the 0 and 1 classification out of the one-hot encoding.  This showed that the number of crashes (encoding=1) had a very low positive value when compared to the encoding=0, or no crash for the given severity and county.  This indicates that the data is unbalanced.  The plot below shows the accuracy for each of the 13 streets and their corresponding unbalanced negative value.  It is nearly a perfect overfit comparison between the two.

![Top13 with valid pvalues](/Resources/images/Street_Accuracy_Overfit.png)

## Street Analysis Summary

Given that the data is unbalanced, techniques could be performed to potentially improve the imbalance, or to changed biased data to be less so.  These are removing samples from the majority class, which in this case is the "negative crash" encoding=0.  Another option would be to add samples to the positive encoding=1. Yet even another option suggested in course work is to SMOLT the data. SMOLT, or Synthetic Minority Oversampling Techique, is similar to the second option listed where samples are added (actually duplicated) in the minority class.  

Prior to changing any of the data, one more option needs to be explored.  This involves using the Longitude and Latitude information contained within the crash data.  This in turn may identify hot spots for crashes which would be more in line with our goal and with more time, be pursued and accuracy improved without being overfit. 

## Result/Conclusion
Our accuracy predictions:

- Weather Accuracy: 0.35014522075653076
- County Accuracy: 0.14039257168769836
- Initial Top30 Street Accuracy: 0.11454081535339355


## Future Considerations

May be able to leverage other data in the Accidents table (Latitude and Longitude) to help improve accuracy. 
Additional data sets could be used to give a complete picture of all traffic (accidents or not) to improve model accuracy.
