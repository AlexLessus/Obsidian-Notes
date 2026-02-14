Tags: [[Aprendizaje Automático]]

# Classification
## Overfitting
- Performs great on training data, 
- Performs poorly on the testing data.
- Model memorized training data and can't generalize learnings to new data
- Use testing set to check model performance
![[Pasted image 20260212235123.png]]
*For instance, the green line here overfits. It's going out of its way to classify all points perfectly, thus performing great on this dataset, but poorly on unseen data. The black line makes more errors on this specific dataset, but generalizes better.*

# how would we measure the model's performance?

## Accuracy
Is the number of correctly predicted observations divided by the number of all observations. *We had 48 correct classifications out of 50, which is a 96% accuracy.*

### Limits
Pueden ocurrir falsos positivos, en el ejemplo hay 90% de precisión pero el modelo puede perder la mayoría de los casos importantes, puede clasificar bien todos los verdaderos positivos pero clasificar muy mal los falsos negativos![[Pasted image 20260213000249.png]]

## Specificity
On the other hand we have specificity, which values true negatives. This is useful metric for spam filters.


---
# Evaluating regression
**==we want the difference between the actual value and the predicted value.==**

This can be the distance between the points and the predicted line. There are many ways to calculate this error, such as root mean square error, but this is the general idea!
![[Pasted image 20260213000534.png]]

# And what about unsupervised learning?
 Unsupervised learning does not have predicted variables, ==so there's no correct output== to compare to. How well your unsupervised learning model performs depends on the problem you're solving. So, you assess the performance based on how well the results advance your initial objective.