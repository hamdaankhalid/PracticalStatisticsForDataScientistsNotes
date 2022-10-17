# Statistical Experiments and Significance Testing

## Inference Pipeline
1. Formulate hypothesis
2. Design experiment
3. Collect data
4. Inference/Conclusions

## A/B Testing
- Experiment with 2 groups to establish which of 2 treatments/product/procedure is better.

### Key terms:
- Treatment: Something to which a subject is exposed. (Drug, price, web headline).
- Treatment group: Group of subjects exposed to a specific treatment.
- Control group: Group of subjects exposed to no (or standard) treatment.
- Randomization: Process of randomly assigning subjects to treatments.
- Subjects: Items exposed to treatment (web visitors, patients, etc).
- Test statistic: metric used to measure the effect of the treatment.
  
## Why have a control group?
- Without a control group, there is no assurance that "all other things are equal" and that any difference is really due to the treatment (or to chance). When you have a control group, it is subject to the same conditions (except for the treatmen of interest) as the treatment group.

## Hypothesis Tests/Significance tests
- Purpose of these tests is to help you learn whether random chance might be responsible for an observed effect.

### Key terms:
- Null hypothesis: The hypothesis that chance is to blame.
- Alternative hypothesis: Counterpoint to the null (what you hope to prove).
- One-way test: Hypothesis test that counts chance results only in one direction.
- Two-way test: Hypothesis test that counts chance results in two directions.

##
- An A/B test is typically constructed with a hypothesis in mind. E.g. hypothesis could be that price B produces higher profit.
- Statistical hypothesis testing was invented as a way to protect resarchers from being fooled by random chance.
- We perform statistical hypothesis testing for further analysis on A/B test, or any randomized experiment, to assess whether random chance is a reasonable explanation for the observed difference between groups A and B.

## One-Way vs Two-Way Hypothesis Tests
- Often in A/B test, you are testing a new option (say B) against an established default option A, and the presumption is that you will stick with the default unless the new option proves itself definitively better. In such a case, you want a hypothesis test to protect you from being fooled by the chance in the direction favoring B. You don't care about being fooled by chance in the other direction because you would be sticking to A unless B proves definitively better. So you want a direcitonal alternative hypothesis (B is better than A). In such a case, you use a one way or one tail hypothesis test.
- If  you want a hypothesis test to protect you from being fooled by chance in either direction, the alternative hypothesis is bidirectional (A is different from B, could be bigger or smaller). In such a case you want a two-way or two tail hypothests test.

## Resampling
- Resampling in statistics means to repeatedly sample values from observed data, with a general goal of assessing random variability in a statistic. It can also be used to assess and improve the accuracy of some machine learning models. There are two main resampling procedures: bootstraop and permutation tests.

### Key terms for Resampling:
- Permutation test/Randomization test: The procedure of combining two or more samples together and randomly reallocating the observations to resamples.
- With or without replacement: In sampling, whether or not an item is returned to the sample before the next draw.

### Permutation Test:
- Samples from two (A and B) or more are combined. We then test that the hypothesis by randomly drawing groups from the combined set and seeing how much they differ from one another. The eprmuation procdure is as follows:
1. Combine results from different groups into one set.
2. Shuffle the combined data, randomly draw (without replacement) a resample of the same size as group A.
3. From the remaining data, randomly draw (without replacement) a resample of the same size as group B.
4. Do the same for groups C,D, and so on. YOu have now collected one set of resamples that that mirror the size of original samples.
5. Whatever statistic or estimate wass calculated for the original samples, calculate it now for the resamples, and record; this constitutes one permuation iteration.
6. Repeat the previous steps R times to yield a permutation distribution of the test statistic.
Now go back to the observed differene between groups and compare it to the set of permuted differences. If the observed difference lies well within the set of permuted differences, then  we have proven nothing-the observed difference is well within the range of what chance might produce. However, if the observed difference is lies outside most of the permuationdistribution, then we conclude that chance is not responsible. In technical terms, the difference is statistically significant.

- n addition to the preceeding ranomd shuffling procedure, also called random permutation test or a randomization testm there are two variants of permutation testing:
  - Exhaustive permutation test (divide group into all possible permuations instead of random shuffling).
  - bootstrap permutation test (everything same as the random permutation test but with replacement).

## Statistical Significance and p-Values
- Statistical significance is measurement for whether the result is something that was prdocued by chance or for an actual difference in the samples. A result not from chacne is called statistically significant.

#### Key terms:
- p-value: Given a chance model that embodies the null hypothesis, the p-value is the probability of obtaining results as unusual or extreme as the observed results.
- Alpha: The probability threshold of "unusualness" that chance results must surpass for outcomes to be deemed statistically significant. (typically has a value between 1-5%).
- Type-1 error: mistakenly concluding an effect is real (when it is due to chance).
- Type-2 error: mistakenly concluding an effect is due to chance (when it is real).

### P-value experiment
| Outcome |  Price A | Price B  |
|--  | -- |---|
| Conversion | 200 | 182  |
| No conversion | 23,539 | 22,406  |

Price has a conversion rate of 3.6% better than price B. Big enough to be meaningful in a high volume business. With over 45,000 data points in the experiment, it is tempting to consider this as "big data", not requiring tests for statistical significance. Howeverm with conversion rate lower than 1% for each group, the sample size needed is determined by these conversions. In this example we use resampling to test whether the difference in conversion between A and B is truly from the price difference or by chance.
We will model this as an experiment where we ask "If the two prices had the same conversion rate, could chance variation produce a difference as big as 3.6% ?"
##### Experiment Pseudocode:
1. Create cards of 2 categoried 1 and 0. #1 cards should be 382 (200+182) and #0 cards should be 45,945 (23539+22406). This now represents the a scenario where price A and price B had the same exact conversion rate.
2. Shuffle and redraw out a sample of size 23,739 (conversion + no conversion of price A). Record how many 1's (conversions) were in this random sample.
3. Record the number of 1's in the remaining 22,588 (same n as price B).
4. Record the difference in proportion of 1's.
5. Repeat steps 2-4.
6. How often was the difference >= 3.6% ?

The answer to step 6 will be approximately 0.308 or 30.8%, p-value = 30.8%.
This P value can be read as "We would expect to achieve a result as extreme or more extreme as our table above by random chance over 30% of the time.


### t-Tests
### Key terms:
- Test statistic: A metric for the difference or effect of interest.
- t-statistic: A standardized version of common test statistics such as mean.
- t-distribution: A reference distribution (in this case derived from the null hypothesis), to which the observed t-statistic can be compared.

In a resmapling test like permutation test the scale of the data does not matter. You create the reference (null hypothesis) distribution from the data itself and use the test statistic as is. In 1920's and 1930's when statistical hypothesis testing was being developed, it was not feasible to randomly shuffle data thousands of times to do a resampling. Statisticians found that a good approximation to the permutation (shuffled) dsitribution was the t-test, bsed on Gosset's distribution. It is used for the very common two-sample comparison -A/B test- in which the data is numeric. But in order for the t-distribution to be used without regard to scale, a standardized form of the test statistic must be used.


### Multiple Testing Problem
- "Torture data long enough and it will confess"
Let's say you have 20 predictor variables that are randomly generated and one outcome variable. The odds that atleast one of them will falsely turn out to be statistically significant if you do a series of 20 significance tests at alpha set as 5% are pretty good. We can actually calculate it as shown below.
```
P (20/20 predictors will all correctly test as non significant) = 0.95^20 = 0.36
P (1/20 predictors will falsely test as significant) =
 1 - P (20/20 predictors will all correctly test as non significant)
=> 1-0.36 => 0.64 ->64% !!!!!!! oh god thats high!!!
```
This is known as alpha inflation. This problem is also related to overfitting in machine learning. The more variables you add, or the more models you run, the greater the probability that something will emerge as "significant" just by chance.

### Key terms:
- Type 1 error: Mistaken conclusion that an effect is statistically significant.
- False discovey rate: Across multiple tests, the rate of making a type 1 error.
- Alpha inflation: Multiple testing problem, that more tests you run the probability of making your alpha match a type 1 error increases.
- Adjustment of p-values: Accounting for doing multiple tests on the same data.
- Overfitting: Fitting the noise.

In supervised learning tasks, a holdout set where models are assessed on data that the model has not seen before mitigates this risk. Without labeled holdout set risk of conclusions based on noise persists.

Adjustment procedures can compensate for this by setting the bar for statistical more stringently than it would be set for a single hypothesis test. Adjustment procedures typically involve "dividing up the alpha" according to the number of tests.

### Degrees of Freedom
Degrees of freedom is a concept applied to statisics calculated from sample data, and refers to the number of values free to vary. For example, if you know the mean for a sample of 10 values, there are 9 degrees of freedom (once you know 9 of the sample values the 10th value can be calculated and is not allowed to be free to vary).
The concept of degrees of freedom lies behind the factoring of categorical variables into n-1 indicator or dummy vairables when doing regression (to avoid multicollinearity).

### ANOVA
Suppose instead of A/B test, we had a comparison of multiple groups, say A/B/C/D, each with numeric data. The statistical procedure that tests for a statistically significant difference among the groups is called analysis if variance, or ANOVA.

### Key terms:
- Pairwise comparison: Hypothesis test between 2 groups among multiple groups.
- Omnibus test: Single hypothesis test of the overall variance among multiple group means.
- Decomposition of variance: Separation of components contributing to an individual value.
- F-statistic: A standardized statistic that measures the extent to which differences among group means exceed what might be expected in a chance model.
- SS square: Sum of squares, referring to deviations from some average values.

### ANOVA Procedure:
- Let's say we have sample groups A, B, C, D (with n = 5, for each group) and mean for each.
  1. combine all data together in a single box.
  2. Shuffle and draw out four resamples of fives values each
  3. Record mean for each group.
  4. Record variance among the four group means.
  5. Repeat steps 2-4 many (say 1,000) times.

The proportion of time the resampled variance exceed the observed variance is the p-value.

### f-Statistic:
Just like t-test can be used instead of a permutation test for comparing the mean of two groups, there is a statistical test for ANOVA based on the F-statistic.

### Two-Way ANOVA
The A/B/C/D test describes 1 way ANOVA. WE could have a second factor involved - e.g. "weekend vs weekday" with data collected on each combinnation. This would be 2 way anova.

### Chi-Square Test
The chi-square test is used with count data to test how well it fits some expected distribution. The most common use of the chi-square statistic in statistical practice is with r x c contingency tables, to assess whether the null hypothesis of independence among variables is reasonable. Chi-square test can also be used in determining appropriate sample sizes for an experiment.


### Multi-Arm Bandit Algorithm
This algorithm offers an approach to testing, especially web testing, that allows explicit optimization and more rapid decision making than traditional statistical approach to designing experiments.
This algorithm let's you explore and exploit by promoting better performering groups over time.

### Epsilon Greedy Algorithm for an A/B test:
  1. Generete a uniformly distributed random number between 0 and 1.
  2. If the number lies between 0 and epsilon, flip a fair coin and show A if heads, else show B.
  3. If the number is greater than epsilon, show whichever A or B sample group that has had the highest response rate to date.
Epsiolon is the single parameter that governs this algorithm. If epsilon is 1, we end up with a standard simple A/B experiment. If epsilon is 0 we get a purely greedy algorithm.
A more sophisticated algorithm would use Thompson's sampling.
Bandit algorithms can efficiently handle 3+ treatments and move toward optimal selection of the "best". For traditional statistical testing procedures, the complexity of decision making for 3+ treatments far outstrips that of the traditional A/B test, and the advantage of bandit algorithms is much greater.

