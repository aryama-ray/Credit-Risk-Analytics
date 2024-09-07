# Credit Risk Analytics

1.	BUSINESS REQUIREMENT

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
 
2.2 Exploratory Data Analysis

Key finding from the analysis:

1. Number of times customer has not payed dues since 90/60/30 days in last 6/12 months are highly correlated with each other.
2. Presence of home loan and outstanding balance are highly correlated
3. Total number of trades highly correlated with number of trades/PL trades opened in last 6/12 months.It has also high correlation 
4. with number of queries made in last 6/12 months excluding home/auto loans

2.3 Calculation of Weigh of Evidence(WoE) and IV Values

                               Variable           IV
       Avgas.CC.Utilization.in.last.12.months 0.2610204093
                           Total.No.of.Trades 0.2089818314
            No.of.months.in.current.residence 0.0649495645
                   Presence.of.open.home.loan 0.0169166671
              No.of.months.in.current.company 0.0131186314
                             No.of.dependents 0.0029249685
                                   Profession 0.0020202656
                   Presence.of.open.auto.loan 0.0015484526
                            Type.of.residence 0.0008705523
                                    Education 0.0008287873
                                       Gender 0.0002698331
  Marital.Status..at.the.time.of.application. 0.0001039180

3. Model building
 
#---------------------------------------------------------------------------------------------------------------------------------
 Model Type					Accuracy	Sensitivity	Specificity	KS Statistic	ProbCutoff
#---------------------------------------------------------------------------------------------------------------------------------
- Biased Data - Logistic Regression	       	0.6342029	0.6204955	0.6348173	0.2553128	0.0450000
- Biased Data - Random Forest			 0.6227053	0.6103604	0.6232586	0.2336190	0.0388000
- Unbiased Data - SMOTE - Logistic Regression	 0.6794686	0.5540541	0.6850898	0.2391439	0.5346465
- Unbiased Data - SMOTE - Random Forest without CV 0.6307246	0.5900901	0.6325459 	0.2226360	0.3611111
- Unbiased Data - SMOTE - Random Forest with CV	 0.6035749	0.5822072	0.6045326	0.1867398	0.3291919
#---------------------------------------------------------------------------------------------------------------------------------

4. Application Score Card

Application Score Card and Financial Analysis is performed for Random Forest Unbised Data without CV.
Cut off credit score is calculated in the following way.

-  Factor <- (20/log(2))
-  offset <- 400 - (Factor*log(10))

- Calculated Cut off score:350.0239

- 59% of total potential defaulter customer will be denied of credit card using this model
