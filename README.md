# Advanced Machine Learning Models Applied to COVID Diagnosing

This project aims to develop and evaluate advanced machine learning models for diagnosing COVID-19 based on medical imaging data such as chest X-rays or CT scans. The goal is to assist healthcare professionals in quickly and accurately identifying COVID-19 cases, especially in situations where laboratory testing may be limited or unavailable.

## Project Overview

The project uses the COVID-19 Radiography Database [1] as it's dataset. It has a total of 15153 Chest X-Rays (CXRs) belonging to 3 different classes (COVID-19,  Normal and Viral Pneumonia).

The project focuses on the following key components:

1. (**Data Collection & Expoloration**)[https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/Data%20Analysis%20Pipeline.ipynb]: Gathering a diverse and representative dataset of medical images, including chest X-rays and CT scans, from confirmed COVID-19 cases as well as non-COVID-19 cases (e.g., pneumonia, normal). This part of the project focuses on analyzing the quality and features of the dataset.

Our data is CT scans similair to this:


  ![image](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/assets/88550828/cb9ea00b-34da-4c15-ac1d-5024efc94ae3)  


Each CT scan is labeled with COVID-19,  Normal, or Viral Pneumonia, and the three types have the following distrubution.


<img src="https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/assets/88550828/6edbc636-32f6-43e4-ac41-93bfe4c5f0d3" alt="image" width="300" height="200">



2. (**Data Preprocessing**)[https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/Data%20Augmentation%20%26%20Visualization.ipynb]: Preprocessing the medical images to ensure they are standardized and suitable for input into machine learning models. This includes tasks such as resizing, normalization, and augmentation. We use majorly two types of Data Augmentation:

- **Symmetry:** Involves flipping an image horizontally or vertically to create new samples.
- **Rotation:** Rotating an image by a certain angle to create new samples.

3. **Model Development**: Developing and training advanced machine learning models, such as convolutional neural networks (CNNs) or deep learning models, to classify medical images as COVID-19 , Normal, orViral Pneumonia. Generally, we first deigned two CNN models, then proposes a fine-tuned CNN model. Then we employed transfer learning to train Resnet-18 & Resnet-26 for our project. For additional models, we implemented EfficientNet as well as InceptionV3. So in general, we have the following models implemented in our project:

- **(CNN-1)[https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/CNN_Model_1.ipynb]** 12 layer CNN with max pooling. 
- **CNN-2** 12 convolutional layers and introducing Dropout layers
- **CNN-best_3** Fine-tuned 12-layer CNN. Hyperparameter done by Gridsearch. 
- **(ResNet-26)[https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/Resnet26.ipynb]** A 26-layer deep neural network with residual connections.
- **(Resnet-18)[https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/Resnet18.ipynb]** A 18-layer deep neural network with residual connections.
- **EfficientNet** Scalable convolutional neural networks achieving state-of-the-art accuracy with fewer parameters.
- **InceptionV3** A convolutional neural network with deep and wide architecture, featuring multiple inception modules.
  
5. **Evaluation**: Evaluating the performance of the developed models using metrics such as accuracy, sensitivity, specificity, and area under the receiver operating characteristic curve (AUC-ROC).

6. **Deployment**: Exploring options for deploying the trained models in real-world healthcare settings, considering factors such as scalability, interpretability, and regulatory compliance.

## Getting Started

To get started with the project, follow these steps:

1. **Clone the Repository**: Clone this repository to your local machine using the following command: git clone https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/



Model Development: Develop and train your machine learning models using the prepared data. Experiment with different architectures and hyperparameters to achieve the best performance.

Evaluation: Evaluate the performance of your models using the provided evaluation metrics. Fine-tune your models as needed to improve their performance.

Deployment: If applicable, explore options for deploying your trained models in real-world healthcare settings. Consider factors such as data privacy, model interpretability, and regulatory requirements.

## References 

[1] David L. Smith, John-Paul Grenier, Catherine Batte, and Bradley Spieler. A Characteristic Chest Radiographic Pattern in the Setting of the COVID-19 Pandemic. Radiology: Cardiothoracic Imaging 2020 2:5.

[2] https://github.com/priyavrat-misra/xrays-and-gradcam/tree/master

Contributors
Nicolas Choong (ndc2140@columbia.com)
Qiankun Li (ql2510@columbia.edu)
License

Feel free to reaach out to discuss!
