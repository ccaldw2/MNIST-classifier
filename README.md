# MNIST-classifier
Utilising a Random-forest classifier to do multiclass predictions on the MNIST Optical Character Dataset, which is composed of 70000 bitmaps for handwritten digits between 0 and 9
## Initial Model
First I split data into training and test sets of 60,000 and 10,000 respectively. I then used the training data to train a random forest classifier model, chosen due to its ability to do multiclass classification without having to use OvO or OvA. This initial model had an effective accuracy score of 94.92%
## Min-Max Scaling
I next attempted to scale the image bitmaps so that, instead of having values between 0 and 255, they laid between 0 and 1. I then trained a scaled classifier, and found no performance increase
## Dataset Augmentation
Next, I created a set of functions to shift the numbers in each image in a direction (up,down, left, or right) by 1 pixel. I then replicated the dataset 4 times, applying a transformation in one direction to each new set, and then concatenated them together. This effectively extended the training set from 60,000 to 300,000. While it now took significantly longer to train the RF classifier, it did increase the accuracy to 95.79%
## Hyperparameter Tweaking
I created a randomized search class to assess various hyperparameters on the RF classifier. due to hardware limitations, I picked very small iteration numbers (So there may be further room to optimise), and subsequently changed the n_estimators from 10 to 125, and the min_samples_split from 2 to 4 in a new, tuned RF model. Using the augmented dataset, this pushes the accuracy metric to 97.58%.
