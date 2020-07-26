---
layout: "wrapper"
title:  "Review on Probability theory"
categories: OEDS
---

Probability theory is a branch of mathematics which draws a numerical description of how likely an event or a proposition is. It is often used in statistics to draw conclusions from data in inferential statistics. Main subjects are: random variables, probability distributions and stochastic processes. In this post we will review the basics of probability theory that will be needed for the following posts about optimal estimation.

## General definitions
There are some definitions that have to be clear when studying probability theory. The first one is the **experiment**, from which it can be obtained a number of outcomes and involves 3 main concepts:
* The set composed by all of the outcomes is called the **sample space**, let's define it by <span>&Omega;</span>. A **trial** is the act of randomly drawing a single **outcome** w<sub>i</sub> <span>&isin; &Omega;</span>.
* A set '*A*' of certain subsets (that accomplishes the rules of a Borel set) of <span>&Omega;</span> is called the **event space** and each subset <span>&alpha; &isin; &Omega;</span> is an **event**, the empty subset <span>&empty;</span> represents the **impossible event**. 
* A real function P(<span>&alpha;</span>) defined on A is called the **probability** of an event and satisfies the axioms:
    1. P(<span>&alpha;</span>) <span>&ge;</span> 0
    1. P(<span>&Omega;</span>) = 1
    1. If <span> &alpha;, &beta; &isin; A  and &alpha; &cap; &beta; = &empty;, then P(&alpha; &cup; &beta;) = P(&alpha;) + P(&beta;)</span>  

Note: <span>&cup;: union, &cap;: intersection</span>.

## Random variables
A random variable <u>x</u>(w) is a variable which output depends on a random phenomenon (which by definition means that we can’t predict its output). They are supposed to pertain to a bigger population and their results are usually used to obtain information from the larger population. In the Bayesian interpretation of probability (which will be explained [later](#bayesian-interpretation-of-probability)) we will use them to predict the values of unknown parameters. Using the definitions stated in the previous section we can define a random variable as a map from the sample space <span>&Omega;</span> to a set of numbers, for example the real numbers i.e. <span><u>x</u>: &Omega; &#8594; &#8477;</span>. 

We can divide random variables in 2 groups:

**Discrete**: The output is taken from a given finite set. For instance, if we have a class full of students we can define a random variable X for the genre of the students i.e.: x = 0 if a student is male and x = 1 if the student is female. Note that 1 and 0 were values selected just for convenience, it could be any pair of numbers, but these just feel natural.

**Continuous**: The output pertains to the real numbers. Taken the example of the class a possible continuous random variable would be the height of the students.

## Quick review on moments
A moment is a specific quatitative measure of the shape of a function. This concept it is both used in mechanics and in statistics. If the function is a probability distribution the **moment of order n** of a random variable is defined by:

| E[x<sup>n</sup>] = <span style= "font-size:20px;">&#8747;</span><sub style= "font-size:10px;">x=-&infin;</sub> <sup style= "font-size:10px; position: relative; bottom: 10px; right: 20px;">&infin;</sup>  x<sup>n</sup> p(x) dx

Note: The notation should be <u>x</u> for the random variable, but if there is no ambiguity the underscore is omited.

The zero order moment is the total probability, the first order is the expected value or mean value and is often denoted by <span>&mu;<sub>x</sub> or by &mu;</span> for simplicity.

The **central moments** are defined by: 

| E[(x - <span>&mu;</span>)<sup>n</sup>] = <span style= "font-size:20px;">&#8747;</span><sub style= "font-size:10px;">x=-&infin;</sub> <sup style= "font-size:10px; position: relative; bottom: 10px; right: 20px;">&infin;</sup>  (x - <span>&mu;</span>)<sup>n</sup> p(x) dx

The first order central moment is 0 and the second order central moment is the **variance** <span>&sigma;</span><sup>2</sup> and it can be extended as Var[x] = E[(x - <span>&mu;</span>)<sup>2</sup>] = E[x<sup>2</sup>] - <span>&mu;</span><sup>2</sup>. The **standard deviation** is defined as <span>&sigma;</span><sub>x</sub> = sqrt(Var[x]). It can also be defined the **standarized moments** by dividing by the n order variance.

| <span>&mu;<sub>n</sub>/&sigma;<sup>n</sup> = E[(x - &mu;)<sup>n</sup>]/&sigma;<sup>n</sup></span>

The third standarized moment is the [skewness](https://en.wikipedia.org/wiki/Skewness) and the fourth one is the [kurtosis](https://en.wikipedia.org/wiki/Kurtosis).

## Probability distributions
A probability distribution is the mathematical function that gives the probabilities of different possible outcomes for an experiment. It has a sample space <span>&Omega;</span> as its input, and gives a probability as its output. 

There is some terminology that it is important to know of probability distributions depending on the type of variables that you are working with, discrete or continous: 

### Terminology for Discrete variables: 
* **Probability mass function (PMF)**: function that gives the probability that a discrete random variable is equal to some value.
* **Cumulative distribution function (CDF)**: function evaluating the probability that X will take a value less than or equal to x for a discrete random variable.

### Terminology for Continous variables:
* **Probability density function (PDF)**: function whose value at any given sample w in the sample space <span>&Omega;</span> can be interpreted as providing a relative likelihood that the value of the random variable would equal that sample.
* **Cumulative distribution function (CDF)**: function evaluating the probability that X will take a value less than or equal to x for continuous variable.

### Discrete probability distribution
Given a finite sample space <span>&Omega;</span> composed by all the possible outcomes of an experiment, and an element x <span>&isin; &Omega;</span>, it is assumed that for each element there is an intrinsic probability value assigned to it, and follows the properties:
1. f(x) <span>&isin;</span> [0, 1] for all x <span>&isin; &Omega;</span>.  

1. <span><summatory idb ="" id="x𝜖Ω">&Sigma;</summatory></span> f(x)=1.

The function f(x) that assigns each point in the discrete sample space to its probability value is the probability mass function (PMF). It exists also a CDF represented as: F<sub><u>x</u></sub>(x) = P(<u>x</u> <span>&le;</span> x) which gives the probability of a random variable <u>x</u> of taking the values less or equal to a independent variable x.

### Continous probability distribution
On the other hand, given a continous sample space <span>&Omega;</span>', if this one is the set of real numbers ℝ or a subset of it, there exists a cumulative distribution function (CDF) 'F', which is defined by F<sub><u>x</u></sub>(x) = P(<u>x</u> <span>&le;</span> x), which corresponds to the probability of the random variable <u>x</u> to be less or equal to an independent variable x, which can be manually set. In this case the CDF satisfies the properties:

1. F is monotonically non-decreasing and right-continuous.
  
1. <span><summatory idb ="" id="x→-∞" style= "font-size:16px;">lim</summatory></span> F(x) = 0;
  
1. <span><summatory idb ="" id="x→∞" style= "font-size:16px;">lim</summatory></span> F(x) = 1;

If F is absolutely continuous (if you take the derivative and integrate it, you obtain the same CDF) then the random variable has a probability density function (PDF) which it is the derivative of the CDF, expressed as: f(x) = dF(x)/dx.

For a set E <span>&sube;</span> ℝ (a subset of ℝ, here <span>&sube;</span> represents that all the elements of E are included in ℝ), the probability of the random variable <u>x</u> to be in E is defined as: 

P(<u>x</u> <span>&isin;</span> E) = <span style= "font-size:20px;">&#8747;</span><sub style= "font-size:10px;">x&isin;E</sub> dF(x)

If the probability density function exists the it can be defined as: 

P(<u>x</u> <span>&isin;</span> E) = <span style= "font-size:20px;">&#8747;</span><sub style= "font-size:10px;">x&isin;E</sub> f(x) dx

Note: PDF only exists for continuous random variables but, the CDF exists for all random variables (even the discrete ones) that take values in ℝ.

Given a random variable <u>x</u> and an independent variable x, the distribution function F<sub><u>x</u></sub>(x)

## Clasical probability distributions
### Discrete distributions
#### Poisson distribution
The Poisson distribution expresses the probability of a given number of events ocurring in a fixed interval of time or space if the mean rate is known. The discrete random variable <u>n</u> will follow the distribution:

<table class="inline">
<td>
P(<u>n</u> = n) =
</td>
<td>
<div class="n">&lambda;<sup>n</sup> exp(-&lambda;)</div><div class="d">n!</div>
</td>
</table>

Where <span>&lambda;</span> is a parameter of the distribution and represents the expected number of events (the mean), E[n] = <span>&lambda;</span>. A special characteristic of the Poisson distribution is that the mean and the variance are equal: Var[n] = E[n] = <span>&lambda;</span>.

#### Binomial distribution
The binomial distribution gives the probability of the successes of n independen experiments which outputs are yes or no. The probability of the positive outcome is denoted by P (and the negative 1-P) and the total number of times the experiment is repeated (the total number of outcomes) is denoted by N. The probability of discrete random variable <u>n</u> is:

<table class="inline">
<td>
P(<u>n</u> = n) =
</td>
<td>
<div class="n">N!</div><div class="d">n! (N - n)!</div>
</td>
<td>
P<sup>n</sup> (1 - P)<sup>N-n</sup> 
</td>
</table>

The expectation of <u>n</u> is E[<u>n</u>] = NP and its variance Var[<u>n</u>] = NP(1-P).

### Continous distributions
#### Normal distribution 
The normal distribution is the one which the probability function is denoted by a gaussian:

<table class="inline">
<td>
p(x) =
</td>
<td>
<div class="n">1</div><div class="d">&sigma; sqrt(2&pi;)</div>
</td>
<td>
exp(
</td>
<td>
<div class="n">-(x - &mu;)<sup>2</sup></div><div class="d">2 &sigma;<sup>2</sup></div>
</td>
<td>
)
</td>
</table>

This probability function is very famous, partly due to the **central limit theorem** in probability theory, which states that under some conditions the average of many samples of a random variable with finite mean and variance is itself a random variable whose distribution converges to a normal distribution as the number of samples increases. Therefore physical quantities that are expected to be the sum of many independent processes are described by this distribution, i.e the noise of a system or the measurement errors.

The parameters of this distribution are <span>&sigma;<sup>2</sup> and &mu;</span>, which are the variance and the expectation

#### Chi-square distribution
A random variable y is said to be <span>&chi;<sub>n</sub><sup>2</sup></span> distributed (Chi-square distributed with n degrees of freedom) if its density function is:

<table class="inline">
<td>
p(y) = 
</td>
<td>
    <blockquote>
    <table class="inline">
        <tr>
            <td>
                <div class="n">1</div><div class="d">2<sup>n/2</sup>&Gamma;(n/2)</div>
            </td>
            <td>
                <sup style= "position: relative; right: 15px; bottom: 15px;">y <sup>n/2-1</sup> e <sup>y/2</sup></sup>
            </td>
            <td>
                y &ge; 0
            </td>
        </tr>
        <tr>
            <td>0</td>
            <td>elsewhere</td>
        </tr>
    </table>
    </blockquote>
</td>
</table>

Where <span>&Gamma;</span>() is the gamma function, and the expectation and variance of a Chi-square distributed random variable is E[y] = n and Var[y] = 2n. This is the distribution of a sum of the squares of n independent standard normal (normal distributed with <span>&mu; = 0 and &sigma; = 1</span>) random variables. This distribution is widely used in inferential statistics, in [hypothesis testing](https://en.wikipedia.org/wiki/Statistical_hypothesis_testing) and in the construction of [confidence intervals](https://en.wikipedia.org/wiki/Confidence_interval).

## Bayesian interpretation of probability
There are different interpretations of probability depending in which branch of statistics you are (objectivism or subjectivism). For this post and for the ones that follow we will consider the Bayessian interpretation of probability, which it is part of the subjectivist interpretation. 

The main difference between Bayesians and frequentists (the most popular version of objectivism) is that Bayesians can consider an unknown variable that is known to be fixed as a random variable. Whereas frequentists say that only by the fact of not knowing much of that variable is not suficient to say that is random, in other words, a variable can not be at the same time random and fixed. 

Bayesian methodology starts by setting what is called a "prior distribution" that represents the prior knowledge of the event/object, and uses real measurements to update this knowledge and obtain the "posterior distribution" using Bayes' law. The posterior distribution can be used later on as the prior distribution to further improve the knowledge.

#### References:  
* F. van der Heijden et al: Classification, Parameter Estimation and State Estimation - An Engineering Approach using MatLab, J. Wiley & Sons, 2004, or 2nd edition, 2017.  
* https://en.wikipedia.org/wiki/Random_variable  
* https://en.wikipedia.org/wiki/Statistics  
* https://en.wikipedia.org/wiki/Probability  
* https://en.wikipedia.org/wiki/Bayesian_statistics   
* https://en.wikipedia.org/wiki/Bayesian_probability  
* https://www.stat.auckland.ac.nz/~brewer/stats331.pdf  
* https://egertonconsulting.com/a-comparison-of-classical-and-bayesian-statistics  
* https://en.wikipedia.org/wiki/Probability_distribution  
* https://en.wikipedia.org/wiki/Normal_distribution  
* https://en.wikipedia.org/wiki/Binomial_distribution  
* https://en.wikipedia.org/wiki/Chi-square_distribution  
* https://en.wikipedia.org/wiki/Poisson_distribution  