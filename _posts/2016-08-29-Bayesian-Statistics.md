---
published: true
layout: post
---
## Bayesian Statistics

[Bayesian Statistics](https://www.coursera.org/learn/bayesian/home/welcome/). 


Bayesian Statistics
by Duke University


[Bayesian Statistics](https://www.coursera.org/learn/bayesian-statistics)

Herbie Lee, Professor of Statistics at the University of California Santa Cruz. 

way to define probabilities is under Bayesian perspective. Bayesian perspective is one of personal perspective.



###

[Bios8366](https://github.com/fonnesbeck/Bios8366/tree/master/notebooks)

[Bayesian-biostatistics-2015](https://github.com/petrkeil/Bayesian-biostatistics-2015)
[STA663-2015](https://github.com/Sta523-Fa14/STA663-2015)
[Bayes](https://github.com/jkarreth/Bayes)


####　minimizing loss functions

summary

‣ L0 minimized at mode 

‣ L1 minimized at median 

‣ L2 minimized at mean

‣ point estimate you report depends on your choice of loss function



#### posterior probabilities & decision

‣ suppose you have two competing hypotheses: H1 and H2

‣ then

‣ P(H1 is true | data) = posterior probability of H1 

‣ P(H2 is true | data) = posterior probability of H2

‣ potential decision criterion: choose the hypothesis with the higher posterior probability

reject H1 if P(H1 is true | data) < P(H2 is true | data) 

‣ alternative: consider a loss function



#### loss functions & decisions

‣ L(d) : loss that occurs when decision d is made 

‣ Bayesian testing procedure then minimizes the posterior expected loss

‣ possible decisions (actions): 

‣ d1 : choose H1 - decide that the patient doesn’t have HIV


‣ d2 : choose H2 - decide that the patient has HIV


#### summary

‣ Bayesian methodologies allow for the integration of losses into the decision making framework easily

‣ in Bayesian testing we minimize the posterior expected loss


#### Bayes factor

‣ quantifies the evidence of data arising from H1 vs. H2 

‣ discrete case: ratio of the likelihoods of the observed data under the two hypotheses

‣ continuous case: ratio of the marginal likelihoods

####　interpreting the Bayes factor BF[H1 : H2]

Jeffreys (1961) Evidence against H2

1 to 3 　Not worth　a bare mention 　

3 to 20　Positive



30 to 150 Strong

> 150　 Very strong



#### summary 
‣ inference with paired or matched normal samples

‣default prior distributions under the two hypotheses

‣posterior distributions for proportions under H2

and H1 

#### pooled prior distributions under H1 p(p) / pam

‣ Bayes factor for comparing H1 to H2 is 2.93

‣ slight evidence in favor of H1 but not “worth a bare mention”
