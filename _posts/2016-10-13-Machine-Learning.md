---
published: true
layout: post
---
## Machine Learning Note

[Statistical Learning](https://lagunita.stanford.edu/courses/HumanitiesSciences/StatLearning/Winter2016/info).


[Machine Learning](https://www.coursera.org/learn/machine-learning/home/welcome)


[CS231n](http://cs231n.github.io/)
 Convolutional Neural Networks for Visual Recognition
 
 
 [machine-learning-toolbox](https://campus.datacamp.com/courses/machine-learning-toolbox/regression-models-fitting-them-and-evaluating-their-performance?ex=2)
 
 
##### In-sample RMSE for linear regression

RMSE is commonly calculated in-sample on your training set. What's a potential drawback to calculating training set error?

You have no idea how well your model generalizes to new data (i.e. overfitting).


##### Introducing out-of-sample error measures


Out-of-sample RMSE for linear regression

What is the advantage of using a train/test split rather than just validating your model in-sample on the training set?

It gives you an estimate of how well your model performs on new data.


##### Randomly order the data frame

One way you can take a train/test split of a dataset is to order the dataset randomly, then divide it into the two sets. This ensures that the training set and test set are both random samples and that any biases in the ordering of the dataset (e.g. if it had originally been ordered by price or size) are not retained in the samples we take for training and testing your models. You can think of this like shuffling a brand new deck of playing cards before dealing hands.

First, you set a random seed so that your work is reproducible and you get the same random split each time you run your script:

set.seed(42)

Next, you use the sample() function to shuffle the row indices of the diamonds dataset. You can later use these these indices to reorder the dataset.

rows <- sample(nrow(diamonds))

Finally, you can use this random vector to reorder the diamonds dataset:

diamonds <- diamonds[rows, ]


##### Try an 80/20 split

Now that your dataset is randomly ordered, you can split the first 80% of it into a training set, and the last 20% into a test set. You can do this by choosing a split point approximately 80% of the way through your data:

split <- round(nrow(mydata) * .80)
You can then use this point to break off the first 80% of the dataset as a training set:

mydata[1:split, ]
And then you can use that same point to determine the test set:

mydata[(split + 1):nrow(mydata), ]



##### Predict on test set

Now that you have a randomly split training set and test set, you can use the lm() function as you did in the first exercise to fit a model to your training set, rather than the entire dataset. Recall that you can use the formula interface to the linear regression function to fit a model with a specified target variable using all other variables in the dataset as predictors:

mod <- lm(y ~ ., training_data)
You can use the predict() function to make predictions from that model on new data. The new dataset must have all of the columns from the training data, but they can be in a different order with different values. Here, rather than re-predicting on the training set, you can predict on the test set, which you did not use for training the model. This will allow you to determine the out-of-sample error for the model in the next exercise:

p <- predict(model, new_data)



##### Calculate test set RMSE by hand

Now that you have predictions on the test set, you can use these predictions to calculate an error metric (in this case RMSE) on the test set and see how the model performs out-of-sample, rather than in-sample as you did in the first exercise. You first do this by calculating the errors between the predicted diamond prices and the actual diamond prices by subtracting the predictions from the actual values.

Once you have an error vector, calculating RMSE is as simple as squaring it, taking the mean, then taking the square root:

sqrt(mean(error^2))





##### Comparing out-of-sample RMSE to in-sample RMSE

Why is the test set RMSE higher than the training set RMSE?

Because you overfit the training set and the test set contains data the model hasn't seen before.


#### Cross-validation