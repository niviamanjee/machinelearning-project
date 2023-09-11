# machinelearning-project

## Introduction

We aim to create an unsupervised model and cluster the images via k-means clustering (while also applying PCA). This means taking out the emotion encodings/column (at least) of the original dataset. 

![Kmeans Clustering](images/KmeansClustering.png)

We hope that the optimal number of clusters is 7 (like the original dataset, the number of emotions), which we then will manually assign each cluster an emotion label based on the closest images to each centroid. We then will assign the corresponding emotion to every image in that cluster and compare it with the original images in the dataset to see if the emotions are correct.

Creating a model for facial recognition is really cool to think about because a machine identifying faces and emotions was something unheard of in the early age of computers. Creating a somewhat successful model as a group of college students would be an achievement.

We wanted to test our technical abilities as well by choosing an unsupervised, image-based project rather than a supervised one based on continuous values. This would allow us to push our limits and give us more confidence for more difficult projects in the future.

The broader impact is that we could give anyone the ability to use our model and classify emotions with any image dataset they have. They would be able to train a model to recognize human emotions without much human input (just by uploading their image dataset)

## Methodology
### Data Exploration
Our dataset is named fer2013.csv and is a dataset that consists of 35,887, 28x28, pixelated images. As such, the dataset consists of 35,887 entries. Each entry has 3 columns: emotion, pixels, and usage. 

Each face is classified into one of 7 emotions: anger, disgust, fear, happy, sad, surprise, or neutral. An encoding for these goes into the emotion column for an entry. The pixel information for each image goes into the pixel column (a 48x48 image, so 2304 values should be in each entry's pixels column. Values range from 0-255). Usage is either training, public test, or private test, which is similar to saying which images should be used for training, validation, or testing.

The dataset contains a wide variety of faces, including individuals of varying ages, people with and without makeup, individuals from different racial backgrounds, actors, and even some instances of virtual avatars. In summary, this dataset offers a substantial and diverse collection of faces, making it highly valuable for training machine learning models.

Link to database: https://ufile.io/40nmtjlw

### Data Preprocessing
The dataset is already almost completely preprocessed. The pixels have been compressed to be 48 x 48 and have already been converted to greyscale. This means we have to do a little preprocessing on the images.

However, we plan to normalize the grey scale values within each entry's pixel column. This will make the pixel column more readable, and less greyscale intensity with numerous images may help with overall speed as normalizing may help with gradient calculation.

We also plan to get an even amount of images from each emotion class, 547, in order to ensure our model doesn't become biased to seeing one emotion too much and hopefully speed up computations for our dataset. This will also justify our removal of the usage column.

The images don't need to be cropped or resized. We don't need to crop them because the images are already pretty decently focused on people's faces, and a good facial recognition model should be able to detect faces even in bad circumstances. They don't need to be resized too because they are already tiny. Normalization will most likely occur. 

### Models
For our Face emotion recognition model, we decided to use unsupervised learning. We used kmeans clustering to cluster the data categorizing it into different groups that could represent the different types of emotions. In our model, the images are converted into 2D arrays. We used PCA to reduce the dimension of the images before fitting them into our kmeans model. Since we have a total of 7 types of emotions, we chose a cluster value of 7. To evaluate the model's efficiency, we used the silhouette score as a metric. So far when training the model we obtain a silhouette score of about 0.3. To improve the model, we applied cross-validation. However, the score only increased by about 0.01. An alternative to improve our model could be data transformation or a different form of data preprocessing using an algorithm different from PCA.

## Results
#### DUMP OUT THE RESULTS HERE BUT DONT TALK ABOUT THEM, ADD DIAGRAMS OF RESULTS, THE CLUSTERING DIAGRAM, OR OTHERS THAT SHOW OUR RESULTS
#### LAST PARAGRAPH HERE IS ABOUT THE FINAL MODEL AND FINAL RESULTS SUMMARY

## Discussion
#### TALK ABOUT THE RESULTS HERE, AND OUR THOUGHT PROCESS BEGINNING TO END. REALLY THINK IN THIS SECTION AND SHOW HOW YOU THINK SCIENTIFICALLY 
In the preprocessing step, we decided to only grab 547 sample images from each class of emotion because one of the classes of emotion only had 547 sample images. Initially, we wanted more than 547 samples to train the model but having more than 547 samples will lead to bias in our model. Therefore, we only have 547 samples from each emotion class. The data was already downsized and gray-scaled so there wasn’t any other thing we would have done other than normalizing the pixels values of each image and dropping the columns “emotion” and “usage”. The column “emotion" is the classification of each image and the “usage” columns specify whether the image will be used for testing or training. We don't need these columns because we are doing unsupervised ML to classify each image and doing our own splitting of the images for testing and training. Before we do any machine learning, we wanted to check and remove any null data so it won’t impact the results of our model. 

Our first model was not that great. The images closest to the centroids of each cluster seem to have no relationship to each other in human eyes but there is some patterns and relationship that only a computer can see. This is to say that there exists some underlying relationship between each image that could be used to better classify the images. We tried printing out more and more of each image at the centroids of each cluster but it seems like every image’s emotion is pretty much random to the naked eyes even though they are images from the centroid of each cluster and should have some relationship to each other. This could mean that the computer may have came out with different kind of classification that we are unaware of. For example, emotions like angry, sad, or happy is obvious to humans but to computer, it is entirely different. Therefore, we concluded that these emotions classification is something only computer can understand what it means and impossible for humans to understand these classification. Out of curiosity, we try a larger set of data to see if it yields better accuracy. And it did! But it only improved the accuracy by a little bit. 

Since we are going for an unsupervised approach we don't really have a true over/underfitting situation so we attempted to compare the clusters to the original dataset. We mapped out our clustered images to the emotions from the original dataset. This was done by plotting a random set of images from each cluster and then mapping out each emotion visually to their respective original emotion. This process was challenging because the clustering wasn't great so we mapped to the emotion that was most dominant. We got an accuracy of about 14% meaning that there was little correlation to the original emotions. Our next steps are to improve the model to increase our silhouette score, which in turn might increase the classification accuracy of the model.

## Conclusion
#### WRAP UP, MIND DUMP, OPINIONS FUTURE PLANS, WHAT WOULD WE DO DIFFERENT.

## Collaboration
#### EVERYONE WILL BE FILL THIS PART OUT FOLLOW EXAMPLE...
### Start with Name: Title: Contribution. If the person contributed nothing then just put in writing: Did not participate in the project.
### Dillon Jackson: Wroked on the readme, accuracy testing, and project facilitation 
