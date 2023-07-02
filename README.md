# Doceree-Hackathon
This is our solution for the Doceree-Hackthon.

Identifying Healthcare Professionals (HCP) and their specialization - 
The ad server logs contain valuable information such as browser details, IP addresses, geographic locations, search patterns, site urls, and other relevant data. The objective of the hackathon is to build a robust model that can accurately predict whether a user belongs to the HCP category and its specialization id/taxonomy.

Input: Ad server logs containing information on user behavior and other features
The input contains the following type of data:
HCP has been identified but the taxonomy/specialization is not identified - IS_HCP is true but taxonomy is not populated.
Both HCP and taxonomy/specialization are identified - IS_HCP is true and taxonomy is also populated.
The remaining rows pertain to data where there is no information about HCP. It may correspond to HCP or may not.

Output: Given a userid(userplatformuid) and ad server log, classify if the user is an HCP and its specialization (taxonomy). 

# Solution proposed and description
The idea and approach that our team decided to pursue with so as to work on the given problem statement was to develop a RandomForest ML model which would first classify if the professional is a HCP or not & then identify the taxonomy.

The solution includes the usage of various python libraries (sklearn, numpy, pandas etc.) and other techniques such as identification of the required attributes, label encoding & decoding, model training and clustering. 

The solution was implemented in such a way that it is easily understandable & works well on the given dataset while giving higher accuracy and performance.

# Approach
At first, both train and test dataset were merged in order to label encode all the values. The primary step of the process was data filtering and preprocessing. After removing the null values and unwanted field, the process heads towards label encoding which involves giving a unique number to every value of each attribute irrespective of its data-type. 
The encoded data-frame is again splitted into train and test data-frames. Random Forest Classifier has been applied to the train encoded dataset with respect to IS_HCP attribute of the test dataset and the result of it is stored in a separate data-frame. This gives the predictions for whether it is a Health Care Person or not.
Now, to predict the Taxonomy of the Health Care person we got from the previous result, we filtered the rows for which IS_HCP equals to 1.
The entries having values equal to 1 are filtered from the model1 prediction dataset and used as test dataset for predicting the Taxonomy of those who are Health Care Persons.
Now, Random Forest Classifier has been applied to the filtered dataset from encoded training dataset and filtered predicted dataset of IS_HCP. 
The final result data-frame contains the Taxonomies of those who are Health Care Persons.




