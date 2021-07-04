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
├── reports          <-- Generated analysis (including presentation)
│
└── README.md        <-- Main README file explaining the project's purpose, methodology, and findings

```




## Data Source
The data used in this analysis was original provided by Mendeley Data and is publicly available [here](https://data.mendeley.com/datasets/rscbjbr9sj/3) (1). The dataset was subsequently adapted to a Kaggle dataset, which can be found [here](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia).

In total, 5856 X-ray images in jpeg format are provided. Each is already labeled to indicate whether or not pneumonia is present.



## Data Understanding
After 



## Modeling
 


## Evaluation



## Conclusion




## Further Investigation
This investigation leaves several aspects of the analysis underdeveloped, leaving space for expanded future analysis. 

- Extensive grid-based hyperparameter tuning

- Testing generic pre-defined neural networks

- Increasing resolution of images. Currently they are downsampled substantially to prevent RAM issues.
