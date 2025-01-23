java c
STATS 763 - 2020 - Final assessment
Due by 4 July 2020 at 12:59 PM
Question 1. [15 marks total]


All cases of non-pregnancy-related listeriosis (a contaminated food-borne disease) occurring in Germany in 2012-2013 were identified. Controls were randomly sampled throughout the country using stratified sampling by age group. Basic information about the sample and population is given in the table below:

We are interested in the effect of consuming cold sausage on listeriosis occur-rence. The data are described as follows:

The first few records in the data are as follows:
> lis %>% head
# A tibble: 6 x 6
Listeriosis ‘Age group‘ ‘Education level‘ Sex Residence ‘Cold sausage‘
     
1 0 66-75 years Medium Female Town 0
2 0 <66 years High Female Town 0
3 0 <66 years Medium Male Town 0
4 0 >75 years Medium Male City 0
5 0 <66 years Medium Male Town 0
6 0 >75 years Medium Female Town 0
We estimate the effect of eating cold sausage for each Residence type and Age
group, adjusting for Residence, Age group, Education level and Sex:
> mod <- glm(Listeriosis~Residence*‘Cold sausage‘+‘Age group‘*‘Cold sausage‘+
+ ‘Education level‘+Sex,family=quasibinomial,data=lis)
> summary(mod)
Coefficients:
Estimate Std. Error t value Pr(>|t|)
(Intercept) -2.68228 0.61584 -4.355 1.4e-05 ***
ResidenceTown 0.47075 0.50280 0.936 0.349264
ResidenceCity 0.33780 0.53923 0.626 0.531105
‘Age group‘66-75 years 0.14661 0.35010 0.419 0.675433
‘Age group‘>75 years -0.27777 0.38667 -0.718 0.472621
‘Cold sausage‘ 1.88051 0.66232 2.839 0.004571 **
‘Education level‘Medium -0.90318 0.35747 -2.527 0.011602 *
‘Education level‘High -1.50549 0.42215 -3.566 0.000371 ***
SexFemale 0.06277 0.23756 0.264 0.791629
ResidenceTown:‘Cold sausage‘ -1.29123 0.69861 -1.848 0.064722 .
ResidenceCity:‘Cold sausage‘ -0.12498 0.71799 -0.174 0.861827
‘Age group‘66-75 years:‘Cold sausage‘ -0.83537 0.55918 -1.494 0.135369
‘Age group‘>75 years:‘Cold sausage‘ -0.41770 0.58412 -0.715 0.474645
---
Signif. codes: 0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
(Dispersion parameter for quasibinomial family taken to be 1.038695)
Null deviance: 702.15 on 1853 degrees of freedom
Residual deviance: 663.69 on 1841 degrees of freedom
AIC: NA
Number of Fisher Scoring iterations: 6
a) [2 marks]
Explain briefly why it is necessary to include the Age group in this model to correctly estimate the effect of eating cold sausage on non-pregnancy-related (NPR) listeriosis.
b) [2 marks]
Explain briefly why the coefficient estimates for cold sausage above are ap-proximately those of log-relative risks.
c) [3 marks]
What is the estimated relative risk of NPR listeriosis from eating vs not eating cold sausage amongst Village residents older than 75 years?
d) [3 marks]
Is there any combination of factor levels for which the estimated relative risk of NPR listeriosis from eating vs not eating cold sausage is smaller than 1? If so, describe any such combination.
e) [2 marks]
Consider the log-odds ratio of NPR listeriosis amongst Village residents younger than 66 years. What would its standard error be under a binomial regression model with logit link?
f) [3 marks]
An alternative way to analyse these data is design-weighted estimation, using for instance the svyglm function from the survey package. What weights would you use on each observation to estimate similar relative risks as above?
Question 2. [15 marks total]
In economics and sociology there are competing theories to explain the higher in-come of people with university degrees. Here are three examples:
• The Human Capital theory says that university education improves both specific knowledge about certain topics and some general reasoning and com-munication skills, so that people who gain university degrees become more valuable employees than they would otherwise have been. Some degrees are more valuable than others because you learn more employment-代 写STATS 763 - 2020 - Final assessmentPython
代做程序编程语言relevant skills doing them.
• The Signalling theory says that university education is difficult, and gaining a university degree shows employers that you are more able than other poten-tial employees, even though the education you receive is not valuable to the employer. Some degrees are more valuable than others because they are more difficult and so people who get those degrees have higher average ability.
• The Social Stratification theory says that university education functions to show that you come from a relatively affluent or otherwise high-status family, and so you are not the sort of person that the employer likes to discriminate against. Some degrees are more valuable than others because they discrimi-nate more effectively against low-status people.
Here is a causal directed graph for relationships between these variables, where the lack of an arrow indicates you may assume there is no effect.

a) [6 marks]
For each of the three theories, remove as few edges as possible from the graph to give the graph if that theory were the only explanation operating. (you may either draw the graphs or list the edges to be removed)
b) [3 marks]
Under the Signalling hypothesis, what are the confounding paths from degree to income?
c) Suppose that ability was measured on a random sample of people by testing at high school, and status by an interview of individuals and families
i [2 marks]
If (unrealistically) the measurements were perfectly accurate, give a model that would estimate the (total) effect of learning on income
ii [2 marks]
Which theory or theories would be supported by a large value of this effect?
iii [2 marks]
If, instead, the measurements were made with substantial error or un-certainty, what would be the impact on the effect estimate?
Question 3. [20 marks total]
A company is marketing an expensive new drug to lower cholesterol. In order to justify the price, they want to find a subset of potential users where the effect of the drug is particularly large.
They have data on 3,500 people who took the drug in a randomised trial, with two cholesterol measurements before the start of treatment and six measurements after the start of treatment, all at three-month intervals (Yi1...Yi8), with
Di = 6/1 (Yi3 + Yi4 + Yi5 + Yi6 + Yi7 + Yi8) − 2/1 (Yi1 + Yi2),
the average change, being the preferred summary of the effect.
They also have 10,000 binary predictor variables G1, . . . , G10000, with each one measuring whether the person has (1) or does not have (0) a particular genetic variant. Scientists expect that most of the genetic variants will have no effect on cholesterol, but that some will have quite large effects on cholesterol regardless of whether the person is taking the drug (they affect both the pre-treatment and on-treatment values) and others will have quite large effects on the reduction in cholesterol due to taking the drug (they affect only the on-treatment values).
a) i [4 marks]
What is one technique covered in the course that would be appropriate for finding a model to predict D from the Gs?
ii [4 marks]
In this context, what are the the advantages and disadvantages of cross-validation in estimating prediction error compared to a training set/validation set split of the data?
b) Data is also available on the proportion Xit of their prescribed pills that person i took in the time period leading up to measurement Yit (for t > 2). The researchers are willing to assume that the genetic variables do not affect the proportion of pills that someone takes.
i [4 marks]
If you simply regress the observations (Yit)t>2on Xit using lm(), what parts of the output will be correct and what parts will be misleading?
ii [4 marks]
What is one technique for getting valid inference about the association between X and Y ?
iii [4 marks]
The researchers are interested in how much the relationship between X and Y varies from person to person. How could you estimate this?







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
