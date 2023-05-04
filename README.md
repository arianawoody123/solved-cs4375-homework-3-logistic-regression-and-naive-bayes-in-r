Download Link: https://assignmentchef.com/product/solved-cs4375-homework-3-logistic-regression-and-naive-bayes-in-r
<br>
In this homework you will create an R script to run logistic regression and naive bayes on the BreastCancer data set, which is part of package mlbench.

<h1>BreastCancer Data</h1>

If you type “?BreastCancer” at the console after loading package mlbench, you will see that this data has been collected clinically and reported in a paper by Wolberg and Mangasarian, “Multisurface method of pattern separation for medical diagnosis applied to breast cytology”, published in 1990 in the National Academy of Sciences.

Instructions:

<ol>

 <li>Start with a new Rstudio Rmd file, add headings for Homework 3, your name and a brief description of the purpose of the script. Clearly label each step. Each step should have one or more R code chunks. For step 1, load library mlbench, installing if needed (at the console). You have to load the data frame into memory with data(BreastCancer) Now run str() and head() on BreastCancer and summary() on just the Class column. Use R instructions to calculate the percent in each class, and print them with an appropriate heading using paste(). Answer the questions in step 1:

  <ol>

   <li>How many instances are there?</li>

   <li>What is your target column?</li>

   <li>How many predictors are there? What type of data are the predictors?</li>

   <li>What percentage of the observations are malignant?</li>

  </ol></li>

 <li>size and Cell.shape are in one of 10 levels. Build a logistic regression model called glm0, where Class is predicted by Cell.size and Cell.shape. Do you get any error or warning messages? Google the message and try to decide what happened. Run summary on glm0 to confirm that it did build a model. Write a comment about why you think you got this warning message and what you could possibly do about it. List the source of your information in a simple markdown link.</li>

 <li>Notice in the summary() of glm0 that most of the levels of Cell.size and Cell.shape became predictors and that they had very high p-values. We would need a lot more data to build a good logistic regression model this way. It might be better to just have 2 levels for each variable. In this step, add two new columns to BreastCancer as listed below.  Run summary() on Cell.size and Cell.shape as well as the new columns. Comment on the distribution of the new columns. Do you think what we did is a good idea? Why or why not?

  <ol>

   <li>small which is a binary factor that is 1 if Cell.size==1 and 0 otherwise</li>

   <li>regular which is a binary factor that is 1 if Cell.shape==1 and 0 otherwise</li>

  </ol></li>

 <li>Create conditional density plots using the original Cell.size and Cell.shape. First attach() the data to reduce typing. Then use par(mfrow=c(1,2)) to set up a 1×2 grid for two cdplot() graphs with Class~Cell.size and Class~Cell.shape. Observing the plots, write a sentence or two comparing size and malignant, and shape and malignant. Do you think our cutoff points for size==1 and shape==1 were justified now that you see this graph? Why or why not?</li>

 <li>Create plots (not cdplots) with our new columns. Again, use par(mfrow=c(1,2)) to set up a 1×2 grid for two plot() graphs with Class~Cell.small and Class~Cell.regular. Now create two cdplot() graphs for the new columns. Now compute the following and provide a summary in the text portion of this answer. Also indicate based on these results if you think small and regular will be good predictors.

  <ol>

   <li>calculate the percentage of small observations that are malignant</li>

   <li>calculate the percentage of not-small observations that are malignant</li>

   <li>calculate the percentage of regular observations that are malignant</li>

   <li>calculate the percentage of non-regular observations that are malignant</li>

  </ol></li>

 <li>Randomly divide BreastCancer into two data sets: train (80% of the data) and test (20%). Make sure you first set the seed to 1234 so you get the same results as others.</li>

 <li>Build a logistic regression classifier to estimate the probability of Class given Cell.small and Cell.regular. Run summary() on your model. Answer the following:

  <ol>

   <li>Which predictor(s) seem to be good predictors. Justify your answer.</li>

   <li>Comment on the Null deviance versus the Residual deviance.</li>

   <li>Comment on the AIC score.</li>

  </ol></li>

 <li>Test the model on the test data and compute accuracy. What percent accuracy did you get? Output the confusion matrix and related stats using the confusionMatrix() function in the caret package.  Where the mis classifications more false positives or false negatives?</li>

 <li>Your coefficients from the model are in units of logits. Extract the coefficient of small with glm1$coefficients[]. Answer the following questions:

  <ol>

   <li>What is the coefficient?</li>

   <li>How do you interpret this value?</li>

   <li>Find the estimated probability of malignancy if Cell.small is true using exp().</li>

   <li>Find the probability of malignancy if Cell.small is true over the whole BreastCancer data set and compare results. Are they close? Why or why not?</li>

  </ol></li>

 <li>Build two more models, each just using Cell.small and Cell.regular and use anova(glm_small, glm_regular, glm1) to compare all 3 models, using whatever names you used for your models. Analyze the results of the anova(). Also, compare the 3 AIC scores of the models. Feel free to use the internet to help you interpret AIC scores.</li>

 <li>Build a Naive Bayes Model Class ~ Cell.small + Cell.regular on the training data using library e1071. Output the model parameters and answer the following questions:

  <ol>

   <li>What percentage of the training data is benign?</li>

   <li>What is the likelihood that a malignant sample is not small?</li>

   <li>What is the likelihood that a malignant sample is not regular?</li>

  </ol></li>

 <li>Predict on the test data with naive bayes model. Compute the accuracy and output the confusion matrix. Are the results the same or different? Why do you think that is the case?</li>

</ol>