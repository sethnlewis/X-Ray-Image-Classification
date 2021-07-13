# X-Ray Image Classification: Identifying Pneumonia 

## Introduction
The purpose of this analysis is to design a model that can use chest x-ray images to identify pneumonia. According to the American Thoracic Society, pneumonia is the [leading cause of death](https://www.thoracic.org/patients/patient-resources/resources/top-pneumonia-facts.pdf) among children under age 5, accounting for roughly 16% of all deaths within that age range in 2015. The application of machine learning techniques such as neural networks can help identify the presence of pneumonia using exclusively chest x-rays. 


**Repository Directory**

```

│                        
├── data             <-- Data in CSV format
│   └── raw          <-- Original (immutable) data dump
│
├── images           <-- Figures used in presentation and notebooks
│
├── notebooks        <-- Jupyter Notebooks for exploration and presentation
│
├── report           <-- Generated analysis (including presentation)
│
└── README.md        <-- Main README file explaining the project's purpose, methodology, and findings

```




## Data Source
The data used in this analysis was original provided by Mendeley Data and is publicly available [here](https://data.mendeley.com/datasets/rscbjbr9sj/3) (1). The dataset was subsequently adapted to a Kaggle dataset, which can be found [here](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia).



## Data Understanding

In total, 5856 X-ray images in jpeg format are provided. Each is placed in a folder corresponding to whether or not the patient had pneumonia. Examples can be seen below.

#### No pneumonia (healthy) 
 <img src="https://github.com/sethschober/X-Ray-Image-Classification/blob/main/images/xrays_pneumonia.png" width="500">


#### Pneumonia
<img src="https://github.com/sethschober/X-Ray-Image-Classification/blob/main/images/xrays_normal.png" width="500">

To an untrained eye, it can be incredibly difficult (if not impossible) to classify each of these images as with or without pneumonia. 

-----

Although the images were split into *train*, *validation* and *test* folders by the original source, there is controversy that some of the images in the *test* folder were incorrectly classified. In the EDA phase of this project, this finding was determined to be likely. The was determined by training and evaluating the models in two separate ways:
1. Using the original train-test split, the model accuracy was in the 70-75% range. 
2. Importing train and test data into one array, then performing a train-test split within the code, the model accuracy jumped to 93-98%. 

Note that the jump in accuracy (and other performance metrics to a similar extent) was not due to data leakage. It was not due to model alterations. The same findings were validation using multiple different randomized train-test splits. 


## Modeling
 The analysis explores seven different iterations of neural networks to find the highest performance. Models started as simple as one dense layer with two nodes. Throughout the process, different layers with different hyperparameters were strategically added. Improvements included 2D convolutional layers, regularization, pooling and dropout. After substantial tuning, a model was developed that demonstrated very little overfitting due to consistent use of regularization, pooling and dropout. Below, the accuracy is shown across the range of epochs while the model was training. 
 
 <img src="https://github.com/sethschober/X-Ray-Image-Classification/blob/main/images/performance_over_epochs_accuracy.png" width="500">


## Evaluation
After running each of the models using an array of hyperparameters, the top performing model was selected. It was composed of 3 Convolutional layers, each of which were followed by a Pooling and Dropout layer. The model architecture can be seen below. 

<img src="https://github.com/sethschober/X-Ray-Image-Classification/blob/main/images/neural_network_diagram.png" width="335">


Further, the below images show the performance of this final model in the form of a confusion matrix. The first shows the actual numbers of images in each classification category, whereas the second shows those values normalized.

<img src="https://github.com/sethschober/X-Ray-Image-Classification/blob/main/images/best_model_confusion_matrix_count.png" width="450">

<img src="https://github.com/sethschober/X-Ray-Image-Classification/blob/main/images/best_model_confusion_matrix_percent.png" width="450">



## Conclusion
Taking a step back, the investigation successfully led to a model that can classify pneumonia based on a single chest x-ray with approximately 96% accuracy. Of note, the algorithm only "missed" 2% of all cases, representing the False Negative portion of the confusion matrix. This metric is especially important in medical applications because telling a patient they are healthy when in fact they are not is the worst possible outcome.

In addition to high performance of the final model, the process proved effective in overall performance improvements across the board both from the baseline model and the first simple model. The final model also showed only small signs of overfitting, largely due to regularization and dropout, which makes for a versatile, more widely applicable model. 


### Future improvements
Although the above models are high performers, there is always room for improvement or further exploration. Some of those possibilities are discussed below.

- **Increase image resolution:** currently, photos are downsampled from roughly 800x1200 pixels to roughly 200x200 pixels. This choice was made to enable the script to run without crashing due to memory shortages. This issue is inherent to the methodology used to the images being stored in memory as a numpy array. However, analyzing these images in "batches" would eliminate the need to store an array in memory. As a result, more data could be analyzed. With more data, presumably the model could be more effective. 
- **Hyperparameter grid searches:** currently, ideal hyperparameters were selected based on some fine tuning and outside research. Note that not all iterations of those models are included in this notebook so that the notebook can run in a reasonable amount of time. An exhaustive hyperparameter optimization is necessary to truly identify the top performing model, but that will be left for future analyses with more computational resources. 

### Citations
(1) Kermany D, Goldbaum M, Cai W et al. Identifying Medical Diagnoses and Treatable Diseases by Image-Based Deep Learning. Cell. 2018; 172(5):1122-1131. doi:10.1016/j.cell.2018.02.010.
