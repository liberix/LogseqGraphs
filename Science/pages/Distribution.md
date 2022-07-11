- # Discrete Distribution
	- ## Binomial Distribution (Bernoulli)
	  collapsed:: true
		- Definition
			- The binomial distribution simulates $n$ number of binary events, such as the left, right choices of the random rat in the T-maze. Imagine that you have done an  experiment and found that your rat turned left in 7 out of 10 trials. 
			  What is the probability of the rat indeed turning left 7 times ($k = 7$)?
			- This is given by the binomial probability of $k$, given $n$  trials and probability $p$:
				- $$
				  \begin{align*}
				  P(k | n, k) &= 
				  \begin{pmatrix}
				  n \\ k 
				  \end{pmatrix}
				  p^k (1-p)^{n-k} \\
				  
				  \begin{pmatrix}
				  n \\ k 
				  \end{pmatrix} &= \frac{n!}{k! (n-k)!}
				  \end{align*}
				  $$
					- $p$ - the probability of (turning left, 硬币正面, etc)
					- $\begin{pmatrix} n \\ k  \end{pmatrix}$ - binomial coeffcients
		- Properties
			- $$
			  \sum_k P(k | n, p) = 1
			  $$
		- Sampling
			-
	- ## Poisson Distribution
		- Definition
			- $$
			  P(x) = \frac{\lambda^x e^{-\lambda}}{x !}
			  $$
				- $\lambda$ parameter corresponding to the average outcome of $x$
		- Usage
			- For [[CompNeuro]]:
				- What is the probability that a neuron within a second will fire $x$ times?
					- Assumes that each spike is independent of the previous one
					- Average firing rate $\lambda$
					- In
- # Continuous Distribution
	- ## Gaussian/Normal Distribution
		- Because of the [central limit theorem](((62c985ed-45b1-4939-b1e1-0f030edf3bb9))), many quantities are Gaussian distributed.
		- Probability Density:
			- $$
			  f(x ; \mu, \sigma^2) = \frac{1}{\sqrt{2 \pi \sigma^2}} exp\bigg(\frac{-(x - \mu)^2}{2 \sigma^2}\bigg)
			  $$
		- Properties:
			- Product of a Gaussian Distributions is a Gaussian distribution
			-