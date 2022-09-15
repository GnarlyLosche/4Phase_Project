# 4Phase_Project

# Overview

For the fourth phase, I put everything I've learned together to build a deep neural network that trains on a large dataset for classification on a non-trivial task. In this case, using x-ray images of pediatric patients to identify whether or not they have pneumonia. The dataset comes from Kermany et al. on Mendeley

The images are split into a training set and a testing set of independent patients. Images are labeled as (disease)-(randomized patient ID)-(image number by this patient)

# Steps to utilize data

In order to get the data into the model for this repository, create a folder called Data in the main directorty and download/extract the images from this link: [link](https://data.mendeley.com/datasets/rscbjbr9sj/3)

Once the data is downloaded and extracted and the internal folders are in your creadet 'Data' folder, create an additional validation forlder that has two sub folders for NORMAL and PNEUMONIA images, matching the file structure in the train and test folders. Frome there, move the bottom 25% of images in the train folder for both NORMAL and PNEUMONIA into their respective folders in the validation folder. With this file structure you can run the model.


# Key facts

- Pneumonia accounts for 14% of all deaths of children under 5 years old, killing 740 180 children in 2019
- Pneumonia can be caused by viruses, bacteria, or fungi.
- Pneumonia can be prevented by immunization, adequate nutrition, and by addressing environmental factors.
- Pneumonia caused by bacteria can be treated with antibiotics, but only one third of children with pneumonia receive the antibiotics they need.
- Pneumonia is a form of acute respiratory infection that affects the lungs. The lungs are made up of small sacs called alveoli, which fill with air when a healthy person breathes. When an individual has pneumonia, the alveoli are filled with pus and fluid, which makes breathing painful and limits oxygen intake.


**Pneumonia is the single largest infectious cause of death in children worldwide.**

Pneumonia killed 740 180 children under the age of 5 in 2019, accounting for 14% of all deaths of children under five years old but 22% of all deaths in children aged 1 to 5. Pneumonia affects children and families everywhere, but deaths are highest in South Asia and sub-Saharan Africa. Children can be protected from pneumonia, it can be prevented with simple interventions, and treated with low-cost, low-tech medication and care.

# Business Area

Rural Hospitals and population-dense hospitals in Sri Lankajust recieved a large grant from the Bill and Melinda Gates foundation to purchase X Ray Machines for their practices. One of the largest problems present in these areas is the prevalence of pneumonia in their pediatric population, and the level of lethality it has for those children

# Problem
The Gates Foundation has the capital to provide the doctors with XRay Machines, but doctors have been widely complaining and criticizing the effort due to the huge volume of patients they see every day. The doctors don't have time to review all of the Xrays, and they don't have enough funding to high radiology techs.

In order to solve this issue, the Gates foundation executive director called on us to build a model that can take in the Xray scans of a patient and automatically predict whether that pediatric patient has pneumonia. The Gates foundation envisions this becoming an automated process in which the xray machine atomatically uploads the image as a jpeg to be run through the model, and depending on the result automatically send the patient's family a notification and a prescription for antibiotics if needed.

# Deliverables
1. Model to predict pneumonia based on Xray imaging
2. Deck Outlining Process and model development
3. Github Repo Containing all information leading to model development

# Business and data understanding:

- We are using pediatric Xray images taken in 2018 to train the model. These images serve as a strong data set due to the number of images (over 5,000), and because the data is easily tagged as normal or pneumonia

# Data preparation*:
- I took the mendeley dataset and further created a validation dataset to train the data upon, as well as only used the grayscale images. These steps allowed me to reduce computational power while also reserving a dataset to prove utility on unseen data.

# packages/libraries used*
- tensorflow and Keras were used to perform the modeling steps, and to build the convolutional neural network
- I used matplot and seaborn to visualize the loss and accuracy of the model as I iterated in order to effectively tune the model

# Modeling:
- My neural net used 3 layers of convolutional neural networks
- The model was built using adam as the optimizer rather than SGD. I don't have a massive data set, and the loss/accuracy was better with the adam optimizer so I stayed with it for the final model
- I used an L2 regularizer since the model had overfitting issues I wanted to address overfitting
- I added a dropout layer at the end to make sure my model wasn't performing porrly/ensuring randomization allowed for better generalizations to reduce 
- Ultimately I added a data augmentation layer into the model to transform the data by both rotating it by 20% and flipping it across both axes during each epoch. The intention was to avoid memorizing the training data.

# Evaluation: 
- final precision was 89%
- final recal was 96%
- final accuracy was 90%
- my model's mean average performance on test data (evaluate method) was loss: 0.3329 - accuracy: 0.9054
