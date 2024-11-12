# Defining Mid-Point Deliverable

<p align="justify">
As part of the larger Climate TRACE Program, which aims to predict global greenhouse gas (GHG) emissions across all sectors, our project focuses on estimating the Energy Usage Intensity (EUI) as a foundational element for calculating GHG emissions from buildings. This semester, we plan to achieve three key milestones in the initial phase. First, we will identify and create new feature inputs relevant to building energy consumption, extending beyond those used in prior research. Second, we will develop a replicable pipeline for model training, validation, and prediction, enabling future estimations of EUI based on these new inputs and portions of ground truth data. Lastly, we will integrate a model evaluation step within the pipeline to compare predicted values against ground truth data and assess model performance.
</p>

<p align="justify">
To accomplish these milestones, we will establish a GitHub repository named Capstone-Team-Climate-Trace. This repository will contain the model prediction pipeline code, predicted EUI results in a geospatial format, a comprehensive project report outlining our process, and visualizations of predicted EUI values globally. From a business perspective, this repository is designed for government agencies interested in understanding our approach, enhancing it, and deploying this pipeline for future GHG emission assessments.
</p>

## Github Repository Strcuture
```
├── README.md
├── data
│   ├── interim
│   │   ├── HDD.csv
│   │   └── HDD_test.csv
│   ├── processed
│   │   └── merged_df.csv
│   └── raw
│       ├── HDI_educationalIndex_incomeIndex.csv
│       ├── download.nc
│       ├── gdp_data.csv
│       └── population.csv
├── notebooks
│   ├── 01_DataPreprocessing.ipynb
│   ├── 02_HDDProcessing.ipynb
│   ├── 03_Humidityrocessing.ipynb
│   ├── 04_Model.ipynb
│   └── 05_Plots.ipynb
├── reports
└── results
    ├── results_20241109_0818_all_domain_knn.csv
    ├── results_20241109_0818_all_domain_lr.csv
    ├── results_20241109_0818_cross_domain_knn.csv
    ├── results_20241109_0818_cross_domain_lr.csv
    ├── results_20241109_0818_total_knn.csv
    ├── results_20241109_0818_total_lr.csv
    ├── results_20241109_0818_within_domain_knn.csv
    └── results_20241109_0818_within_domain_lr.csv
```

Deliverable: `README.md`
<p align="justify">

**Purpose** : Serves as the main entry point for the repository, guiding stakeholders through the project’s structure and providing setup instructions.
**Goal**: The README makes it easy for stakeholders to navigate the repository, access the necessary files, and understand the project’s objectives.
</p>

## Milestone 1: Feature Creation and Data Collection
<p align="justify">
The first milestone involves gathering and creating new feature inputs beyond those used in prior research to capture factors impacting building energy consumption. This stage includes sourcing raw data from diverse areas, such as climate, economic, and population metrics. The goal is to enrich the dataset, thus enhancing the model's ability to accurately predict Energy Usage Intensity (EUI) and providing insights into the underlying drivers of building-related greenhouse gas emissions.
</p>


<p align="justify">
Why and how to:
	To ensure consistent and high-quality data input to support accurate model predictions, we create a folder for found feature data file, these data files later were preprocessed as input feature for model consumption. But there is restriction related to Big File Upload on Github. So we had a backup storage for our “oversized” data, which is Google Drive. And there is third situation that some data can be only downloaded from official website through API endpoint, which we would directly read and process within our pipeline model files.
</p>

`data/raw/` Folder

`HDI_educationalIndex_incomeIndex.csv`, `download.nc`, `gdp_data.csv`, `population.csv`

<p align="justify">

**Purpose**: These raw datasets are collected from various sources to capture a range of factors, including economic indicators (GDP data), population density, and climate variables (temperature, humidity).
</p>
<p align="justify">

**Utility**: These files provide the foundational data from which features will be engineered, ensuring the model has comprehensive inputs related to environmental and socioeconomic conditions.
</p>

`01_DataPreprocessing.ipynb`
<p align="justify">

**Purpose**: This notebook is responsible for cleaning, integrating, and standardizing the raw datasets.

**Utility**: A well-processed dataset ensures consistency, reducing the risk of errors in the modeling stage. This step is essential for preparing reliable input data to model EUI accurately.
</p>

`02_HDDProcessing.ipynb`
<p align="justify">

**Purpose**: This file calculates Heating Degree Days (HDD) as a feature reflecting energy demand for heating in buildings.

**Utility**: HDD values give insight into temperature-related energy needs, which is critical for predicting energy intensity in cold climates, aligning well with stakeholder interests in understanding seasonal emission patterns.
</p>

`03_HumidityProcessing.ipynb`
<p align="justify">

**Purpose**: Processes humidity data to generate a feature that reflects climate influence on energy consumption.

**Utility**: Humidity affects cooling needs, particularly in warmer regions. Including this feature enriches the model’s environmental understanding, making predictions more relevant to stakeholders.
</p>

## Milestone 2: Model Training and Validation Pipeline
<p align="justify">
The second milestone is dedicated to building a robust pipeline for training, validating, and testing the EUI prediction model. This pipeline is designed for replicability, enabling future users to apply the model to new data using the newly created feature inputs. This milestone is crucial because it sets the foundation for an efficient and scalable approach to estimate EUI, helping stakeholders quickly assess emissions with new data.
</p>

`data/processed/merged_df.csv`
<p align="justify">

**Purpose**: The cleaned and processed dataset that combines all relevant features.

**Utility**: This file serves as the final input for the model training, ensuring that the data is both comprehensive and standardized for effective modeling.
</p>

`04_Model.ipynb`
<p align="justify">

**Purpose**: Trains the machine learning model using the `merged_df.csv`, applying techniques to maximize model accuracy.

**Utility**: This model is the core tool for estimating emissions. Stakeholders rely on it to produce actionable insights, making it vital for the model to be both accurate and reliable.
</p>

## Milestone 3: Model Comparison and Performance Evaluation
<p align="justify">
The final milestone adds a comparison component to the pipeline, allowing the predicted data to be evaluated against ground truth data. This step enables the team to assess the model's accuracy and reliability, providing stakeholders with performance metrics that support confidence in the model’s outputs. The performance evaluation is essential for validating the model before deploying it for large-scale, real-world emissions predictions.
</p>

`results/` Folder

<p align="justify">

Files: Contains multiple result files (e.g., `results_20241109_0818_all_domain_knn.csv`, `results_20241109_0818_cross_domain_lr.csv`) reflecting various model configurations and their outputs.
**Purpose**: Stores the model’s output files, categorized by different domains and model types (e.g., KNN, linear regression).

**Utility**: These files provide a comparative basis for evaluating which models perform best under different conditions, enabling us to choose the most suitable approach for our needs for further predict generation.
</p>

`06_Plots.ipynb`
<p align="justify">

**Purpose**: Generates visualizations, such as ground truth data point distribution, geographic heatmaps plots, to illustrate the spatial and temporal patterns in emission data.

**Utility**: Visualizations help stakeholders intuitively explore and understand the model’s predictions, supporting effective communication of emission trends and hotspots.
</p>

`reports/` Folder
<p align="justify">

**Purpose**: Contains summaries and analyses of model performance, offering detailed insights into accuracy, model comparisons, and findings.

**Utility**: These reports offer stakeholders clear and concise information on model reliability, supporting informed decision-making based on data-driven insights.
</p>

