# Customer Survival Analysis

## Introduction
 
Customer attrition, also known as customer churn, customer turnover, or customer defection, is the loss of clients or customers.

Telephone service companies, Internet service providers, pay TV companies, insurance firms, and alarm monitoring services, often use customer attrition analysis and customer attrition rates as one of their key business metrics because the cost of retaining an existing customer is far less than acquiring a new one. Companies from these sectors often have customer service branches which attempt to win back defecting clients, because recovered long-term customers can be worth much more to a company than newly recruited clients.

Predictive analytics use churn prediction models that predict customer churn by assessing their propensity of risk to churn. Since these models generate a small prioritized list of potential defectors, they are effective at focusing customer retention marketing programs on the subset of the customer base who are most vulnerable to churn.

**Survival Analysis:** 
Survival analysis is generally defined as a set of methods for analyzing data where the outcome variable is the time until the occurrence of an event of interest. The event can be death, occurrence of a disease, marriage, divorce, etc. The time to event or survival time can be measured in days, weeks, years, etc.

For example, if the event of interest is heart attack, then the survival time can be the time in years until a person develops a heart attack.

**Objective:**
The objective of this analysis is to utilize non-parametric and semi-parametric methods of survival analysis to answer the following questions.
- How the likelihood of the customer churn changes over time?
- How we can model the relationship between customer churn, time, and other customer characteristics?
- What are the significant factors that drive customer churn?
- What is the survival and Hazard curve of a specific customer?
- What is the expected lifetime value of a customer?

**Kaplan-Meier Survival Curve:**

<p align="center">
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/SurvivalCurve.png" width="400" height="300">
</p>

From above graph, we can say that
- AS expected, for telcom, churn is relatively low. The company was able to retain more than 60% of its customers even after 72 months.
- There is a constant decrease in survival probability probability between 3-60 months.
- After 60 months or 5 years, survival probability decreases with a higher rate. 

**Log-Rank Test:** 

Log-rank test is carried out to analyze churning probabilities group wise and to find if there is statistical significance between groups. The plots show survival curve group wise.

<p align="center">
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/gender.png" width="250" height="200"/> 
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/Senior%20Citizen.png" width="250" height="200"/>
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/partner.png" width="250" height="200"/> 
</p>

<p align="center">
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/dependents.png" width="250" height="200"/> 
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/phoneservice.png" width="250" height="200"/>
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/MultipleLines.png" width="250" height="200"/> 
</p>

<p align="center">
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/InternetService.png" width="250" height="200"/> 
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/OnlineSecurity.png" width="250" height="200"/> 
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/OnlineBackup.png" width="250" height="200"/> 
</p>

<p align="center">
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/DeviceProtection.png" width="250" height="200"/> 
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/TechSupport.png" width="250" height="200"/>
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/Contract.png" width="250" height="200"/> 
</p>

<p align="center">
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/StreamingMovies.png" width="250" height="200"/>
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/paymentmethod.png" width="250" height="200"/> 
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/PaperlessBilling.png" width="250" height="200"/>
</p>

From above graphs we can conclude following:
- Customer's Gender and the phone service type are not indictive features and their p value of log rank test is above threshold value 0.05.
- If customer is young and has a family, he or she is less likely to churn. The reason might be the busy life, more money or another factors.
- If customer is not enrolled in services like online backup, online security, device protection, tech support, streaming Tv and streaming movies even though having active internet service, the survival probability is less.
- The company should traget customers who opt for internet service as their survival probability constantly descreases. Also, Fiber Optilc type of Internet Service is costly and fast compared to DSL and this might be the reason of higher customer churning. 
- More offers should be given to customers who opt for month-to-month contract and company should target customers to subscribe for long-term service. 
- If customer's paying method is automatic, he or she is less likely to churn. The reason is in the case of electronic check and mailed check, a customer has to make an effort to pay and it takes time.

**Survival Regression:**
I use cox-proportional hazard model to perform survival regression analysis on customer data. This model is used to relate several risk factors or exposures simultaneously to survival time. In a Cox proportional hazards regression model, the measure of effect is the hazard rate, which is the risk or probability of suffering the event of interest given that the participant has survived up to a specific time. The model fits the data well and the coefficients are shown below.

<p align="center">
<img src="https://github.com/PrachiKharat/Customer-Survival-Analysis/blob/main/Plots/Survival-analysis.png" width="750" height="500"/>
</p>

Using this model we can calculate the survival curve and hazard curve of any customer as shown below. These plots are useful to know the remaining life of a customer. 

<p align="center">
<img src="https://github.com/archd3sai/Customer-Survival-Analysis-and-Churn-Prediction/blob/master/Images/survival.png" width="400" height="300"/>
<img src="https://github.com/archd3sai/Customer-Survival-Analysis-and-Churn-Prediction/blob/master/Images/hazard.png" width="400" height="300"/>
</p>

**Customer Lifetime Value:**

To calculate customer lifetime value, I would multiply the Monthly charges the customer is paying to Telcom and the expected life time of the customer.

I utilize the survival function of a customer to calculate its expected life time. I would like to be little bit conservative and consider the customer is churned when the survival probability of him is 10%.
