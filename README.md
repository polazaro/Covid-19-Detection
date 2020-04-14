# COVID-19 Detection from chest X-Ray images using Convolutional Neural Networks

### Pablo Lázaro Herrasti (lazaroh.pablo@gmail.com)
### Rubén Barco Terrones  (rubate10@gmail.com)

#### Abstract
In 2020, humanity is facing one of the greatest challenges ever seen in the last years because of a virus (Covid-19). An unprecedented pandemic that has millions of people confined at home. In this research, the possibility of detecting this virus in people using chest X-Ray images is studied. (i) A public dataset containing images from Covid-19, viral pneumonia and healthy people is used with (ii) Convolutional Neural Network architecture to be able to differentiate between various medical situations. Finally, (iii) it is revealed graphically the regions on which the CNN focuses in order to determine the medical situations of the person.

#### Introduction
In this work, we have tried to argue about the feasibility of automatically detecting Covid-19 by using chest X-Ray images. **This research does not want to make any medical claim about Covid-19, because this is not our work and is not our purpose**. Our main goal is to study a new way to **help doctors** in their decisions. We are **not trying to replace their knowledge and experience**, we just want to see if this type of tools based on Deep Learning can be exploited by them.

Attending to experts, the main symptoms of the virus are the following: sore throat, cough, fever and difficulty breathing (in severe cases). **In most of the severe cases, the virus is capable of causing pneumonia in the patient**. One of the techniques used to detect pneumonia are chest X-Ray images, among many other, because they provide a very useful insight into the lungs. Is this pneumonia easy to detect? Can we differentiate between a viral pneumonia and a Covid-19 pneumonia? These two questions are the main concepts that this research is trying to solve. In order to bring a solution, some **Deep Learning** techniques are applied.

In this research, we are going to use some **Convolutional Neural Networks (CNNs)**. This network is able to extract these complex features from the samples given to the network and generalize the results with other samples that the network has never seen.

#### Database
The database has been downloaded from a public [Kaggle](https://www.kaggle.com/tawsifurrahman/covid19-radiography-database/data#). The images were collected from different sources and they are truthful images.

![Examples from the database.](https://github.com/polazaro/Covid-19-Detection/blob/master/images/database.bmp)

This database contains chest X-ray images for **COVID-19 positive cases** along with **Healthy** and **Viral Pneumonia** images. In their current release, there are **219 COVID-19 positive images**, **1341 normal images** and **1345 viral pneumonia images**. 

#### Method
For the training processes we have used Keras over Tensorflow an Python. All the architectures have been created, trained and tested from scratch, which means that the weights of the network are initialized randomly and there is not previous information from other data that could help our models to improve their results. 

**First Architecture - Baseline Architecture**
We propose the following baseline CNN:

![Baseline Architecture.](https://github.com/polazaro/Covid-19-Detection/blob/master/images/baseline.bmp)






