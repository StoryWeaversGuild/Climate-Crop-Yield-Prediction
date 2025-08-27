# **Crop Yield Prediction using Machine Learning**

This project focuses on predicting crop yield based on various agricultural and environmental factors. By leveraging machine learning models, it aims to provide accurate predictions that can assist in agricultural planning and decision-making.

## **📝 Introduction**

The primary goal of this project is to build a robust machine learning model that can accurately predict crop yield. The model is trained on a dataset containing historical data on crop production, weather patterns, and the use of agricultural inputs like fertilizers and pesticides. The final model is a stacked ensemble of XGBoost and CatBoost regressors, which has demonstrated high accuracy in predicting crop yields.

## **📊 Dataset**

The dataset used in this project, crop\_yield.csv, contains the following features:

* **Crop**: The type of crop grown.  
* **Crop\_Year**: The year of cultivation.  
* **Season**: The season of cultivation (e.g., Kharif, Rabi).  
* **State**: The state where the crop was grown.  
* **Area**: The area of land used for cultivation.  
* **Production**: The total production of the crop.  
* **Annual\_Rainfall**: The annual rainfall in the region.  
* **Fertilizer**: The amount of fertilizer used.  
* **Pesticide**: The amount of pesticide used.  
* **Yield**: The crop yield (target variable).

## **⚙️ Methodology**

The project follows a structured machine learning workflow:

### **1\. Data Preprocessing**

* **Categorical Feature Encoding**: The categorical features (Crop, Season, and State) are converted into numerical format using LabelEncoder.  
* **Feature Scaling**: The numerical features are scaled using StandardScaler to ensure that all features contribute equally to the model's performance.

### **2\. Model Architecture**

* **Base Models**:  
  * **XGBoost Regressor**: A powerful gradient boosting algorithm known for its performance and speed.  
  * **CatBoost Regressor**: Another gradient boosting algorithm that handles categorical features effectively.  
* **Stacking Ensemble**:  
  * A StackingRegressor is used to combine the predictions of the XGBoost and CatBoost models.  
  * A Ridge regressor is used as the meta-model to make the final prediction based on the outputs of the base models.

## **📈 Results**

The stacked ensemble model achieved the following performance on the test set:

* **R² Score**: 0.94  
* **Root Mean Squared Error (RMSE)**: 218.95

These results indicate that the model can explain 94% of the variance in crop yield and has a relatively low prediction error.

## **🚀 Usage**

To use the trained model for predictions, you can load the saved model and encoders using joblib:

import joblib

\# Load the model and encoders  
stacked\_model \= joblib.load('xgb\_crop\_model.pkl')  
crop\_encoder \= joblib.load('Crop\_encoder.pkl')  
season\_encoder \= joblib.load('Season\_encoder.pkl')  
state\_encoder \= joblib.load('State\_encoder.pkl')

\# Prepare your input data and make predictions  
\# ...

## **📦 Dependencies**

The following Python libraries are required to run this project:

* pandas  
* matplotlib  
* seaborn  
* scikit-learn  
* xgboost  
* catboost  
* joblib