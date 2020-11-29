A self case study in deep learning based computer vision. Transfer Learning with VGG16, ResNet50, Inception_V3 and MobileNet.

### The Dataset
1. The dataset can be obtained from Kaggle : https://www.kaggle.com/puneet6060/intel-image-classification
2. This Data contains around 25k images of size 150x150 distributed under 6 categories.
3. The categories are 'buildings', 'forest', 'glacier' , 'mountain' , 'sea', 'street'.
4. The Train, Test and Prediction data is separated in each zip files. There are around 14k images in Train, 3k in Test and 7k in Prediction.
5. The Train and Test images are grouped in folders according to their classes and hence ImageDataGenerated gets hold of their class labels.
6. The images from test folder are used for validation during training.
7. Prediction images are not grouped in folders according to their classes and hence we can not calculate test accuracy using these images.
8. Prediction images are used to check predictions on individual images. 
9. All images are of size 150 x 150.

### The problem statement
Its a multiclass classification problem with six classes in Intel image scene dataset. 

### Preprocessing
Different preprocessing is done for different models
1. Data Augmentation is used for VGG16, Inception and mobileNet.
2. For ResNet50 the in built preprocessing provided by tf.keras.applications.resnet.preprocess_input is used.
3. The Data Augmentation, when used, is applied only to train set and not to validation and test set.
4. Rescaling to 1/255 is done for all sets
5. Batch sizes used are : ResNet-256, mobileNet-128, Inception-128, VGG16-256.

### Modeling
1. Pretrained models having imagenet weights are used with transfer learning.
2. Modeling is done with VGG16, ResNet50, Inception_V3 and MobileNet.
3. All the layers except last few layers of the model are frozen.
4. The top layer of the model is not used. Instead, a dense layer with 6 units and softmax activation is used.
5. VGG16 took the longest to train while mobileNet is the quickest.

### Results
1. Accuracy and loss plots along with Confusion matrix is plotted for all models.
2. Validation accuracies are as follows
      ##### VGG16        - 89.13%
      ##### Inception_V3 - 84.17%
      ##### ResNet50     - 91.37%
      ##### mobileNet    - 90.43%
3. The predictions on test images are not so good for Inception_V3 and mobileNet models.
4. VGG16 and ResNet have performed really well on test images.


