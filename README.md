# Using AI to diagnose patients with pneumonia
<p align="center">
  <img src="https://github.com/Jko0425/Phase_4_project_image_recognition/blob/main/Images/chestxrays.jpg" width="1000" />
</p>

By: Joshua Ko
<br>Email: joshuawko@gmail.com
## Repository Structure
```bash
Phase_4_project_image_recognition/
├─ Image/
│  ├─ Confusion matrix.png
│  ├─ Metrics vs. Epoch.png
├─ .gitignore
├─ Image recognition of patients with pneumonia.ipynb
├─ README.md
├─ Using the Vgg16 model to separate pneumonia caused by virus and bacteria.ipynb
├─ presentation.pdf
```
## Structure of data folder in Google Drive
Link for data folder: https://drive.google.com/drive/folders/1LV79q3V7-VUANTYEe2hBgEfdSwolcagd?usp=drive_link
```bash
Data/
├─ Augmented/
│  ├─ NORMAL
│  ├─ PNEUMONIA
├─ Augmented_Virus/
│  ├─ BACTERIA
│  ├─ VIRUS
├─ Chest_xray/
│  ├─ NORMAL
│  ├─ PNEUMONIA
```
## Table of Contents
* [Addressing the shortage of doctors in the US](https://github.com/Jko0425/Phase_4_project_image_recognition/blob/main/README.md#Addressing-the-shortage-of-doctors-in-the-US)
* [About the data](https://github.com/Jko0425/Phase_4_project_image_recognition/blob/main/README.md#About-the-data)
* [Creating the best neural network](https://github.com/Jko0425/Phase_4_project_image_recognition/blob/main/README.md#Creating-the-best-neural-network)
* [Results](https://github.com/Jko0425/Phase_4_project_image_recognition/blob/main/README.md#Results)
* [Conclusion](https://github.com/Jko0425/Phase_4_project_image_recognition/blob/main/README.md#conclusion)
## Addressing the shortage of doctors in the US
The issue with the shortage of doctors predates COVID-19. This resulted in longer wait times, and poorer dynamics between patients and physicians. Additionally, when you factor in that doctors now deal with healthcare administration to give their patients proper care, it is no surprise that we are not getting the proper healthcare that we need. Northwell Health, one of the biggest healthcare providers in New York, needs proper patient care so that patients will not only just follow through with their treatment plans, but also may increase patient compliance. So what can we do to improve our healthcare while lessening the burnout that doctors are experiencing? By implementing AI in these hospitals, we can assuage some of the workload without diminishing patient care. Northwell can also use AI to train inexperienced nurses and doctors, [as multiple studies have found that AI is able to perform just as well as medical experts](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6716335/). This project will focus on developing an AI model that will be able to diagnose a pediatric patient with pneumonia by reading chest xrays. Hopefully the performance of the model will reassure that AI does have a place in the medical field.
## About the data
The data consisted of chest x-rays of pediatric patients with or without pneumonia, provided by [Mendeley Data](https://data.mendeley.com/datasets/rscbjbr9sj/3). The data folder contains three folders: "chest_xray", "Augmented_Virus", and "Augmented". The "chest_xray" has two folders labeled "TRAIN" and "TEST", and each of these folders contain two more folders: "NORMAL" and "PNEUMONIA". However, the dataset in the "TRAIN" folder is unbalanced; the "NORMAL" data is a few thousand less than the "PNEUMONIA" data. In an attempt to balance these data, the augmented folders ("Augmented" and "Augmented_Virus") contain augmented images in order to increase the minority class. Since the "Data" folder is about 2 GB, it will be stored in [Google Drive](https://drive.google.com/drive/folders/1LV79q3V7-VUANTYEe2hBgEfdSwolcagd?usp=drive_link).
## Creating the best neural network
To create the neural network that will return the best accuracy without overfitting, we start with a simple neural network, with only one hidden layer, and observe how the addition or replacement of layers improves the metrics of the model. We graph the metrics of each epoch to observe if there are any overfitting while simutaneously observing the changes in metrics like accuracy. The best model is saved in the file "normal_pneumonia_with_augmented_data.keras". The saved model can be found [here](https://drive.google.com/file/d/1B8m1rsUGkOWHf19led_infZOE2MBhe6x/view?usp=drive_link) as it is several hundred MB.
## Evaluation of the model
When we compare the best model against the simple neural network we see how well the best model performs:
<p align="center">
  <img src="https://github.com/Jko0425/Phase_4_project_image_recognition/blob/main/Images/Comparing%20l2%20and%20cnn%20model.png" width="800" />
</p>

## Results
Running the test set through the saved model yielded this confusion matrix where 0 indicates normal and 1 indicates pneumonia:
<p align="center">
  <img src="https://github.com/Jko0425/Phase_4_project_image_recognition/blob/main/Images/Confusion%20Matrix.png" width="500" />
</p>

* __Precision:__ 0.82
* __Recall:__ 0.96
* __Accuracy:__ 0.84
* __F1:__ 0.88
<br>*Metrics will change when code is rerun but should not change by much
## Conclusion
The results of the model differentiating between a normal and pneumonia lung performed adequately. With a sample size of 2500 images in each class, we were able to achieve an 84% accuracy. A higher recall score is preferred over precision as failing to properly label a sick patient may be harmful to the hospital's reputation. Some problems that have occured during this project are class imbalances and lack of data. Although this is corrected, the method of balancing the class may have not been the best as over 1000 images of the minority class is generated by image augmentation. However, the model is able to differentiate between the two class fairly well.
<br>Northwell can use similar models and approach to develop or enhance existing AI models in order to form a diagnosis. In turn, the healthcare provider may:
* __enhance patient-doctor relationships__
* __reduce doctor burnouts__
* __help develop skills of less experienced doctors__
