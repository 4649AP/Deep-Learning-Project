# Convolution Neural Network Architecture Exploration Project

### Aim: 
Achieve the best possible classification by training on a provided training dataset of 37882, 128 pixel by 128 pixel, grayscale images that are transformed to arrays with values ranging between 0-255. Each image contains a seemingly digitally generated single centered character out of context with almost no visual noise. 

### Hardware:
We created an p2-xlarge GPU instance on Amazon EC2 consisting of a GPU with 12GB memory, 4 vCPUs and 61GB of memory. The AWS Deep Learning AMI was adopted and comes pre-installed with Python3.6, Tensorflow and Keras. Other required packages were installed to the instance and experiments conducted using Jupyter notebooks. Within this environment the benchmark CNN ran in 122 seconds.

### Input Data: 
The dataset contains black characters on a white background with varying height and width, belonging to one 62 classes including digits 0-9 and the alphabet in both upper-case and lower-case. Each character has been stripped of context, including other characters of a word or sentence, relative size of neighbouring characters or a plane that may give some hint towards the case of a character. Thus, for this distilled challenge classifiers will be relying primarily on the features of the character itself to perform classification.

### Model Experiments

![Model table](https://github.com/4649AP/Deep-Learning-Project/blob/master/DL_table.png?raw=true)


### Results: 
The initial Feedforward Neural Network’s established a baseline accuracy of a surprisingly high 85%, which confirmed the group’s expectation that centered alignment and lack of noise in the input images of this dataset presented would be conducive to classification using neural networks. As anticipated a Convolutional Neural Network represented a material improvement over the baseline. The group then sought to maximise accuracy by attempting to apply a variety of network configurations iteratively and adjusting architectures based on inspection of the progressive training and validation accuracy/loss. Beginning with an architecture using concepts informed by the VGGNet architecture, such as multiple 3x3 convolutional layers between pooling layers, we applied subsequent advancements such as Batch Normalisation. Eventually the increasing width of convolutional layers present in VGGNet was abandoned for a simpler series of 32 filter convolutional layers with no negative impact on accuracy.

Data augmentation was explored but because the images depict characters, to retain proper context only limited rescaling and warping were applied with no material improvement to predictive ability. Experimentation revealed that simpler networks with far less parameters and showed a slightly improved accuracy. Varying combinations of convolutional layers and fully connected layers until Model D was found to give the best accuracy at 90.79%.

Inspection of the resultant confusion matrix reveals that over 70% of classes were consistently predicted (over 90%). However where the CNN appeared to struggle was with similarly shaped characters, despite their relative size, such as some uppercase and lowercase pairs of the same alphabetic symbol.


### Conclusion: 
The final CNN model achieved over 90% accuracy which seemed to handle the majority of prediction cases. The difficulty in differentiating some uppercase and lowercase pairs appears to be a result of the scale invariant focus on local features by CNNs. Given a larger training dataset or images with greater context, perhaps it could be overcome by these models. Otherwise, the presence of mislabels training dataset, which is to be expected in ‘real-life’, highly stylized fonts and italics seem to contribute the inaccuracies present and hindered progress towards higher accuracies. In a practical use case, these limitations could be addressed by providing input characters with more context such as words, sentences and a consistent horizontal plane that may aid the model to grasp greater contextual information to improve accuracy.




