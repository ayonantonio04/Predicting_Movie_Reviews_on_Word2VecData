# **ML Classifier Applications on Word2VecData**

### Introduction 

For this report we will focus on using pre-recorded data to make predictions on whether a review will be positive or negative. To achieve this, we will use multiple machine learning classifiers that will use a text embedding dataset, which is essentially a series of vectors acquired from the word2vec model, and categorize it based on the vector’s specifications. In order to minimize data discrepancies or biases, the data was split into a training and testing set, where we will use the training data to predict the testing data. Some of the classifiers utilized include: K-Nearest Neighbor, Perceptron, Logistic Regression and SVM.

### *Preprocessing Data*
With the use of the function ” readTrainTestData(trainFile, testFile)”, we where able to take the training and testing data files, convert each line to a string and then convert it again to a numerical data type. After the file conversion, loops where used to separate each file into two separate ones, one being the labels and the other word2vec vector. As a result we ended up with four separate datasets: Train_vec, Train_lab(label), Test_vec and Test_lab.
In the case of cross validation, we combined the *vec* and *lab* datasets to form X_val and y_val.

### *K-Nearest Neighbor*
This is a classification algorithm widely used in machine learning. As a supervised model, previous input is needed in order for the algorithm to classify future objects. So based on our model “sentimentClassKNN(train_vec, train_lab, test_vec, test_lab, k, distanceMeasure)” we can get a hint of what is required for the algorithm to work. To break it down, KNN takes multiple labelled data points and then determines the label of a new point based on the proximity of the established points around it. This is a where “k” come into play because it dictates the amount of points it checks before deciding the label.

### *Perceptron*
This is a linear classifier mainly used for binary predictions. The model uses multiple features provided in the data, then creates a threshold between those distinguishing features and predicts whether a new data point belongs to one category or the other. In the case predictions do not match the correct classifications , weights are updated to aim at getting a better approximation of the next target. 

### *Support Vector Machine*
In this case we used SVM as a linear separator. This classifier essentially creates a hyperplane between data points and then takes the minimum distance of each point from either side of the plane and establishes a margin. So looking at it in a 2D plot, there are a total of three linear lines separating the data, two margin lines and one hyperplane in the center. Once these lines have been established, the new data can be labelled.

### *Logistic Regression*
Through the use of the Sigmoid function, logistic regression allows for more accurate classifications among binary variables. Unlike linear regression, this model’s decision boundary contains curved shapes which in many cases does a better job in encompassing specific outliers. 
The result probabilities will also only be within a range of 0 and 1, hence providing a simple visual once plotted.

### *Data* 
As explained in the section above, Preprocessing Data, we started with two text files consisting of training and testing data. The training file has 40000 different vectors consisting 100 decimal values plus one label value at the beginning. The testing file is much smaller with just 10000 different vectors with the same amount of decimal and labeled values in each. Once the preprocessing is done we end up with a numerical list of labels and arrays for each file. Hence, ending up with parameters train_vec, train_lab, test_vec, and test_lab, where each vec is (100,1) and lab  is (1,1) in dimension.  
What do all these numbers inside the vectors mean? 
All this data comes from a model called word2vec. To summarize, the model comes from a twolayer neural network used specifically for text. As we try to get an accurate review prediction, we must know why a specific review is either positive or negative. For this we need context, sentiment, key words…so this is where the word2vec is able to take several words, provide them with a numerical value based on the word’s context and then group vectors that have similar words. If given enough data, this will enable the model to predict the meaning of future words in a sentence because it already has vectors telling it its meaning and usage.
