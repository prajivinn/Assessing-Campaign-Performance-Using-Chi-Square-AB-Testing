# Assessing-Campaign-Performance-Using-Chi-Square-AB-Testing

Project_Link: https://prajivinn.github.io/2022/01/23/chi-square-test.html

## Project Overview

Earlier in the year, our client, a grocery retailer, ran a campaign to promote their new “Delivery Club” - an initiative that costs a customer $100 per year for membership, but offers free grocery deliveries rather than the normal cost of $10 per delivery.

For the campaign promoting the club, customers were put randomly into three groups - the first group received a low quality, low cost mailer, the second group received a high quality, high cost mailer, and the third group were a control group, receiving no mailer at all.

The client knows that customers who were contacted, signed up for the Delivery Club at a far higher rate than the control group, but now want to understand if there is a significant difference in signup rate between the cheap mailer and the expensive mailer. This will allow them to make more informed decisions in the future, with the overall aim of optimising campaign ROI!

## Actions
For this test, as it is focused on comparing the rates of two groups - we applied the Chi-Square Test For Independence. Full details of this test can be found in the dedicated section below.

Note: Another option when comparing “rates” is a test known as the Z-Test For Proportions. While, we could absolutely use this test here, we have chosen the Chi-Square Test For Independence because:

The resulting test statistic for both tests will be the same
The Chi-Square Test can be represented using 2x2 tables of data - meaning it can be easier to explain to stakeholders
The Chi-Square Test can extend out to more than 2 groups - meaning the client can have one consistent approach to measuring signficance
From the campaign_data table in the client database, we isolated customers that received “Mailer 1” (low cost) and “Mailer 2” (high cost) for this campaign, and excluded customers who were in the control group.

We set out our hypotheses and Acceptance Criteria for the test, as follows:

Null Hypothesis: There is no relationship between mailer type and signup rate. They are independent. Alternate Hypothesis: There is a relationship between mailer type and signup rate. They are not independent. Acceptance Criteria: 0.05

As a requirement of the Chi-Square Test For Independence, we aggregated this data down to a 2x2 matrix for signup_flag by mailer_type and fed this into the algorithm (using the scipy library) to calculate the Chi-Square Statistic, p-value, Degrees of Freedom, and expected values

## Results & Discussion
Based upon our observed values, we can give this all some context with the sign-up rate of each group. We get:

Mailer 1 (Low Cost): 32.8% signup rate
Mailer 2 (High Cost): 37.8% signup rate
However, the Chi-Square Test gives us the following statistics:

Chi-Square Statistic: 1.94
p-value: 0.16
The Critical Value for our specified Acceptance Criteria of 0.05 is 3.84

Based upon these statistics, we retain the null hypothesis, and conclude that there is no relationship between mailer type and signup rate.

In other words - while we saw that the higher cost Mailer 2 had a higher signup rate (37.8%) than the lower cost Mailer 1 (32.8%) it appears that this difference is not significant, at least at our Acceptance Criteria of 0.05.

Without running this Hypothesis Test, the client may have concluded that they should always look to go with higher cost mailers - and from what we’ve seen in this test, that may not be a great decision. It would result in them spending more, but not necessarily gaining any extra revenue as a result

Our results here also do not say that there definitely isn’t a difference between the two mailers - we are only advising that we should not make any rigid conclusions at this point.

Running more A/B Tests like this, gathering more data, and then re-running this test may provide us, and the client more insight!
