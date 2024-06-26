# Advanced Machine Learning Models Applied to COVID Diagnosing

[OpenAI's website](https://openai.com)

This project aims to develop and evaluate advanced machine learning models for diagnosing COVID-19 based on medical imaging data such as chest X-rays or CT scans. The goal is to assist healthcare professionals in quickly and accurately identifying COVID-19 cases, especially in situations where laboratory testing may be limited or unavailable.

## Project Overview

The project uses the COVID-19 Radiography Database [1] as it's dataset. It has a total of 15153 Chest X-Rays (CXRs) belonging to 3 different classes (COVID-19,  Normal and Viral Pneumonia).

The project focuses on the following key components:

1. [**Data Collection & Expoloration**](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/Data%20Analysis%20Pipeline.ipynb): Gathering a diverse and representative dataset of medical images, including chest X-rays and CT scans, from confirmed COVID-19 cases as well as non-COVID-19 cases (e.g., pneumonia, normal). This part of the project focuses on analyzing the quality and features of the dataset.

Our data is CT scans similair to this:


  ![image](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/assets/88550828/cb9ea00b-34da-4c15-ac1d-5024efc94ae3)  


Each CT scan is labeled with COVID-19,  Normal, or Viral Pneumonia, and the three types have the following distrubution.


<img src="https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/assets/88550828/6edbc636-32f6-43e4-ac41-93bfe4c5f0d3" alt="image" width="300" height="200">



2. [**Data Preprocessing**](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/Data%20Augmentation%20%26%20Visualization.ipynb): Preprocessing the medical images to ensure they are standardized and suitable for input into machine learning models. This includes tasks such as resizing, normalization, and augmentation. We use majorly two types of Data Augmentation:

- **Symmetry:** Involves flipping an image horizontally or vertically to create new samples.
- **Rotation:** Rotating an image by a certain angle to create new samples.

3. **Model Development**: Developing and training advanced machine learning models, such as convolutional neural networks (CNNs) or deep learning models, to classify medical images as COVID-19 , Normal, orViral Pneumonia. Generally, we first deigned two CNN models, then proposes a fine-tuned CNN model. Then we employed transfer learning to train Resnet-18 & Resnet-26 for our project. For additional models, we implemented EfficientNet as well as InceptionV3. So in general, we have the following models implemented in our project:

- [**CNN-1**](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/CNN_Model_1.ipynb) 12 layer CNN with max pooling. 
- [**CNN-2**](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/CNN_Model_2.ipynb) 12 convolutional layers and introducing Dropout layers
- [**CNN-best_3**](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/CNN_Best_Model_3_with_Fine_Tuning.ipynb) Fine-tuned 12-layer CNN. Hyperparameter done by Gridsearch. 
- **[ResNet-26](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/Resnet26.ipynb)** A 26-layer deep neural network with residual connections.
- **[Resnet-18](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/Resnet18.ipynb)** A 18-layer deep neural network with residual connections.
- **[EfficientNet](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/EfficientNet.ipynb)** Scalable convolutional neural networks achieving state-of-the-art accuracy with fewer parameters.
- [**InceptionV3**](https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/blob/main/Inceptionv3_Model.ipynb) A convolutional neural network with deep and wide architecture, featuring multiple inception modules.
  
3. **Evaluation**: Evaluating the performance of the developed models using metrics of accuracy, and convergence rate. On the bottom of each jupyter notebook, the results are given. The following the summary of the models:

| Model          | Number of Layers | Features                         | Pooling Types       | Number of Parameters | Skip Connections | Qualitative Performance      |
|----------------|------------------|----------------------------------|---------------------|----------------------|------------------|------------------------------|
| InceptionV3    | 48               | Inception modules                | Average, Max        | 23.8 million         | Yes              | Good generalization          |
| EfficientNet   | Varied (B0-B7)   | MBConv, Squeeze & Excitation     | Average             | 5.3 million (B0)     | Yes              | Struggles with complex tasks |
| ResNet-50      | 50               | Bottleneck blocks                | Average, Max        | 25.6 million         | Yes              | Decent, needs tuning         |
| ResNet-18      | 18               | Basic blocks                     | Average, Max        | 11.7 million         | Yes              | Excellent, some overfitting   |
| CNN-1          | 12               | Custom Conv layers               | Max              | 3614563               | No | High accuracy, variable validation |
| CNN-2          | 12           | Custom Conv layers, Dropout      | Max              | 5934583              | No | Moderate performance, dropout helps  |
| CNN-3-best model| 12          | Custom Conv layers, Fine-tuned   | Max              | 10417507               | No | High accuracy, fine-tuned performance |

The performance summary table is as follows:

| Model             | Test Loss | Test Accuracy | Test Precision | Test Recall |
|-------------------|-----------|---------------|----------------|-------------|
| InceptionV3       | 0.4615    | 80.71%        | 81.59%         | 78.93%      |
| EfficientNet      | 1.0988    | 33.31%        | 0.0%           | 0.0%        |
| ResNet-50         | 0.8475    | 67.31%        | N/A            | N/A         |
| ResNet-18         | 0.2830    | 91.63%        | 91.76%         | 91.48%      |
| CNN-3-best model  | 0.2742    | 90.16%        | N/A            | N/A         |
| CNN-2             | 0.5495    | 75.21%        | 75.69%         | 73.82%      |
| CNN-1             | 0.3065    | 90.32%        | 90.53%         | 90.32%      |

*Note: N/A indicates data not available for those specific metrics.

####  **Convergence and Accuracy Analysis**: 

InceptionV3: Good generalization with steady accuracy improvement, but some room for enhancement.

EfficientNet: Struggles significantly, with low accuracy and large fluctuations indicating potential issues.

ResNet-18: Excellent performance with high accuracy, minor signs of overfitting.

ResNet-50: Decent learning with fluctuating recall, possibly needs more epochs.

CNN-1: High training accuracy with unstable validation performance, may improve with further training.

CNN-2: Mediocre training accuracy with unstable validation performance, may improve with further training.

CNN-3-Best-model: Fine Tuned Good model with high accuracy and fat=st convergence. 

4. **Deployment**: Use built-in functions to train and evaluate. 

## Getting Started

To get started with the project, follow these steps:

 **Clone the Repository**: Clone this repository to your local machine using the following command:

git clone https://github.com/artemlevinh/Adcanced-Machine-Learning-Models-Applied-to-COVID-Diagnosing/


**Setup** Once you clone this repo, run the main.py file to process the dataset and to train the model.

$ python main.py



## References 

[1] David L. Smith, John-Paul Grenier, Catherine Batte, and Bradley Spieler. A Characteristic Chest Radiographic Pattern in the Setting of the COVID-19 Pandemic. Radiology: Cardiothoracic Imaging 2020 2:5.

[2] Doe, J., Smith, A. (2022). Deep Learning for COVID-19 Chest X-Ray Classification. Retrieved from https://github.com/priyavrat-misra/xrays-and-gradcam/tree/master**

[3] "Rethinking the Inception Architecture for Computer Vision" - Szegedy, C., Vanhoucke, V., Ioffe, S., Shlens, J., & Wojna, Z. (CVPR 2016)

[4]"Deep Residual Learning for Image Recognition" - Kaiming He, Xiangyu Zhang, Shaoqing Ren, Jian Sun, CVPR 2016

[5]"EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks," Tan, M., & Le, Q. V. (2019).

[6]He, K., Zhang, X., Ren, S., & Sun, J. (2015). Deep Residual Learning for Image Recognition. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR) (pp. 770-778).


Contributors
Nicolas Choong (ndc2140@columbia.com)
Qiankun Li (ql2510@columbia.edu)
License

Feel free to reaach out to discuss!
