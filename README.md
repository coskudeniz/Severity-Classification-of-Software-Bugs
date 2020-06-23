# Severity-Classification-of-Software-Bugs
Classify a given software bug as severe or non-severe using an unbalanced dataset for training. 

## AIM
The aim is to be able to classify a given software bug description as severe or non-severe. This task is a binary classification task. The chosen model can be used to classifiy bug descriptions automatically. This can further be used as which software bugs should be given high priority and should be resolved before than non-severe bugs. 

## DATA
The dataset consists of 159998 instances. 134586 instances are labelled as non-severe and the remaining 25412 instances are labelled as severe. The data is not distributed evenly between these two labels and is an unbalanced dataset. There 5.3 times more non-severe bugs then severe bugs. Therefore accuracy may not be the best metric to optimize here. If every bug description will be classified as non-severe then an accuracy of 0.84 will be achieved. 

In order to test the usefullness of an ML model compared to a baseline solution that does not use ML, different metrics can be optimized. Instead of accuracy, metrics like F1-Score or Area Under Curve (AUC) can tried to be optimized. Average precision can be another metric to optimize. F1-Score is the harmonic mean of precision and recall. AUC gives the ranking accuracy, which can be seen as an estimate of the probability that an aribitrary chosen positive-negative pair is ranked correctly. Average precision can be thought as the area under the precision-recall curve.

Another option can be to use a portion of the non-severe bugs for training in order to create a more balanced dataset. Another option can be assigning a weight of 1 to the non-severe bugs and assigning a weight of approximately 5.3 to the severe bugs to balance the dataset. Also, another option can be to determine an operating point and then the ML model which will satisfy the condition of the operating point as well as that will achieve good results in other metrics can be chosen. For example, %90 recall rate can be the desired operating condition and all classifiers trained should satisfy this operating condition. Among those classifiers satisfying the operating point condition, the one that achieves better results in other metrics can be chosen for deployment.

## ML MODELS USED
The Scikit-Learn implementation of the following ML models are trained on the dataset:

* Logistic Regression
* SVM
* Bernoulli Naive Bayes
* Multinomial Naive Bayes
* Random Forrest
* Gradient Boosting
* Multilayer Perceptron (Deep Learning)

Except for training the Naive Bayes models, TF-IDF features are used for the input to the models. More detailed information can be found in the notebook provided in this repository. Scapy implementation of lemmatization and stemming from the NLTK library can be integrated with the TF-IDF vectroizer and this notebook shows how to do that. Lemmatization and stemming will mainly be useful if the generalization is the proplem instead of underfitting. 

Finally, the probability estimations of the chosen model will tried to be improved using calibration. There can be two options for calibrating the probabilities of an ML model. 
