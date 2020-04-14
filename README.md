# COVID-19 Detection from chest X-Ray images using Convolutional Neural Networks

#### Pablo Lázaro Herrasti (lazaroh.pablo@gmail.com)
#### Rubén Barco Terrones  (rubate10@gmail.com)

## Abstract
In 2020, humanity is facing one of the greatest challenges ever seen in the last years because of a virus (Covid-19). An unprecedented pandemic that has millions of people confined at home. In this research, the possibility of detecting this virus in people using chest X-Ray images is studied. (i) A public dataset containing images from Covid-19, viral pneumonia and healthy people is used with (ii) Convolutional Neural Network architecture to be able to differentiate between various medical situations. Finally, (iii) it is revealed graphically the regions on which the CNN focuses in order to determine the medical situations of the person.

## Introduction
In this work, we have tried to argue about the feasibility of automatically detecting Covid-19 by using chest X-Ray images. **This research does not want to make any medical claim about Covid-19, because this is not our work and is not our purpose**. Our main goal is to study a new way to **help doctors** in their decisions. We are **not trying to replace their knowledge and experience**, we just want to see if this type of tools based on Deep Learning can be exploited by them.

Attending to experts, the main symptoms of the virus are the following: sore throat, cough, fever and difficulty breathing (in severe cases). **In most of the severe cases, the virus is capable of causing pneumonia in the patient**. One of the techniques used to detect pneumonia are chest X-Ray images, among many other, because they provide a very useful insight into the lungs. Is this pneumonia easy to detect? Can we differentiate between a viral pneumonia and a Covid-19 pneumonia? These two questions are the main concepts that this research is trying to solve. In order to bring a solution, some **Deep Learning** techniques are applied.

In this research, we are going to use some **Convolutional Neural Networks (CNNs)**. This network is able to extract these complex features from the samples given to the network and generalize the results with other samples that the network has never seen.

## Database
The database has been downloaded from a public [Kaggle](https://www.kaggle.com/tawsifurrahman/covid19-radiography-database/data#). The images were collected from different sources and they are truthful images.

![Examples from the database.](https://github.com/polazaro/Covid-19-Detection/blob/master/images/database.bmp)

This database contains chest X-ray images for **COVID-19 positive cases** along with **Healthy** and **Viral Pneumonia** images. In their current release, there are **219 COVID-19 positive images**, **1341 normal images** and **1345 viral pneumonia images**. 

## Method
For the training processes we have used Keras over Tensorflow an Python. All the architectures have been created, trained and tested from scratch, which means that the weights of the network are initialized randomly and there is not previous information from other data that could help our models to improve their results. 

#### First Architecture - Baseline Architecture

We propose the following baseline CNN:

![Baseline Architecture.](https://github.com/polazaro/Covid-19-Detection/blob/master/images/baseline.bmp)

This simple architecture consists of three Convolutional layers followed by a MaxPooling layer after each of them to reduce the dimensionality of the outputs. The convolutional layers have 32, 64 and 128 filters, respectively, all of them with size 3x3. After this blocks, the obtained features are flattened and two consecutive Fully-Connected layers are applied to reduce the dimensionality of the feature vector (the first one) and to perform de classification (the second one).

#### Second Architecture - Inception Based Architecture

The second architecture is based in a technique called **inception**. The main idea is to use different size kernels (1x1, 3x3, and 5x5) and different number of kernels (64, 32 and 16, respectively) in parallel to extract different features from the same image. Then, all these features are concatenated and its dimensionality is reduce by a MaxPooling layer. After that, another convolutional layer is applied, followed by its correspondant MaxPooling layer. At the end , we apply the same two Fully-Connected layers to reduce the dimensionality and perform the classification.

![Inception Based Architecture.](https://github.com/polazaro/Covid-19-Detection/blob/master/images/final_arch.bmp)

## Experiments and Results
First of all, some data augmentation has been done in order to balance the COVID-19 cases with the other two classes, because we are in an unbalance scenario. In the following table we can see the number of samples divided by its class:

![Number of samples.](https://github.com/polazaro/Covid-19-Detection/blob/master/images/data_aug.bmp)

We are obtaining a total of **739** new samples with the following data augmentation techniques
* Left-Right Flip
* Rotation (-15º to 15º)
Here are some examples of the data augmentation, where a) corresponds to a flipped one and b) is a rotation.

![Examples of Data Augmentation.](https://github.com/polazaro/Covid-19-Detection/blob/master/images/data_aug_examples.bmp)

The distributions for the **training process** are: **75%** of the samples for training, **15%** for validation and **15%** for test. It is important to note that the test set from Covid-19 is going to be composed of only 33 images, which is a very poor test set, but there are no more public X-Ray images from Covid-19 that we could use in these experiments.

We have performed some experiments without data augmentation and some with data augmentation in order to compare the influence of these "artificial" samples. The results are collected in this table:

![Results.](https://github.com/polazaro/Covid-19-Detection/blob/master/images/results.bmp)

We obtain a surprisingly high test accuracy of **95,45%** without data augmentation. This means that the model is making 415 correct predictions over 435 samples. If we compare the performance of the baseline model for the three classes separately, we can see that the **Healthy and Pneumonia is much higher (98.50% and 95.04% respectively) than Covid-19 accuracy (78.78%)**, as we expected. Now, if we focus on the baseline model with data augmentation, the total test accuracy is improved in **0,23%** and the accuracy for the COVID-19 samples has increased until **84,84%**. The second architecture improves even more this result, with a COVID-19 test accuracy of **87,87%**, but decreases the accuracy for the Pneumonia cases in 1%.

#### Conclusion
With very simple architectures we are able to learn and distingish some features from penumonia, COVID-19 and healthy chest X-Ray images. This means that there are some patterns and differences between a normal Pneumonia and a COVID-19 Pneumonia. On the other hand, we have seen that data augmentation has helped us to improve Covid-19 accuracy. This tell us that there is not enough data and there is a need of collecting more data (real or not) in order to improve the results. 

Another interesting approach would be to collect more information about patients, like their age, gender, pathologies, etc. This information could be included in the model using different techniques or a simple concatenation of features.
