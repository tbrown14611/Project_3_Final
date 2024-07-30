# Project Team 6 - Traffic Crashes Classification and Prediction  
# Project 3 

## Overview

Traffic Accidents, is the selected focus for our project.  Specifically, we're focused on the accidents that occur in the state of Colorado.  Our dataset is one from Kaggle, the "US-Accidents: A Countrywide Traffic Accident Dataset".  https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents
Our dataset has 7.7 million records, covering 49 states, omitting just Hawaii.  However, analysis reveals that there isn't any data for Alaska either. This dataset was initially published in 2016 by Sobhan Moosavi, a Data Scientist at Lyft, Inc.  Sobhan's CV can be obtained at https://smoosavi.org/cv/ .  The dataset contains crash data starting from February, 2016 through March, 2023. The data is generated continously via multiple APIs that provide streaming traffic event data from serveral enties such as US and state department of transportation, law enforcement agencies, traffic cameras, and traffic sensors within road networks.  https://smoosavi.org/datasets/us_accidents .


## Acknowledgements 

The following two papers are being cited as a condition for our academic use of this dataset. 

    Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, and Rajiv Ramnath. “A Countrywide Traffic Accident Dataset.”, arXiv preprint arXiv:1906.05409 (2019).

    Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, Radu Teodorescu, and Rajiv Ramnath. “Accident Risk Prediction based on Heterogeneous Sparse Data: New Dataset and Insights.” In proceedings of the 27th ACM SIGSPATIAL International Conference on Advances in Geographic Information Systems, ACM, 2019.

The dataset is distributed under the following license:  Creative Commons Attribution-Noncommercial-ShareAlike license (CC BY-NC-SA 4.0).


### Focused State of Analysis - Colorado

As mention earlier, our dataset encompases the continental United States containing 7.7 million records.  We have selected a subgroup for our analysis, focusing only on the data representing The State of Colorado.  Although the data comprising just Colorado is reduce down to 90885 records, we feel this still should provide a good amount of data to perform our goals, while limiting the amount of data to a manageable size. 

### Traffic Analysis by Street and County

After cleaning the street data, which had only 158 null or missing values, 90,727 records remained to proceed with. One column, severity, provided the only resemblence of accidents that occurred. The severity rating of 1 through 4, rated only the delay associated with any given accident, that impacted traffic conditions at the time.  Severity 1 was given to accidents that impacted traffic flow the least amount, where 2, 3, and 4 we're given to accidents with greater levels of traffic delay.  Severity 4 was considered the worst impact to traffic flow.  

In this analysis, tenserflow was the model used to attempt accident prediction, where severity was assigned the model's X value.  Street name and county name were used to identify where the accident occurred and both were the tenserflow 'y' values (y_street and y_county).  Initially all streets in Colorado were considered for analysis, however, after finding out that the number of unique Colorado streets contained in the data that had accidents was 4,744, it was decided to reduce the analysis down to the streets that fell in the top5 to top30 with the most accidents. This reduced the volume of data accordingly to 51.8%, 47.6%, 44%, 40% and 31.8% for the top30, top20, top15, top10, and top5 respectively. These groups became the groups of primary focus. Each group was iteratively processed by first encoding the streets through onehot encoding, producing a column for each street in the group, and splitting the data into test and train datasets that were fitted to the nueron network model.  The accuracy results for each group of streets is listed below, all extremely low.

#### Top 5 to 30 streets by # of accidents - accuracy score

Top30-  .008
Top20-  .185
Top15-  .186
Top10-  .127
Top5 -  .306

Given at the time, the team had one week left to improve the above accuracy, the sentiment was beginning to lean towards focusing on write-up and presentation rather than spend more time on model optimization.  Nonetheless, one more analysis was pursued.  This involved applying a p-value test to the top 30 group with the results as shown below.  

#### Top 30 streets by # of accidents and pvalue correlating severity and street

The result showed several streets (13) to investigate further, focusing only on those with a pvalue less than .05% and greater than 0.

Street_ US Highway 50           0.039263
Street_I-25 S                   0.031770
Street_ US Highway 285          0.023408
Street_US-85 S                  0.020724
Street_I-270 W                  0.019563
Street_US-6 W                   0.012349
Street_I-70 E                   0.008659
Street_I-76 E                   0.008196
Street_I-70 W                   0.007905
Street_I-225 N                  0.002867
Street_I-225 S                  0.001835
Street_I-76 W                   0.001507
Street_US-36 W                  0.000317

To analyze each of these individually through the same model, the model unit# for street output was changed to 1 from multiple values earlier, and the activation to "sigmoid" from "softmax".  Likewise, the loss for street output was changed to binary crossenthropy from catagorical.    

The following results were obtained and listed by street in the descending pvalue shown above.

Run statistics for street prediction with a street p-value less than .05
                                                                                                                   Positive %
Street-  US Highway 50   Accuracy- 0.9915816187858582   p-Value - 0.039263   Value Counts 0.0=46678   1.0= 362         .007   
Street-  I-25 S          Accuracy- 0.8414965867996216   p-Value - 0.031770   Value Counts 0.0=39332   1.0=7708         .160
Street-  US Highway 285  Accuracy- 0.9923469424247742   p-Value - 0.023408   Value Counts 0.0=46625   1.0= 415         .008
Street-  US-85 S         Accuracy- 0.989625871181488    p-Value - 0.020724   Value Counts 0.0=46601   1.0= 439         .009
Street-  I-270 W         Accuracy- 0.9897959232330322   p-Value - 0.019563   Value Counts 0.0=46536   1.0= 504         .010
Street-  US-6 W          Accuracy- 0.9717687368392944   p-Value - 0.012349   Value Counts 0.0=45657   1.0=1383         .029
Street-  I-70 E          Accuracy- 0.8852040767669678   p-Value - 0.008659   Value Counts 0.0=41829   1.0=5211         .011
Street-  I-76 E               Not produced                        0.008196   
Street-  I-70 W          Accuracy- 0.8955782055854797   p-Value - 0.007905   Value Counts 0.0=42061   1.0=4979         .105
Street-  I-225 N         Accuracy- 0.9786564707756042   p-Value - 0.002867   Value Counts 0.0=46023   1.0=1017         .022
Street-  I-225 S         Accuracy- 0.9795918464660645   p-Value - 0.001835   Value Counts 0.0=46058   1.0= 982         .020
Street-  I-76 W          Accuracy- 0.9854592084884644   p-Value - 0.001507   Value Counts 0.0=46341   1.0= 669         .014
Street-  US-36 W         Accuracy- 0.9915816187858582   p-Value - 0.000317   Value Counts 0.0=46637   1.0= 403         .008

Nearly in all cases, the accuracy improved from high 80's to high 90's.  This seemed to good and over-fitting became suspect.  
Therefore, value counts were analyzed for the O and 1 classification out of the one-hot encoding.  This showed that the number of crashes (encoding=1) had a very low positive value when compared to the encoding=0, or no crash for the given severity and county.  This indicates that the data is 
unbalanced.  

## Summary

Given that the data is unbalanced, techniques could be performed to potentially improve the imbalance, or to changed biased data to be less so.  These are removing samples from the majority class, which in this case is the "negative crash" encoding=0.  Another option would be to add samples to the positive encoding=1. Yet even another option suggested in course work is to SMOLT the data. SMOLT, or Synthetic Minority Oversampling Techique, is similar to the second option listed where samples are added (actually duplicated) in the minority class.  

Prior to changing any of the data, one more option needs to be explored.  This involves using the Longitude and Latitude information contained within the crash data.  This in turn may identify hot spots for crashes which would be more in line with our goal and with more time, be pursued. 





