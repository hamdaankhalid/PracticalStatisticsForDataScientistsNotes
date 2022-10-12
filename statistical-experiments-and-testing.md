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
