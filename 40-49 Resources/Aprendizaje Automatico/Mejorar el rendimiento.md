Tags [[Aprendizaje Automático]]

# Dimensionality reduction
A dimension denotes the number of features in your data, so dimensionality reduction essentially means **reducing the number of features.**

![[Pasted image 20260213001300.png]]
*For example, if we're trying to predict how long it will take us to go to the office, the time of day and the weather are interesting, but how many glasses of water we drank yesterday is unlikely to be very useful.*

![[Pasted image 20260213001440.png]]


## Hyperparameter tuning
A machine learning model is like a music production console. Depending on whether you're mixing
Some settings will sound better with certain genres than others.

In our case the genre is the dataset and the instruments settings are the hyperparameters. Depending on your dataset, different hyperparameter values will give better or inferior results.

![[Pasted image 20260213001650.png]]
we switched from a straight line to a curved one. That's because we tuned the hyperparameter "kernel" from "linear" to "polynomial".

There are many more hyperparameters that can be tuned in the SVM model. Playing with different values for each hyperparameter will impact our model's performance. You don't have to just guess combinations at random, there are structured ways to [[find the optimal values]] 



# Ensemble methods
This is a technique that combines several models in order to produce one optimal model.

Imagine we're using three different models: models A, B and C. In a classification setting, we would use voting. If Model A and C say the student is accepted, and model B says she's not, then the observation is accepted, as it was the most common prediction amongst all models.![[Pasted image 20260213001932.png]]

In a regression setting, we use averaging. If Model A predicts a temperature of 5, Model B a temperature of 8, and Model C a temperature of 4, the observation gets assigned the average value, 5.67 degrees.

![[Pasted image 20260213002015.png]]