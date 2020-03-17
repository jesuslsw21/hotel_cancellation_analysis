# Hotel Cancellation Analysis



Abstract 

We are a data science consultancy that has been hired by a large hotel chain to investigate viable methods of mitigating the impact of short-notice customer cancellations. The approach taken in this analysis was to look at what characteristics of an individual may indicate that they are of a high probability to cancel. If an individual is deemed likely to cancel, they are charged a higher deposit at the point of purchase. This means that some of the lost revenue due to cancellation is recovered, thus reducing the overall cost to our client. We take ethics very seriously so for obvious reasons race, religion, gender and biological sex have not been considered. All customers will pay the same overall price (if they are purchasing the same product), it is only the initial deposit (as a % of the total price) that will change on a customer to customer basis.



Context

This dataset describes hotel(city) demand data, with 31 variables describing the 79,330 observations( observation represents a hotel booking. )
Also, datasets comprehend bookings due to arrive between the 1st of July of 2015 and the 31st of August 2017, including bookings that effectively arrived and bookings that were canceled. 

The dataset now made available were collected aiming at the development of prediction models to classify a hotel booking׳s likelihood to be canceled. Nevertheless, due to the characteristics of the variables included in thIs dataset, their use goes beyond this cancellation prediction problem.

we chose this dataset, because of the following reasons below:

1) This could be a good excerise to tackle the real-world dataset.
2) Evenly distributed ( roughly half of the data is cancelled and the other half is not cancelled)



Objectives 

1) how to mitigate the problem of cancellation and 
2) how to maximise the profits (Minimise the loss) from this context.
3) Provide insights about the users who is likely to cancel the hotel booking 
4) Select the best model and predict the conversion probabilities of the users 

Methodology

1) Data ingestion

EDA

2-1) Balanced Classes:

An assumption of classification models is that all the classes are of equal occurrence in the data set. 
In our case of a binary classification problem, the split is 50/50.
We have nearly even number of the dataset.

2-2) Data Encoding 

We initially tried the method of "One Hot Coding" and it caused the Sklearn version problem. 
Thus we used "dummies" instead.

3) Modeling

3-1) Data Scaling

In order to apply Logistic Regression, the data must be scaled in advance, 
because its accuracy might be influenced.

3-2) Data splitting (X,y split)

3-3) Class Modelling

We have made " pre-made coding" to apply later.

4) Models

we tested numbers of models 

I) Logistic Regression

( L.Regression is very easy to use and it generally gived a good prediction)  

we evaluated with following number of evaluation techniques:

1) Accuracy, 
2) Precision 
3) Recall 
4) F1_Score
5) Roc_Auc Score
6) Confusion Matrix

and we found two meaningful ones ( ROC and Confusion Matrix)

1) ROC

Train AUC (0.903361)
Validation AUC (0.898656)

2) Confusion Matrix

(7541, 1170),(1584, 4574)



II) Decision Trees 

1) Iteration 1

Train AUC (0.927799)
Validation AUC (0.919023)

2) Iteration 2

Train AUC (0.933974)
Validation AUC (0.921681)

3) Iteration 3

Train AUC (0.936956)
Validation AUC (0.923146)

4) Iteration 4

Train AUC (0.9372820)
Validation AUC (0.923006)

Confusion Matrix

(7812, 899),(1432, 4726)

We can clearly see that we have improved the accuracy from iterations (0.919023-> 0.923006)


*****************
Conclusion:

Decision Tree shows better accuracy over Logistics regression 

Logistic regression (0.898656) < Decision Tree (0.923006)

In addition, confusion matrix is also better than Logistics Regression.

Logistic regression (7541, 1170),(1584, 4574)  <  Decision Tree (7812, 899),(1432, 4726) 

we have better True Positive 7541 < 7812.
*****************


III) Random Forest

1) Iteration 1

Train AUC (0.999411)
Validation AUC (0.946462)

2) Iteration 2

Train AUC (0.998293)
Validation AUC (0.947042)

3) Iteration 3

Train AUC (0.998293)
Validation AUC (0.947042)


*****************
Conclusion:

ROC: Decision Tree (0.923006) < Random Forest (0.947042)

Matrix: Decision Tree (7812, 899),(1432, 4726) < Random Forest (8057, 654),(1185, 4973)  
*****************




IV) Ensemble Methods ( Train AUC, Validation AUC)

1) Voting Classifier (0.97889,0.942302)

2) AdaBoost - Random Boost ( 0.999942, 0.932234)

3) XGBoost (0.920237, 0.920104)

4) Stacking (0.996112, 0.948935)

*****************
Stacking has the highest accuracy of 0.948935
*****************


V) Model Selection 

We found that Stacking has the highest accuracy of 0.948935.

However, we decided to go for Random Forest, since it is faster and simpler method than Stacking.
Moreover, its different is only 0.001893.

VI) Importance Feature

We found the list of important features below

	Importance	Feature
	0.101343	LeadTime
	0.081141	Country_PRT
	0.074694	TotalOfSpecialRequests
	0.060365	ADR
	0.046779	PreviousCancellations
	0.029017	CustomerType_Transient
	0.027794	StaysInWeekNights
	0.020519	CustomerType_Transient-Party
	0.019357	StaysInWeekendNights
	0.017951	MarketSegment_Online TA
	0.016006	MarketSegment_Groups
	0.015982	Agent_ 9
	0.015354	Adults
	0.014579	DistributionChannel_TA/TO
	0.014467	Country_FRA
	0.013896	Agent_ 7
	0.012924	Country_DEU
	0.011856	AssignedRoomType_D
	0.009492	RequiredCarParkingSpaces
	0.009331	DistributionChannel_Direct

VII) Threshold Selection



VIII) Recommendation

1) Rather than apply the high - deposit models. 
   Future work might be good to find out the descount model( no need for deposit Early cancellation)
   or sell more services (cheaper rate of room upgrade , free internet wifi or 10% discount on the hotel restaurant etc)
   at the time of booking with discounted rate and charge them normal rate of cancellation of fee for all services 
   (room charge and services)
   
   
   


