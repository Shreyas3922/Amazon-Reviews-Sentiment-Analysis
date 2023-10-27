# Scrape amazon reviews for iphone13, Build model, use pretrained model for sentiment analysis
#### requirements file
All the necessary libraries for the project are given. <br>
### Webscraping Reviews 
I am using Beautifulsoup to scrape data for iphone 13 from amazon. "Splash" is a lightweight web browser with an HTTP API, implemented in Python 3, I used it because of the restrictions placed by the amazon to scrape data. The webpage is rendered on splash and then scraped from there. <br>
We can only view 10 review pages, each with 10 reviews only(total 100 reviews), Hence we can filter the reviews for 5 stars, 4 stars and so on to scrape more reviews. <br>
Check the links provided in requirements file to install and run splash. <br>
### Data Cleaning, Visualization and Basic NLTK
Remove the rows that does not have reviews in it, we need to add a column describing good and bad reviews based on the ratings, it would help to train our own custom model to determine whether a review is good or bad. For Visualization use wordcloud library to view the most common good and bad words from all the reviews. <br>
We can Tokenize the reviews using NLTK library, this would help to do stemming, lemmatization and removing stop words from the reviews. This would help increase the processing time and improve the quality of reviews. <br>
### Vader and Bert models
__vader__ : This model is only showing neutral = 1 for all the reviews becuase Vader sentiment analysis relies on a pre-trained lexicon of words and their associated sentiment scores. If the Amazon reviews contain a lot of industry-specific jargon or sarcasm, it might confuse the model and result in a neutral sentiment prediction. Hence we use lemmatization on reviews and the feed to vader modle to get pproper sentiments. <br>
__BERT__ : This is a model from Hugging face which is pretrained from a large corpus of data. This transformer model makes sure that the relationship between words is also considered for sentiment analysis. <br>
This is a good approach for sentiment analysis as it already trained from a large dataset which would help in better accuracy of the output , The custom model we build would not be so accurate becuase of small dataset. <br>
The model has its own unique tokenizer, be sure to use it on the reviews, else the model wont be able to process the reviews and give sentiments. <br>
This two models are then compare.
### Custom ANN model 
Tensorflow is used to build an artificial neural network, train the datset, and plot a validation loss and validation accuracy over epochs. <br>
we need to embedd the reviews to get vectors as the model doesnt take object type, used universal sentence encoder from transformers hub for embedding the reviews. <br>
This model is trained to determine whether a review is good or bad (It gives 2 float values representing good and bad). <br>
Result on test set : loss= 0.410 and accuracy=0.837 <br>
Some predictions are done and a confusion matrix is plotted to verify the model's accuracy.
### Result
All the models showed that there is more positivity in the reviews, which shows that iphone 13 is a good product
