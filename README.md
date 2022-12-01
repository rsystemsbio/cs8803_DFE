# cs8803_DFE
# Identification of Optimal Features for Effective COVID-19 Disease Forecasting with Machine Learning Models


This codebase will allow a user to set up a combined table with google search term data, mobility data, and facebook survey data. With this combined data, the user can run a shap and ablation analysis to see important features in the dataset. The states of interest are California, Texas, Georgia, Massachusetts, and Florida. If more states would be like be evaluated, they can be added to the state_list variable in the run scripts. To see the results of the analysis, the Final_Report.pdf document is stored in the DOCS folder.  

There are three primary scripts. The get_data.py script pulls the data from the COVIDcast API and combines it with the symptom data. The symptom data must be downloaded and placed in the data folder by the user. Do not change the name of the file once it is downloaded. The run_shap.py script takes the combined_set.csv and trains three models compatible with SHAP: Xgboost, Random Forest, Linear Regression. The SHAP results are output in the plots folder and the model training results are shown in the command line. The run_ablation.py takes the combined_set.csv and performs ablations on the dataset at 25 features at a time for the Xgboost model. The results are stored in the plots folder for the MAE and RSME over the number of features provided. 

## Setup

To get the symptom search data, follow these links and place the files in the **data** folder. 

* [2020 Symptom data](https://storage.cloud.google.com/gcs-public-data---symptom-search/2020/country/daily/2020_US_daily_symptoms_dataset.csv)
* [2021 Symptom data](https://storage.cloud.google.com/gcs-public-data---symptom-search/2021/country/daily/2021_US_daily_symptoms_dataset.csv)
* [2022 Symptom data](https://storage.cloud.google.com/gcs-public-data---symptom-search/2022/country/daily/2022_US_daily_symptoms_dataset.csv)


Use the package manager [pip](https://pip.pypa.io/en/stable/) to install the necessary packages.

```bash
pip install covidcast umap-learn pandas matplotlib seaborn numpy xgboost colorcet shap scikit-learn 
```

## Usage

To get the data and generate the UMAP, run the following command:

```bash
python get_data.py
```
To make sure that it worked, check the data folder and look for a file called combined_set.csv. To train the models for the SHAP analysis, run the following command:
```bash
python run_shap.py
```
The plot outputs will be stored in the plots folder. The resulting RSME and MAE for each trained model will be printed in the command line output. 

To run the ablation analysis, run the following command:
```bash
python run_ablation.py
```
The plot outputs will be stored in the plots folder. The resulting RSME and MAE for Xgboost will be printed in the command line output.
