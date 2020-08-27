# Carvana_dataset_analysis
Performed Exploratory and Predictive Analysis for Carvana dataset
## Problem: 
Auto dealers purchase used cars at auctions with a plan to sell them to consumers, but sometimes these auctioned vehicles can have severe issues that prevent them from being resold at a profit (hence, lemons)

## Objective: 
The objective is to develop models to predict the outcome variable “BadBuy”, which labels whether a car purchased at an auction was a “bad buy” (lemon). The task is to build a model to guide auto dealerships in their decisions on whether to bid for and purchase a vehicle.

## Solution:

* Logistic regression achieves an accuracy of 66.99%. The coefficient of Age is 0.2785. The exp(0.2785) is 1.32. It indicates, for every one year change in the age of the car, the odds of the car being classified as a lemon increase by 1.32 times while all else held constant. The coefficient of SizeVAN is -0.5982. The exp(-0.598) = 0.549 indicates that the size of car being a VAN makes the odds of a car becoming a lemon approximately 0.549 times than the odds we would have with the baseline case of size while all else held constant. 

* The performance measures for the LDA model are: 
  * Accuracy: 67.23% 
  * Sensitivity: 70.97% 
  * Specificity:64.77% 

  * If we compare the LDA model with logistic regression, logistic model has an accuracy of 67%. There is only a marginal increase in accuracy of LDA with respect to logistic model. This points out that the both the model performs almost similarly for the given data, which is true as the given data is linear. If we compare the sensitivity and specificity of both the models, we can see a kind of tradeoff as LDA model loses out marginally on specificity but gains on sensitivity.

* Performance measures of kNN model are: 
  * Accuracy: 63.79% 
  * Sensitivity: 66.76% 
  * Specificity: 61.86% 

  * For KNN, if we compare it with LDA, the value of all the performance measures have decreased. The value of accuracy has decreased by 4%. It could be inferred that correlation is present in data. The KNN model works generally well with uncorrelated data.

  * The optimal k-value obtained after setting a tunelength of 20 is 43. The model overfits is a small k value is chosen and the model underfits if a large k value is chosen. The optimal value of k would increase the accuracy of model to highest possible value. It could be inferred from the graph that accuracy is different for different k values and it is highest at the optimal value of k i.e. 43.

* The performance measures for the Lasso model are: 
  * Accuracy: 66.94% 
  * Sensitivity: 69.68% 
  * Specificity: 65% 

  * When comparing Lasso with the above models, it could be inferred that Lasso’s performs similar to LDA and Logistic regression. The Lasso model performs better than KNN because the Lasso model considers only the important variables after dropping the insignificant variables.

  * The variable reported by Lasso to have maximum importance is WheelTypeNULL. From domain knowledge, we can infer that wheel type makes sense to be an important variable when we want to make a prediction about the car is lemon or not. The second variable at 36% variable importance is color which is also important for making a prediction because people have preferences about car’s color. Also, applying domain knowledge the odometer reading and the make of car are also important variable, but Lasso has dropped these variables.

* The performance measures for the Ridge model are: 
  * Accuracy: 67.11% 
  * Sensitivity: 69.38%
  * Specificity: 65.43% 

* The performance measure for the Elastic net model are: 
  * Accuracy: 66.94% 
  * Sensitivity: 69.64% 
  * Specificity: 64.94% 

  * Comparing all the three Lasso, Ridge and Elastic Net models, we can infer that Ridge model performs best among the three. It could be seen that ridge performs only marginally better in comparison to other two models, the increase in performance could be understood from the fact that Lasso model drops some variables, and shrink them to zero but ridge doesn’t do shrink variables to zero and near to zero. Also, the specificity for Ridge is the highest.

* The performance statistics of QDA model are: 
  * Accuracy: 63.87% 
  * Sensitivity: 71.92% 
  * Specificity: 60.38% 

  * The QDA model performs better on the sensitivity measure but the LDA model performs better on the accuracy measure. This can be attributed to the rank deficiency error in QDA.

* To predict a lemon using all other variables, we would emphasis on less number of false negatives (specificity), because if model predicts a good car to be a lemon, then there would be loss to the dealer. This metric is the most important and therefore we choose the ridge model which has the highest specificity of 65.43%


