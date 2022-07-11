- # What is Machine Learning
	- Arthur Samuel (1959) - Informal  and older
	  
	  > Field of study that gives computers the ability to learn without being explicitly programmed
	- Tom Michelle (1989) - Modern
	  collapsed:: true
	  
	  > A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E
		- ### Example: playing checkers
		  * E = the experience of playing many games of checkers
		  * T = the task of playing checkers.
		  * P = the probability that the program will win the next game.
		- ### Example: email spam
		  * T ⇒ classifying emails as spam or not spam
		  * E ⇒ watch you as label emails as spam or not spam
		  * P ⇒ The number (or fraction) of emails correctly classified as spam/not spam
- # Classification
  collapsed:: true
	- ## Supervised Learning
		- In *supervised learning*, we are given a data set and **already know** what our correct output should look like, having the idea that there is a relationship between the input and the output.
		  
		  Supervised learning problems are categorized into "regression" and "classification" problems.
		- #### Regression
			- regression -  **continuous** value output 
			  i.e. house price, etc
			- trying to predict results within a continuous output, meaning that we are trying to map input variables to some continuous function.
		- #### Classification
			- classification - discrete value ouputed (0, 1, wheaher hacked)
			- trying to predict results in a discrete output. In other words, we are trying to map input variables into discrete categories.
			- SVM - Math trick to deal with inifite features that might influence learning algorithms
	- ## Unsupervised Learning
		- Given the data and we do not know what results would be like. We can derive this structure by **clustering** the data based on relationships among the variables in the data.
		- With unsupervised learning there is no feedback based on the prediction results.
		- Examples:
		  1. Clustering: Take a collection of 1,000,000 different genes, and find a way to automatically group these genes into groups that are somehow similar or related by different variables, such as lifespan, location, roles, and so on.
		  2. Non-clustering: The "Cocktail Party Algorithm", allows you to find structure in a chaotic environment. (i.e. identifying individual voices and music from a mesh of sounds at a [cocktail party](https://en.wikipedia.org/wiki/Cocktail_party_effect)).
		-
- # Algorithms & Methods
	- [[Linear Regression with One Variable]]
	-