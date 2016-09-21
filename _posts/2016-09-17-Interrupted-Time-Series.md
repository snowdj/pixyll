---
published: true
layout: post
---
## UBCx: ITSx Policy Analysis using Interrupted Time Series
### OBSERVATIONAL STUDY DESIGNS


In a pre-post study design, the counterfactual assumption is that the level of the outcome would not have changed absent the change being studied. 

In a post-only with control study, the assumption is that the counterfactual outcome in the intervention group would have mirrored that observed in the control group. This study design is very prone to selection bias. It is likely that the locations vary on a number of other factors -- both observable and unobservable -- that impact fuel sales.


has data for two groups at one time period before the intervention and one time period after. This reflects a pre-post with control design.


The counterfactual assumption in this study design is that the outcome would have changed in the invention group in the same manner as the control group absent the intervention.

School break is clearly an event that occurs between the periods, so is a history threat to validity. However, in this case as it only affects one group and not the other, it is an interaction with selection in this instance.

the second example is a potential threat to validity. While the first looks like a history threat, the timing would have to be close to the intervention in order to be of concern. The second is an example of an instrumentation threat and is of concern as it happened close to the intervention. Finally, migration out is an issue of maturation, but because it was constant over the entire period would not constitute a threat to validity. Any changes in the outcome this caused would likely be addressed by the estimate of the pre-intervention time trend.



##

identified many potential threats to validity

collect longitudinal data and conduct a single interrupted time series analysis on her data

Both A and C are potential threats, because they are changes that would potentially impact the outcome (fuel sales), are not the intervention of interest, and happen close to the intervention under study. In contrast, while B may impact the outcome, it happended at the start of the study period, so would not be of concern. Any change that it did cause in the outcome would be captured in the existing level and trend in the pre-intervention period.

The answer to the above question represents a history threat to validity, as it is an event that is not the intervention of interest that would be expected to impact the outcome. It would not be selection-history, as there is only one group under study in this data series.

The key to this answer is the change in Bogusland, which we know was not subject to the carbon tax. The decrease in slope observed around the time of the intervention line is consistent with a change in the price of fuel that acted to decrease the secular trend in consumption.


It is important to remember that all of your estimates for the impact of the policy will be relative to the changes observed in the control group. As the level in the control group appears to increase slightly after the intervention, this would serve to increase the relative change in the intervention group. Conversely, the downward trend in the control group would cause the change in trend to be smaller relative to the estimate from the single series model.


 the actual steps you will take to conduct an analysis yourself. We will divide things up into 10 steps, which are:

* Determine time periods
	* interruption 
    * length of period enough to measure a trend 8/12 
    
    A commonly cited minimum number of data points is 8-12 before and 8-12 after the intervention. Be cautious with this rule, however. Many data series will be too variable for 8 data points to provide a stable trend estimate.
    
    
    * phase-in period
    * co-interventions
    
    Any fixed time period is suitable for an ITS analysis. There will be a trade-off with any selection: longer time periods will likely be more stable, but are also more likely to run into trouble with co-interventions that impact the same outcomes.
    
    
    
* Select analytic cohorts
	* expect impact
    * continuously enrolled// attrition -> problem
    * control groups: unexposed similar group/ subgroup, another region. non-equivalent but still comparible
    
    What's one advantage of having individual level data?
        
You can focus in on groups where you expect an impact     
    Individual-level data gives you the flexibility to run your time series models on whatever subgroups you like within your study population. This can allow you to narrow in on groups where the policy likely had an impact, and also use those where you wouldn't expect an impact as potential controls.
    
    In order to fit the model with a control group, you must have access to data on the same outcomes over the same time periods. While A and B would definitely help make your analysis more convincing, they are not technically required. With respect to response D, control groups can come from within the same region.
    
    
* Determine outcomes of interest
	* characteristic/outcome 





* Setup data
* Visually inspect the data
* Perform preliminary analysis
Check for and address autocorrelation
Run the final model
Plot the results
Predict relative and absolute effects


