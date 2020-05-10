# UnSupervisedLearning
Data analysis of Loan Clustering

Objective:
The understanding of the segments in customers that the marketing team needs to focus more on the high potential customer and invest more.

Expectation: 

Identify the segment of People based on the following features has any influence on new applicants with a higher approval rate where our marketing team can invest more.
1)	Age
2)	Area (Urban/Rural)
3)	Converted (Funded/Not Funded)
4)	Approval Percentage

We can have a hypothesis whether the APR rate has any influence in the Converted Funds or not.

Univariate Data Analysis: 

We will explore the distribution of data of every feature available to check any outlier or anomaly present. 
Feature 1: Age Analysis: 
The age of 20-30 age slab applicants holds for 26 % of total applicants 

 





Feature 2: Loan Amount Analysis: 

 
Feature 3:             Deposit Analysis: 
 
Feature 4:        Car Type Analysis:

 



Feature 5:               Area Analysis:

Rural has 52% of total application
Urban has 48% of total application
 


Feature 6:   Application Outcome Analysis: 
The average approval rate is 64.7%

 

Feature 7:  Funded Analysis: 
 

Feature 8: Annual Percentage Rate: 
 
Data Pre-Processing: 

Removing Trailing Space:

The data has extra few unwanted trailing spaces in columns and dropping those which offer no value.

Finding Missing values: 

By shaping the dataset, we can identify the number of missing values in the rows. We identify more than 3530 columns have missing values.

  





Unbiased Data:

The data set of Rural applicants (5290) and Urban applicants (4710) in the data set is not equal. So, we will be experienced biased results when we run our model over the dataset.

Data Cleansing: 

The data received has pounds, the comma between numbers, trail values, missing values, N/A available for more than 3530 rows. We removed those and before apply our analysis over the dataset. 

The more information on the dataset cleaning and preparation was explained in the python workbook file attached. 

Cross Tab Analysis:  

We will be comparing all the category features for other categories or continuous variables. 

APR vs Application Outcome: 
We need to find the relation of the application outcome. i.e approval status has any relation with APR rate
 


Application Outcome vs Age:
From the below boxplot, we can see no applicants of age group (>50 years) was declined. Also, 50% of the applicant who canceled are in the age between 25 years to 35 Years
 

Application outcome vs Car_type

 

Application Outcome vs Age Slab

We shall pivot age feature using Excel to create a window/Slab for applicant age (from 18+ to 65) frequency slab over Application outcome. This again verifies the Applicants age below 35 has the greatest number of declined applications. 
  


We start with the Approval Success Rate versus Area code as this shows significant during our univariate analysis. The Area code had the lesser granularity again the approval rate and go deeper from there.

Summary of Application Outcome

Approved Applicants	6470
Declined Applicants	3530
Grand Total	10000
Total Approval: 64% 

Crosstab analysis of Area Vs Application Outcome

Approved	6470
No	3401
Rural	1798
Urban	1603
Yes	3069
Rural	1245
Urban	1824
Declined	3530
Grand Total	10000
	

Rural (52% of overall applicants)       
Approved: 3043(57.5%)    
Declined: 2247(42.4%)
 
Urban (48% of overall applicant)
Approved: 3427(72.7%) 
Declined: 1283(27.2%)


Inference 1:

1.	Overall applicants have 52% of rural people and 48% of urban people.
2.	The Urban people's approval rate is 20% higher than rural applicants. 


Crosstab analysis on (Age Slab, Area) vs Approval status

To portray the target market, we will be window/group the age which will help the marketing/sales team. We will create a pivot column to group a certain age group. So that we will age group will be reduced in five slabs which will help us segment target people.

Age group	Age Slab
60+	60 Above
50 to 60	50 TO 60
40 to 50	40 TO 50
30 to 40	30 TO 40
20 to 30	20 TO 30
10 to 20	Below 20

Row Labels	Rural	Urban	Grand Total	 
Approved	3043	3427	6470	% of Approval
20 TO 30	392	462	854	24
30 TO 40	576	632	1208	58
40 TO 50	781	834	1615	81
50 TO 60	753	844	1597	78
60 Above	488	589	1077	84
Below 20	53	66	119	29
Declined	2247	1283	3530	 
20 TO 30	1223	541	1764	76
30 TO 40	409	339	748	42
40 TO 50	179	99	278	19
50 TO 60	211	156	367	22
60 Above	93	28	121	16
Below 20	132	120	252	71
Grand Total	5290	4710	10000	 

Inference 2:
•	All Approved applicants are coming from the age slab more than 50 and above. 
•	All the Rural declined applicants were below 40 years. 
•	Only 4% of the 60+ age applicant’s application got declined.
•	The applicants who declined with age below 30 have a rejection rate of more than 71%. 
•	The age slab above 60 has success Fund rate of 79 %
•	People fall in age slab between 20-30 years accounts for 50% of total applicants declines. 
















Python Cluster Classification: 

This method of segment identification gives equal opportunities to all the features available in the dataset. 
Python Pandas, seaborn, matplotlib, sklearntree for pre-processing, labeling, applying unsupervised K-Means cluster, PCA techniques.
Modeling steps:
1.	Load pre-processed data
2.	Treat the categorical values for modeling
3.	Find the optimal cluster size
4.	Do PCA to reduce the dimension.
5.	Apply K-means clustering on PCA components and map the cluster to the original data
6.	Analysis of cluster mapped data

 Finding an optimal cluster size using Elbow curve:
 






Cluster Result:
 
K-Means Cluster
Cluster mapped Data:
 
“Customer_Segments” – Column that specifies the cluster
We will then tabulate the features to the funded column. 

Cluster Vs (Application outcome and fund status)
From below pic, we can correlate our customer segment feature along with the application outcome and funded customer

 

Inference 3:
1.	From the result, we can see that customer segment 0 and segment 3 has the highest approval rate. This helps the marketing team to focus more on segment 3 applicants only.
Approved, Funded and Loan Amount Coded:
We then group/bin based on the age slab, loan, and deposit based on the segment cluster 0,1,2,3 and 4. 
Group/Code of Feature Age, Deposit and Loan Amount: 
   
 
The above-binned features are then crosstab to find out the pattern. 

 
Approved vs Funded vs Loan Amount Coded
We need to focus on the customer not funded and deposit code less than 4 as they have a high probability of approved applicants
Here we identify the pattern of funds based on the Annual Percentage Rate. We see APR value less than 10% have resulted in nearly twice that of funds taken.
 

From the above picture, we can identify that the applicants belong to Cluster 4 has more percentage probability for rejection of the application as wells as no fund approval.
Likewise, if a new customer comes in, we can fit the customer features and identify which cluster the customer falls and identify the success rate probability. 

Inference 4: 
•	We identify the applicants belong to the segment cluster 2 and 3 have a higher approval rate even though it was not funded. 
•	We can go granular further by windowing the deposits and loan amount to see the category of 0 to 4 has resulted in no funds. So, our marketing team can concentrate more on the no fund people with deposit code less than 4. 

Overall Summary of Inference:

•	Applicants from the urban people have more approval rate (72%) in comparison to the Rural applicants (40%). The marketing strategy should be more focussed on the urban area compared to rural.

•	Moreover, our marketing team can only concentrate on people aged over 50+ in the rural area has more probability (80%) of loan approval. 

•	As less than 40 years old people from rural areas already approved and funded, so the market can more focus on other aged people from rural areas.

•	The Decline rate of the people below 30 age group has a rejection rate of more than 71%. The marketing team needs to give promotions and discounts for those segments.

•	Nearly 50 % of all the rejection in the rural area was between 20 to 30 age group.

•	From the unsupervised clusters, we find the segment 0 and segment 3 has a higher approval rate even though it is not funded. 

•	From Approved vs Funded vs Loan Amount Coded table, we can see not converted/Funded applicants with Loan amount slab (0,1 and 2) and deposit bin (0,1, 2, and 3).  For more slab information check page 13 tables (Group/Code of Feature Age, Deposit and Loan Amount).

•	From Converted Funds vs APR, we find a pattern that particular segments of people age even after the approval the fund is not converted. We need to market towards the features of those segments of people so that we can be sure the applicant’s application has more probability for approval. This could help us to market on the segment of people who has higher chances of loan approval. 






 

