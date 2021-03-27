---
layout: post
tags:
- deeplearning
- machinelearning
categories: Machine Learning
title: Cross Entropy Loss
description: Cross Entropy Loss
---
<br/>

# Cross Entropy Loss

In a supervised learning problem for predicting classes, we predict probabilities for the classes. To determine how successful we are predicting the classes, we require a `loss function`.    

**Cross-Entropy loss** function provides a loss function to calculate the loss between the actual classes and the predicted probabilities     

This can be represented as 

1. Get the predicted probability of the class
2. Get the actual label of the class ( `1 or 0` )
3. Multiply the `actual label` with the `log of the predicted probability` of the class
4. Sum the values obtained from each of the classes  
5. Multiply by -1 the value obtained in Step 4

This is the loss for a single observation. Therefore to calculate the **total** loss for a set of observations, we need to sum all the losses of the observations. Therefore to calculate the **average** loss for a set of observations, we need to average the losses of the observations.

Let's take an example. We develop a fruit prediction model which predicts whether the fruit is orange, apple or guava.   

The results are as follows

| #  | Actual Label  | Predicted Probability | Log Predicted Probability |     
| ------------- | ------------- | ------------- | ------------- |    
| 1| Orange  | 0.9  | log(0.9)  |    
| 2| Apple | 0.6  | log(0.6)   |    
| 3| Guava  | 0.7  | log(0.7)   |    
| 4| Apple | 0.4  | log(0.4)   |      

    
    
Total loss is therefore -1 * ( log(0.9) + log(0.6) + log(0.7) + log(0.4) )   


Let's go deeper for the 1st row. `Here the fruit is orange`. Therefore the class label for the orange is 1 and the class labels for apple and guava are 0 and 0. Therefore the cross-entropy loss would be        

-1 * [1 * Log ( Predicted Probability of Orange ) +   
0 *  Log ( Predicted Probability of Apple ) +  
0 *  Log ( Predicted Probability of Guava )]    
= -1 *Log ( Predicted Probability of Orange )

* When the predicted probability is closer to 1, the loss is lower since **log(1) = 0**   
* When the predicted probability is closer to 0, the loss is higher   

Therefore, **better predictions** produces a lower loss.     

# Code   

<br/>

We checked the concepts by using Keras and using our concepts from 1st principles. Please also try it in your favorite environment.

## Example 1      
       
<br/>   

In this example, we have a single observation with 3 classes. We checked with Keras and from 1st principles, our results match.

```python
import tensorflow as tf
import numpy as np
```

```python
y_true = [[0, 1, 0]]
y_pred = [[0.05, 0.9, 0.05]]
cce = tf.keras.losses.CategoricalCrossentropy()
print(f'cce from keras ',cce(y_true, y_pred).numpy())
print(f'cce from first principles ',-1 * round(np.log(0.9),9))
```

## Example 2
<br/>   

In this example, we have  3 observations with 3 classes. We see that we had to average the losses and our results match perfectly with the Keras function.

```python
y_true = [[0, 1, 0],[1, 0, 0],[0, 0, 1]]
y_pred = [[0.05, 0.9, 0.05],[0.7, 0.2, 0.1],[0.2, 0.2, 0.6]]
cce = tf.keras.losses.CategoricalCrossentropy()
print(f'cce from keras ',cce(y_true, y_pred).numpy())

sum = -1 * (np.log(0.9) + np.log(0.7) + np.log(0.6))

print(f'cce from first principles ',sum / 3)
```
## Kaggle Notebook  Link 

<br/>   

[Cross Entropy Kaggle Notebook](https://www.kaggle.com/ambarish/crossentropy)

