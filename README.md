You have text data and want to create a set of features indicating the number of times an observation’s
text contains a particular word, Use scikit-learn’s CountVectorizer, This output is a sparse array, which is often necessary when we have a large amount of text. However,
in our toy example we can use toarray to view a matrix of word counts for each observation, We can use the get_feature_names method to view the word associated with each feature, This might be confusing, so for the sake of clarity here is what the feature matrix looks like with the
words as column names (each row is one observation), One of the most common methods of transforming text into features is by using a bag-of-words model.
Bag-of-words models output a feature for every unique word in text data, with each feature containing a
count of occurrences in observations. For example, in our solution the sentence I love Brazil.
Brazil! has a value of 2 in the “brazil” feature because the word brazil appears two times.
The text data in our solution was purposely small. In the real world, a single observation of text data
could be the contents of an entire book! Since our bag-of-words model creates a feature for every
unique word in the data, the resulting matrix can contain thousands of features. This means that the size
of the matrix can sometimes become very large in memory. However, luckily we can exploit a common
characteristic of bag-of-words feature matrices to reduce the amount of data we need to store.
Most words likely do not occur in most observations, and therefore bag-of-words feature matrices will
contain mostly 0s as values. We call these types of matrices “sparse.” Instead of storing all values of the
matrix, we can only store nonzero values and then assume all other values are 0. This will save us
memory when we have large feature matrices. One of the nice features of CountVectorizer is that the
output is a sparse matrix by default.
CountVectorizer comes with a number of useful parameters to make creating bag-of-words feature
matrices easy. First, while by default every feature is a word, that does not have to be the case. Instead
we can set every feature to be the combination of two words (called a 2-gram) or even three words (3-
gram). ngram_range sets the minimum and maximum size of our n-grams. For example, (2,3) will
return all 2-grams and 3-grams. Second, we can easily remove low-information filler words using
stop_words either with a built-in list or a custom list. Finally, we can restrict the words or phrases we
want to consider to a certain list of words using vocabulary. For example, we could create a bag-ofwords feature matrix for only occurrences of country names, 
