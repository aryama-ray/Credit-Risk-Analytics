# Customer Acquistion Analytics: Capstone Project

1.	PROBLEM STATEMENT AND BUSINESS REQUIREMENT

CredX is a leading credit card provider. It receives thousands of credit card applicants every year. However, in the past few years it has experienced an increase in credit loss for such issued credit cards. 
Our endeavor would be to help CredX to identify the right set of customers using predictive models such that right set of customers are acquired, and credit loss is minimized. 
There are two data sets available namely demographic information and credit performance history about the past applicants. Based on this information we need to analyze and formulate the risk model. This model is to be assessed from financial benefits perspective and following are required to be reported:

●	The implications of using the model for auto approval or rejection, i.e. how many applicants on an average the model would automatically approve or reject.
●	The potential credit loss avoided with the help of the model.
●	Assumptions based on which the model has been built.

2.	ANALYSIS APPROACH 

To mitigate the acquisition risk, we target to minimize defaulter rate by acquiring right customers. From applicants’ demographic data and past credit data from credit bureau, we have their performance tag, which denotes if the customer has defaulted or has good credit history without being a defaulter. Hence, we target this performance tag variable and analyze the data to build a model which can predict the performance of customer accurately.

Our analysis approach will start with data understanding, cleansing and preparation followed by exploratory data analysis using weight of evidence (WOE),Information value(IV) analysis and transformation.We will then perform different data modeling to deduce the ideal model which can predict defaulter rate accurately.

2.1	DATA UNDERSTANDING

Demographic or customers’ application data is provided by customers during credit card application. It consists of customer level information like
Age
Gender
Marital status
Number of dependents
Income
Education
Profession
Type of residence
Number of months customer residing in a current residence
Number of months the customer is in current company

This data set has total 71295 records along with 12 variables.
  Credit related information is taken from Credit Bureau and it contains customer’scredit performance historylike:
	Number of times customer did not pay dues since 30/60/90 days within last 6 months or 12 months
	Average utilization of credit card by customer
	number of times the customer has done the trades in last 6 months/ 12 months
	number of times the customers has inquired in last 6 months/12 months
	Whether customer has home loan
	Outstanding balance
	Number of times customer has done total trades
	Whether the customer has auto loan

This data set has total 71295 records along with 19 variables.
	Both the data sets have unique Application ID for each record
	Both the data sets have 71292 unique records
	Both the data sets haveperformance tag indicating good and defaulter/bad customers
