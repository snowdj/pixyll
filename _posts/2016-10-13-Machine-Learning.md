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



Advantage of cross-validation

What is the advantage of cross-validation over a single train/test split?

It gives you multiple estimates of out-of-sample error, rather than a single estimate.




##### 10-fold cross-validation

As you saw in the video, a better approach to validating models is to use multiple systematic test sets, rather than a single random train/test split. Fortunately, the caret package makes this very easy to do:

model <- train(y ~ ., my_data)

caret supports many types of cross-validation, and you can specify which type of cross-validation and the number of cross-validation folds with the trainControl() function, which you pass to the trControl argument in train():

model <- train(
  y ~ ., my_data,
  method = "lm",
  trControl = trainControl(
    method = "cv", number = 10,
    verboseIter = TRUE
  )
)
It's important to note that you pass the method for modeling to the main train() function and the method for cross-validation to the trainControl() function.



##### 5-fold cross-validation
100xp
In this course, you will use a wide variety of datasets to explore the full flexibility of the caret package. Here, you will use the famous Boston housing dataset, where the goal is to predict median home values in various Boston suburbs.

You can use exactly the same code as in the previous exercise, but change the dataset used by the model:

model <- train(
  medv ~ ., Boston,
  method = "lm",
  trControl = trainControl(
    method = "cv", number = 10,
    verboseIter = TRUE
  )
)
Next, you can reduce the number of cross-validation folds from 10 to 5 using the number argument to the trainControl() argument:

trControl = trainControl(
  method = "cv", number = 5,
  verboseIter = TRUE
)


##### 5 x 5-fold cross-validation

You can do more than just one iteration of cross-validation. Repeated cross-validation gives you a better estimate of the test-set error. You can also repeat the entire cross-validation procedure. This takes longer, but gives you many more out-of-sample datasets to look at and much more precise assessments of how well the model performs.

One of the awesome things about the train() function in caret is how easy it is to run very different models or methods of cross-validation just by tweaking a few simple arguments to the function call. For example, you could repeat your entire cross-validation procedure 5 times for greater confidence in your estimates of the model's out-of-sample accuracy, e.g.:

trControl = trainControl(
  method = "cv", number = 5,
  repeats = 5, verboseIter = TRUE
)

##### Making predictions on new data

Finally, the model you fit with the train() function has the exact same predict() interface as the linear regression models you fit earlier in this chapter.

After fitting a model with train(), you can simply call predict() with new data, e.g:

predict(my_model, new_data)

























