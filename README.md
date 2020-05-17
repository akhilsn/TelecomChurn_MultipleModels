# TelecomChurnPredict-DrivingFactors-MultipleModels
A huge dataset consisting of a telecom operator 'T' customer records for the months of June, July, Aug, Sept (2014). Objective is to find High Value Customers, label them with Churn/Not churn (based on certain criteria described later), make multiple models for predictions, and models to derive driving factors towards Churn.


## Problem Statement, Details, and Approach towards Model Building:

### 1. Problem Statement

In the telecom industry, customers are able to choose from multiple service providers and actively switch from one operator to another. It is a highly competitive market, where telecommunications industry experiences an average of 15-25% annual churn rate. Given the fact that it costs 5-10 times more to acquire a new customer than to retain an existing one, customer retention has now become even more important than customer acquisition.

For many incumbent operators, retaining high profitable customers is the number one business goal.
To reduce customer churn, telecom companies need to predict which customers are at high risk of churn.

In this project, we analyse customer-level data of a leading telecom firm, build predictive models to identify customers at high risk of churn and identify the main indicators of churn.

### 2. Understanding and Defining Churn
There are two main models of payment in the telecom industry - postpaid (customers pay a monthly/annual bill after using the services) and prepaid (customers pay/recharge with a certain amount in advance and then use the services).

In the postpaid model, when customers want to switch to another operator, they usually inform the existing operator to terminate the services, and you directly know that this is an instance of churn.

However, in the prepaid model, customers who want to switch to another network can simply stop using the services without any notice, and it is hard to know whether someone has actually churned or is simply not using the services temporarily (e.g. someone may be on a trip abroad for a month or two and then intend to resume using the services again).
Thus, churn prediction is usually more critical (and non-trivial) for prepaid customers, and the term ‘churn’ should be defined carefully.  Also, prepaid is the most common model in India and southeast Asia, while postpaid is more common in Europe in North America.

-> In this Project, our dataset is based on the Indian and Southeast Asian Market, and hence the records are from Pre-Paid Customers. 

### 3. Definitions of Churn
There are various ways to define churn, such as:

a. Revenue-based churn: Customers who have not utilised any revenue-generating facilities such as mobile internet, outgoing calls, SMS etc. over a given period of time. One could also use aggregate metrics such as ‘customers who have generated less than INR 4 per month in total/average/median revenue’.
The main shortcoming of this definition is that there are customers who only receive calls/SMSes from their wage-earning counterparts, i.e. they don’t generate revenue but use the services. For example, many users in rural areas only receive calls from their wage-earning siblings in urban areas.

b. Usage-based churn: Customers who have not done any usage, either incoming or outgoing - in terms of calls, internet etc. over a period of time.
A potential shortcoming of this definition is that when the customer has stopped using the services for a while, it may be too late to take any corrective actions to retain them. For e.g., if you define churn based on a ‘two-months zero usage’ period, predicting churn could be useless since by that time the customer would have already switched to another operator.

 
-> In this project, we shall use the usage-based definition to define churn.

### 4. High Value Churn
In the Indian and the southeast Asian market, approximately 80% of revenue comes from the top 20% customers (called high-value customers). Thus, if we can reduce churn of the high-value customers, we will be able to reduce significant revenue leakage. 

-> In this project, we will define high-value customers based on a certain metric (mentioned later below) and predict churn only on high-value customers.

### 5. Understanding the Business Objective and the Data
The dataset contains customer-level information for a span of four consecutive months - June, July, August and September (months are encoded as 6,7,8,9).

The business objective is to predict the churn in the last (i.e. the ninth) month using the data (features) from the first three months. To do this task well, understanding the typical customer behaviour during churn will be helpful.

### 6. Understanding Customer Behaviour During Churn
Customers usually do not decide to switch to another competitor instantly, but rather over a period of time (this is especially applicable to high-value customers). 

***In churn prediction, we assume that there are three phases of customer lifecycle :***

The **‘good’ phase***: In this phase, the customer is happy with the service and behaves as usual.

The ***‘action’ phase***: The customer experience starts to sore in this phase, for e.g. he/she gets a compelling offer from a  competitor, faces unjust charges, becomes unhappy with service quality etc. In this phase, the customer usually shows different behaviour than the ‘good’ months. Also, it is crucial to identify high-churn-risk customers in this phase, since some corrective actions can be taken at this point (such as matching the competitor’s offer/improving the service quality etc.)

The ***‘churn’ phase***: In this phase, the customer is said to have churned. ***We define churn based on this phase.*** Also, it is important to note that at the time of prediction (i.e. the action months), this data is not available to us for prediction. Thus, after tagging churn as 1/0 based on this phase, we discard all data corresponding to this phase.

In this case, since we are working over a four-month window, the first two months are the ‘good’ phase, the third month is the ‘action’ phase, while the fourth month is the ‘churn’ phase.

#### NOTE: Please refer to the Data Dictionary to understand the Features given in the dataset.

Finally, we shall recommend strategies to manage customer churn based on our observations.
