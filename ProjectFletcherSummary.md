# Project Summary

### Project Design

My original plan for this project was to train models on Childish Gambino's hip-hop lyrics and use these models to see if I could accurately identify Donald Glover's stand-up comedy transcripts out of a mix of comedy transcripts, in the hopes that his linguistic style would translate across media. In addition, I was planning on training the model in the reverse order and was going to attempt to see if I could identify Childish Gambino lyrics after having trained on Donald Glover's comedic transcripts. However, my project quickly changed course when I realized that I wouldn't be able to gather enough of Donald Glover's comedy transcripts in order to effectively train a model.

Due to this roadblock, I decided to stick to one medium and decided to see if I could create classification models that would be able to distinguish one hip hop artist from another. In order to do so I used the Genius API to gather artist and song information on Childish Gambino, Chance the Rapper, Drake, Kendrick Lamar, and Kanye West. Using that information and BeautifulSoup, I gathered all of the song lyrics from these artists.

There was quite a bit of data cleaning to be performed, most importantly verifying which verses contained in a song were actually from the artist whose song it was, as opposed to a featured artist on the track. Once I was satisfied with my cleaned verses, I moved onto using NLTK to begin my natural language processing. I decided to tokenize the verses and break them down in two ways, through both stemming and lemmatization, in order to check if one would have an added positive impact on my modeling. After analyzing portions of the lyrics, it seemed as though lemmatization performed much better in keeping the true meaning of words, as stemming broke up certain slang words poorly.

Once I was satisfied with the tokenization of the lyrics, I vectorized the verses using both CountVectorization and TFIDF Vecorization through sklearn. Having vectorized my data, the next step was to dimensionally reduce them. In order to do so, I tried different combinations of the two vectorizing techniques on 3 different dimensionality reducers: TruncatedSVD, Non-negative Matrix Factorization, and Latent Dirichlet Allocation. I created my own "GridSearch" to loop through the proper number of components to optimize each dimensionality reducer, and came away with interesting results. The best combination of vectorizer/reducer to separate verses by artist was not the best combination to simply cluster my data. The verses didn't cluster well by artist at all, but there seemed to be 15-17 very distinct clusters when projecting this dimensionally-reduced data down onto a T-SNE space.

I tried both KMeans++ and DBSCAN through sklearn to cluster the data, and it turned out that KMeans did a very good job at clustering my data. I validated the clusters through silhoutte scores/plots as well as labeling the T-SNE graph with my predicted labels from Kmeans. I still needed to figure out what these clusters represented though, because there was some very clear underlying structure to my data. I then used the 15 labels (one label per dimension) from the LDA dimensional reduction to label the T-SNE plot, and was able to find which topics corresponded to which cluster. From there, I used the cosine similarities to find out which verses were closest to the centroid of each cluster, and was able to create cluster labels for each of the 15 cluster, which represented the 15 distinct topics that are present in hip-hop lyrics.

After having drawn some interesting conclusions from the underlying clusters of hip-hop lyrics, I still wanted to find out the best way to classify verses by artist. In order to find the best vectorizer/reducer technique to classify artist, I created a simple recommender system and iterated through the different vectorizer/reducer combinations with varying hyper-parameters in order to determine the recommender system that would recommend the same artist the most, given a specific verse. While very rudimentary, this is how I was able to land on my combination of TFIDF vectorization with the TruncatedSVD dimensionality reduction, and then trained a multitude of classification models on each, using GridSearchCV to help me find the proper hyper-parameters, the results of which can be found in the Results section below.

Finally, I wanted to create a "Rap Generator" trained on each of the artists individually, as well as on the artists as a whole, in order to see which artist was most representative of the genre, or if each artist would be equally impactful on the combined model. In order to do so I created two different generators, the first of which used a Markov Chain technique. In order to create this model, the verses were first tokenized by word, and then were separated into bigrams, with a dictionary recording each bigram and the number of times a specific word followed that bigram. The text generator was created by taking in an initial text seed, and generated following words based on the probabilities of each word following the bigram before it, with the probabilities coming from the aforementioned dictionary. The neural network was a much more complicated model which used character-based generation on a Gated recurrent unit neural network. The Markov chain generator seemed to have much more cohesive sentence structure, because each word produced was an actual word stated by the artists in reality. The RNN allowed for much more creativity and true novel generation, which led to more mistakes. However, I fed these generated verses back into my classification models to see how well the generated texts held onto the unique linguistic signature of each artist, which can be found in the Results section below.

### Tools

For this project I used a multitude of tools, some of which were more important and more involved than others. I used MongoDB to pull in and store information off of the Genius API, and then used that information to set up a pipeline to use BeautifulSoup to scrape Genius and gather lyrics on the 5 hip hop artists I designed my project around. I used NLTK to tokenize and lemmatize the lyrics, and then used sklearn to vectorize and dimensionally reduce the lyrics. Sklearn was additionally used for clustering analysis (Kmeans++ and DBSCAN) and classification (LR, MultinomialBayes, SVM, KNN, DT, RF, GradientBoostedTrees). Neural networks (GRUs) and Markov chains were used for text generation.

### Results

#### Classification with real lyrics

| Model Name | Accuracy |
|------------|:--------:|
| Random Forest | 0.58 |
| Logistic Regression | 0.46 |
| K-Nearest Neighbors | 0.57 |
| Decision Trees | 0.49 |
| Dummy Classifier | 0.23 |

#### Classification with RNN generated lyrics

| Model Name | Accuracy |
|------------|:--------:|
| Logistic Regression | 0.38 |
| Random Forest | 0.36 |
| Decision Trees | 0.30 |
| K-Nearest Neighbors | 0.21 |
| Dummy Classifier | 0.16 |

#### Classification with RNN generated lyrics

| Model Name | Accuracy |
|------------|:--------:|
| Logistic Regression | 0.26 |
| Random Forest | 0.26 |
| K-Nearest Neighbors | 0.22 |
| Decision Trees | 0.20 |
| Dummy Classifier | 0.15 |

### Conclusions

Going forward with future iterations of this project, I'd like to include many more hip-hop artists with more contrasting styles than this group in order to get a more robust feel for this genre of music as a whole. I'd also like to create a more robust recommender system to accurately pick new music for a given listener, which I think has a very robust business case for many different companies. Finally, I'd like to re-incorporate my original idea and try to see if I could bring in a sizeable amount of Donald Glover stand-up comedy transcripts to run them through my models and see how well they are able to classify him across genres.
