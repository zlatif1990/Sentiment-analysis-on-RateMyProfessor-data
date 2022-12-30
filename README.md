# Sentiment-analysis-on-RateMyProfessor-data
Sentiment analysis on RateMyProfessor data 

Data
Initially we had a vast amount of raw data where we see many students who took courses leave review and ratings about their professor by professor’s name and the institution from ratemyprofessor.
com He (2020). There is total 51 columns. Some columns state their opinion such as rating, whether they would like to retake the course, comments etc. Then some data about professor’s demand,
course load, instructor behavior and grading. Our major column is “comment” which will be our input text analysis. Our target column is the ’student_star’ which was relabeled into 3 major
categories. As we are forming a text classification of the comment, we already got the rating of the professor into 3 (three) categories. Good, bad, and average. Here total
number of good, bed and average review is 11814, 4764 and 3415. We have analyzed the frequency of these three categories and the majority belongs to good review category.

Data preprocessing
On data preprocessing we have used some methods to make the data properly trainable by our system. Some of the preprocessing are like converting to lowercase. removing punctuation’s and
characters, removing stop words, cut down word stemming( removing -ing, -ly), lemmatisation etc. This process is integrated with tokenization of the dataset.Tokenization is the process of changing sensitive
data to non-sensitive data for machine learning process without bringing it into scope. After this process the data is called "tokens". This process converts the data from string to list. Each
token is given unique identifying number. This task is important for Natural Language Processing (NLP) applications like summarization, context understanding, and question-answering.

Evaluation method
Accuracy, Precision, Confusion matrix, ROC and Recall will be used as the different evaluation metrics to evaluate the performance. The accuracy will indicate the portion of correct predictions by the
model. Precision will indicate the ratio of correct instances against retrieved instances. The confusion matrix will display a the correct and incorrect predictions made by the model in a tabular format.
The ROC (Receiver Operating Characteristic) will be a plot to illustrate the true positive rate against the false positive rate at different thresholds. The plot will contain an AUC (Area Under the Curve)
which will show the probability of ranking a random positive sample higher than a random negative sample for a given classifier. Finally, the Recall will indicate the portion of correct instances that
were actually retrieved Walden (2019).

Experimental details
The dataset was imported as a dataframe from a csv file. From the multiple columns in the dataset, the columns named ’student_star’ and ’comments’ were kept and the remaining columns were dropped.
The ’student_star’ contained ratings from 0.5 to 5.0. These ratings were converted into 3 labels called ’Good’, ’Average’ and ’Bad’. Any rating in between 5.0 to 4.0 was labelled as ’Good’. Ratings
from 3.5 to 2.5 were labelled as ’Average’ and ratings between 2.0 to 1.0 were labelled as ’Bad’. As a result, it was possible to use the data for a multiclass classification problem. A total of 7 sets of
experiments were run and for each set of experiments, the dataset was split into 70% for training and 30% for testing. Rows containing empty values were also dropped. For feature extraction from
the training text, term frequency–inverse document frequency (Tf-Idf) and Count vectorizer was used with a 10,000 word limit with unigrams and bigarms Zhang et al. (2011). Experiment 1 and 2
involved machine learning algorithms and the use of words as features with the help of Count vectorizer and Tf-Idf respectively without using standard text preprocessing techniques. Experiment
3 and 4 involved the same setting as experiment 1 and 2 with the use of standard text preprocessing techniques applied to the ’comments’ column. These steps involved stop word removal, stemming
and lemmatization Kadhim (2018). Experiment 5 and 6 followed the setting of experiment 3 and 4 respectively with the addition of resampling techniques. For experiment 5, no resampling was done
on the training set. For experiment 6, Synthetic Minority Over-sampling Technique (SMOTE) was applied with the help of the imblearn library in python Chawla et al. (2002) Lemaître et al. (2017).
Experiment 7 involved the use of a deep neural network model with pre-trained word embeddings. The pre-trained word embedding model used was called glove-wiki-gigaword-300 model Borchers
(2019). The target size of the word vectors was set to 300. This means that any word in the dataset can be transformed into a vector of size 300. These vectors were used as weights in the neural network.
In order to accomplish this, the dataset was converted to a padded sequence of ids. An embedding matrix was created to map these ids to the word vectors. This was used as the weights for the input
layer in the neural network. While creating the sequence of ids, the maximum length was set to 40. While training the network, 30% of the training data was used as a validation set and the training
loss and accuracy, validation loss and accuracy was recorded over 10 iterations. Initially, a full test was conducted using the Naive Bayes classifier without any text preprocessing steps with the help of
count vectorizer which served as our baseline approach. The Naive Bayes classifier was chosen as it calculates the probability of a given label by considering the features independently and thus produces
a prediction based on the highest probability Kim et al. (2006). To further help us get insight on why the model is giving a certain prediction, the ’lime’ package in python was used to create an explainer
Ribeiro et al. (2016). This explainer was used to generate an illustration so see what the model predicts for a given instance in the test set and explains why the prediction was made.

Results
Experiments 1 and 2 did not involve the use of standard text preprocessing techniques. In experiment 1, and by using count vectorizer, we find that the Multinomial Naive Bayes algorithm has
the highest accuracy ( 73%) compared to the other algorithms used, while we observe that the SVM algorithm has the highest accuracy across all algorithms (74.5%) in experiment 2 when using Tfldf
Vectorizer. When applying text preprocessing techniques on the ’comments’ column and keeping the same settings as in experiment 1 and 2 in both experiments 3 and 4, we discover that the same
algorithms are providing the highest accuracy compared to the other algorithms used. When using count vectorizer in experiment 3, the Multinomial Naive Bayes algorithm has an accuracy of 72.8%,
while the SVM algorithm has an accuracy of 73.3% when using the Tfldf Vectorizer in experiment 4. In experiments 5 and 6, the same settings of experiments 3 and 4 were followed respectively, and
resampling techniques were added. We notice that the Multinomial Naive Bayes algorithm provides the highest accuracy in both experiments (69% and 64% respectively) compared to the rest of the algorithms
used. Finally, the Deep Learning pre-trained word embedding model used in experiment 7 has an accuracy of 66%.

Analysis
Throughout all of the experiments conducted, we discovered that the Multinomial Naive Bayes and the SVM algorithms were providing the highest accuracy compared to the other algorithms used.
Our experiments show that the Multinomial Naive Bayes algorithm performed well overall. We believe that this is because Naive Bayes is suitable for solving multi-class prediction problems, and
works best on categorical input variable than numerical ones. The experiments also showed that the neural network approach had a higher recall compared to all other approached (66%).
Although the results obtained are satisfying, we could have put more effort in the feature engineering and extraction process as our dataset is very imbalanced. Also after the text preprocessing step,
most of the comments were very short, and thus the numbers of words in a particular comment would decrease a lot.

Conclusion
The result of our work is summarized in how we performed multiple experiments on the Ratemyprofessor database, using different machine learning models and NLP techniques in order to process
all the data and words tokens for getting the best predictions based on the data studied, the models that gave the best results were Multinomial Naive Bayes and the SVM algorithms which provided
the highest accuracy on the experiments, word embedding was one of the techniques that gave better results for the preprocessing and future work will involve pretrained and transfer learning models in
which other types of predictions could be achieved.
