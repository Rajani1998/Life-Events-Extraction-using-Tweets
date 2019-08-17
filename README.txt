The goal of the project is to extract important life events from user tweets
and identify the relevant category of the tweets.

This is done using the data set containing positive(pos.txt) and negative(neg.txt) tweets and 
Gaussian Naive Bayes is applied to train and test the data set.

It starts with the function readPosTweets() and readNegTweets() to
read the files containing positive and negative tweets.

The data is cleaned by using the function preProcessingPipeline() converting the tweets to lower case, removing punctuations and
removing stop words from the tweets, and lemmatizing the tweets.

Model is then trained with tag(pos or neg) using Gaussian Naive Bayes in the function train() which accepts tag as a parameter, 'pos' is
for positive tweets and 'neg' tag is for training negative tweets.
This training is done in the trainingPipeline() function.

The classifyPosOrNeg() function accepts tweet as a paramter and after 
preProcessingPipeline(), it classifies the tweet using the predefined function.

After classifying the tweet as postive tweet we do the following work to detect the category of the tweet.

readCat() function is used to read the file 'Categories.xlsx' which has the data
about the categories of the tweets, each category maps to some of the keywords which are used to identify 
the category, there is a total of forty three categories in the file.

The preProcessCategories() function is used to clean the data in the categories.
The trainCategories() function is for training the model for identifying categories. The
model is saved in JSON format("data/categories.json").
classigyCategory() function just accepts the tweet and classifies it 
using the predefined function.

finalTrainingPipleine() is the function which classifies both the tag and category.
extractEvent() function accepts the tweet, applies preProcessingPipeline() on it,
and classfies the tag using classifyPosOrNeg() function, if the tag is 'pos', it returns the life event category by calling
classifyCategory() function, else it returns "Not recognized."