# Project_Fletcher

Fourth project at Metis Data Science Bootcamp (NLP/Unsupervised). Classification of hip-hop artists based on individual verses from their songs. Clustering analysis was performed to see if clustering could be used to separate verses by artists. Additionally, two forms of text generation were used to create new verses after having been trained on the original artists, and these generated texts were fed into the trained classification models in order to see if their linguistic signature remained through the text generation process.

## Repository design

This repo is broken down into 4 main folders:
* Genius_API
* NLP_and_Clustering
* Markov_Rap_Generators
* RNN_Rap_Generators

The Genius_API folder contains two files in which I obtained information from the Genius API and gathered lyrics for the Natural Language Processing (NLP) portion of my project.

The NLP_and_Clustering folder contains the portions of my project that have to do with the natural language processing techniques and unsupervised clustering of verses. The important files to look at here are the Fletcher_NLP_all_rappers and Fletcher_Clustering_Scaled notebooks.

The Markov_Rap_Generators and RNN_Rap_Generators are broken down by artist, but all contain identical code. This was originally performed to make sure each artists generated texts were kept separate, but in a future commit this will all be contained in one notebook.
