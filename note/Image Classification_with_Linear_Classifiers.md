# Lecture 2: Image Classification with Linear Classifiers

## Image Classification

**A core Task in Computer Vision**
- The image classification task
- Two basic data-diven approches to image classification
    - K-nearest neighbor and linear classifier

---

### Motivation

---

### Challenges

- Viewpoint vairation
- Scale variation
- Deformation
- Occlusion
- Illumination conditions
- Background clutter
- Intra-class vairation

---

### Data-driven approach

**The image classification pipeline**
We’ve seen that the task in Image Classification is to take an array of pixels that represents a single image and assign a label to it. Our complete pipeline can be formalized as follows:

- **Input:**  Our input consists of a set of N images, each labeled with one of K different classes. We refer to this data as the training set.
- **Learning:** Our task is to use the training set to learn what every one of the classes looks like. We refer to this step as training a classifier, or learning a model.
- **Evaluation:** In the end, we evaluate the quality of the classifier by asking it to predict labels for a new set of images that it has never seen before. We will then compare the true labels of these images to the ones predicted by the classifier. Intuitively, we’re hoping that a lot of the predictions match up with the true answers (which we call the ground truth).

---

### Nearest Neighbor Classifier

he nearest neighbor classifier will take a test image, compare it to every single one of the training images, and predict the label of the closest training image. 

You may have noticed that we left unspecified the details of exactly how we compare two images, which in this case are just two blocks of 32 x 32 x 3.One of the simplest possibilities is to compare the images pixel by pixel and add up all the differences. In other words, given two images and representing them as vectors $ I1,I2 $, a reasonable choice for comparing them might be the L1 distance.

### K-Nearest Neighbor Classifier

Instead of finding the single closest image in the training set, we will find the top k closest images, and have them vote on the label of the test image. 

--- 

### Validation sets for Hyperparameter Tuning

In particular, we cannot use the test set for the purpose of tweaking hyperparameters.
Luckily, there is a correct way of tuning the hyperparameters and it does not touch the test set at all. The idea is to split our training set in two: a slightly smaller training set, and what we call a validation set. This validation set is essentially used as a fake test set to tune the hyper-parameters.

- **Cross-validation:**  In cases where the size of your training data (and therefore also the validation data) might be small, people sometimes use a more sophisticated technique for hyperparameter tuning called cross-validation. 

- **In practice:** In practice, people prefer to avoid cross-validation in favor of having a single validation split, since cross-validation can be computationally expensive. 

### Pros and Cons of Nearest Neighbor Classifier

---

## Linear Classification

The approach will have two major components: a score function that maps the raw data to class scores, and a loss function that quantifies the agreement between the predicted scores and the ground truth labels. We will then cast this as an optimization problem in which we will minimize the loss function with respect to the parameters of the score function.


### Paramereterized mapping from images to label scores

Linear classifier. In this module we will start out with arguably the simplest possible function, a linear mapping:
$$ f_{(x_i,W,b)} = Wx_i + b$$

In the above equation, we are assuming that the image $x_i$ has all of its pixels flattened out to a single column vector of shape [D x 1]. The matrix $W$ (of size [K x D]), and the vector $b$ (of size [K x 1]) are the parameters of the function. 

The parameters in $W$ are often called the weights, and $b$ is called the bias vector because it influences the output scores, but without interacting with the actual data $xi$.


### Interpreting a linear classifier

- Analogy of images as high-dimensional points.
- Interpretation of linear classifiers as template matching.
- Bia trick
- Image data preprocessing


### Loss function

Intuitively, the loss will be high if we’re doing a poor job of classifying the training data, and it will be low if we’re doing well.

#### Muticlass Support Vector Machine loss


