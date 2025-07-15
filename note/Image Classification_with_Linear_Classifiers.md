## Lecture 2: Image Classification with Linear Classifiers

### Image Classification

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

### Nearest Neighbor Classifier

