# AB_Testing-
Projects and Case Studies of AB Testing 

__1.        What is A/B testing?__  
A/B testing (sometimes called split testing) is basically statistical hypothesis testing applied to web page comparison. 
You compare two versions of web pages by showing the two variants (call them A and B) randomly to two equally sized groups of visitors at the same time, the one that gives better conversion rate wins. 

__2.        Describe the process of A/B test__  
A/B test can be summarized into the 5 steps below: 
(1). choose and characterize metrics to evaluate your experiment, i.e. what do you care about, how do you want to measure the effect. 
Brain storm potential metrics. Use customer conversion funnel to summarize the process. Invariant metric does not relate to the change. Evaluation metrics are related to the change.
(2). choose significant level (alpha), statistical power (1-beta) and practical significance level you really want to launch the change if the test is statistically significant
(3). Calculate required sample size
(4). Take sample for control/ treatment groups and run the test
(5). Analyze the results and draw valid conclusions
Sanity check: invariant metric does not change in experiment and control  
Analyze evaluation metrics  
Using pooled mean/conversion probability, then calculate pooled standard deviation, then calculate margin of error (z*sd). Then compare the difference between control and experiment and calculate upper and lower bound of the difference (P-diff +/ - margin of error). Compare with 0 (statistically significant) or required difference to be practically different.
Sign test: confirm the result with sign test. The number of success out of total trial is statistically significant.

__3.  Situations we can’t analyze through A/B test__
A/B test can’t test new experience, because (1) what ‘s the base of your comparison (2) how much time it will take for the users to adapt to the new experience. 
Long term effect is hard to test with A/B test

__4.        How many variates should we have in A/B test__
The goal of A/B test should be clear. A number of factors from each different design can muddy the test result water. We suggest running two versions against each other, and then running a second test afterwards to compare the winners.

__5.        What do I do if I do not trust the results?__
If you really don’t trust the results and have ruled out any errors or challenges to the test’s validity, the best thing to do is to run the same test again. Treat it as an entirely separate test and see if you can replicate the results. If you can replicate again and again, you probably have a solid set of results.

__6.        What if I do not have control?__
A control is the existing version of a landing page or webpage that you are testing against. Sometimes you may want to test two versions of a page that never existed before… and that’s oaky. Just choose one of the variations and call that one the control. Try to pick the one that’s the most similar to how you currently design pages and use the other as the treatment.

__7.        When A/B test is not useful, what you can do?__
Analyze the user activity logs
Conduct retrospective analysis
Conduct user experience research
Focus groups and surveys
Human evaluation

__8.        Metrics__
The metrics we choose for sanity check are called invariant metrics. They are not supposed to be affected by the experiment. They should not change across control and experiment groups.
Evaluation metrics are used to measure which variation is better. For example daily active users (DAU) to measure user engagement; click through rate (CTR) to measure a button design on a webpage. 

There are four categories of metrics:
•        Sums and counts
•        Distribution (mean, median, percentiles)
•        Probability and rates (click through probability and click through rate)
•        Ratios: any two numbers divide by each other
Sensitivity and robustness:
You want to choose a metric that has high sensitivity, so the metric can pick up the change you care about. You also want the metric to be robust against changes you don’t care about. There is a balance between the sensitivity and robustness, you need to look into the data to find out which metric to use.
How to measure the sensitivity and robustness?
•        Run experiments
•        Use A/A test to see if metrics pick up difference (if yes, then the metric is not robust)
•        Retrospective analysis

__9.        Significance level, statistical power and practical significance level__
Usually the significance level is 0.05 and power is 0.8. practical significance level varies depends on each individual test. Practical significance level is higher than statistical significance level. You may not want to launch a change even the test is statistically significant because you need to consider
•        The business impact of the change
•        Whether it is worth to launch considering the engineering cost, customer support, sales issue and opportunity cost

__10.      How to estimate(calculate) sample size?__
Sample size required for valid hypothesis test depends on 5 of the following parameters
1.   The conversion rate value of control variation (baseline value)
2.   The minimum difference between control and experiment which is to be identified. 
The smaller the difference between experiment and control to be identified, the bigger the sample size is required.
3.   Chosen confidence/significance level
4.   Chosen statistical power
5.    Type of the test: one or two tailed test. Sample size for two tailed test is relatively bigger.
There are different kinds of online testing tools, G-power, Evan Miller, google analytics, etc. 
If using R, first calculate the z value based on alpha using qnorm(). Then using a grid of sample size values to calculate beta (the pdf of reject the null when the null is true) using pnorm(), so the smallest sample size corresponds to beta <= required beta is the required sample size for valid test. This make use of the fact that as sample size getting big, the estimated standard deviation become smaller, so the power of the test gets big. 
Formula:


__11.        How to split sample?__
The sample size in control and experiment should be statistically equal. 

__12.        Correlational VS causal__
You observe the churn rates for users using/not-using your feature:. 1point3acres
25% of new users that do NOT use your feature churn (stop using product 30 days later)
10% of new users that use your feature churn
[Wrong] Conclusion: your feature reduces churn and thus critical for retention
Flaw: Relationship between the feature and retention is correlational and not causal
The feature may improve or degrade retention: the data above is insufficient for any causal conclusion
Example: Users who see error messages in Office 365 churn less. 
This does NOT mean we should show more error messages.
They are just heavier users of Office 365
See Best Refuted Causal Claims from Observations Studies
for great examples of this common analysis flaw

(a)        Common cause: women have smaller palm and on average lives longer
(b)        Misses time related factors, such as external events, weekends, holidays, seasonality

__13.        Advantages of A/B test__
Scientific way to prove causality, i.e. the changes in metrics are caused by changes introduced in the treatment.
Sensitivity: you can detect tiny changes to metrics
Detect unexpected consequences
