Beijing Multisite Air Quality Analysis & PM2.5 Prediction

This project uses a Jupyter Notebook (BMAQ.ipynb) to analyze, visualize, and model the Beijing Multisite Air Quality dataset. The primary goal is to predict the concentration of PM2.5 (a key air pollutant) based on other meteorological and pollution data.

📋 Dataset

This project uses the Beijing Multisite Air Quality Data Set from the UCI Machine Learning Repository.

Source: UCI Machine Learning Repository: Beijing Multisite Air Quality Data

Description: The dataset contains hourly air quality data from 12 monitoring sites in Beijing, spanning from March 1st, 2013, to February 28th, 2017.

Columns: Includes measurements for PM2.5, PM10, SO2, NO2, CO, O3, as well as meteorological data like TEMP, PRES, DEWP (dew point), RAIN, wd (wind direction), and WSPM (wind speed).

Column Definitions

PM2.5: Fine particulate matter (particles ≤ 2.5 micrometers). This is the target variable for prediction.

PM10: Inhalable particulate matter (particles ≤ 10 micrometers).

* SO2: Sulfur Dioxide.

* NO2: Nitrogen Dioxide.

* CO: Carbon Monoxide.

* O3: Ozone.

* TEMP: Temperature (in degrees Celsius).

* PRES: Atmospheric Pressure (in hPa).

* DEWP: Dew Point Temperature (in degrees Celsius).

* RAIN: Hourly precipitation (in mm).

* wd: Wind Direction (categorical, e.g., 'N', 'NW').

* WSPM: Wind Speed (in meters/second).

Note: The notebook BMAQ.ipynb assumes the data file is named Beijing Multisite air Quality data.csv.

🔬 Project Workflow (Notebook Structure)

The analysis is contained entirely within the BMAQ.ipynb notebook and follows these steps:

Imports: Loads all necessary libraries (pandas, numpy, matplotlib, sklearn).

Data Loading: Loads the .csv file into a pandas DataFrame.

Basic Exploration: Checks the data's shape, views the first few rows (.head()), and inspects data types and missing values (.info(), .isnull().sum()).

Cleaning & Feature Engineering:

Identifies PM2.5 as the target variable.

Handles missing values by dropping rows where the target (PM2.5) is missing and filling other numeric NaNs with the median.

Constructs a datetime object from the year, month, day, and hour columns for potential time-series analysis (though it's primarily used as separate features in the model).

Visualization:

Plots a histogram to show the distribution of the target variable, PM2.5.

Generates scatter plots to visualize the relationship between PM2.5 and other key features (e.g., PM10, SO2, NO2).

Modeling:

Prepares the data by separating features (X) and the target variable (y).

Splits the data into training (80%) and testing (20%) sets.

Applies StandardScaler to the features for the Linear Regression model.

Builds and trains two regression models:

Linear Regression

Random Forest Regressor (n_estimators=100)

Evaluation & Results:

Evaluates both models on the test set using Root Mean Squared Error (RMSE) and R-squared (R2).

Extracts and displays the top 10 most important features from the Random Forest model.

📊 Results & Key Findings

The models were evaluated to predict PM2.5 concentrations. The Random Forest model significantly outperformed the Linear Regression model.

Model

RMSE

R-squared (R2)

Linear Regression

1052.193

0.839

Random Forest

349.024

0.947

Feature Importance

The Random Forest model identified PM10 as the most significant predictor for PM2.5, which is expected as they are both particulate matter.

Feature

Importance

PM10

0.7981

CO

0.0990

DEWP

0.0196

SO2

0.0152

TEMP

0.0134

PRES

0.0106

NO2

0.0101

O3

0.0084

year

0.0066

WSPM

0.0062

⚖️ Model Performance Comparison

The Random Forest Regressor was the clear winner, performing significantly better than the Linear Regression model.

R-squared (R2): The Random Forest explained 94.7% of the variance in PM2.5 levels, while the Linear Regression only explained 83.9%. A higher R2 value indicates a better fit.

Root Mean Squared Error (RMSE): The Random Forest's predictions were, on average, off by ~349 units, whereas the Linear Regression's predictions were off by ~1052 units. A lower RMSE is better.

Why did Random Forest perform better?

Non-linearity: Air pollution is a complex phenomenon. The relationships between features (like temperature, wind speed, and other pollutants) and PM2.5 are not strictly linear. A Linear Regression model can only capture straight-line relationships.

Feature Interactions: Random Forest (an ensemble of decision trees) is excellent at automatically capturing complex interactions between features (e.g., the effect of wind speed might change depending on the wind direction). A standard Linear Regression model does not do this.

Robustness: The Random Forest model is less sensitive to outliers in the data compared to Linear Regression.

🚀 How to Run This Project

Clone the Repository:

git clone [https://github.com/your-username/your-repository-name.git](https://github.com/your-username/your-repository-name.git)
cd your-repository-name




Install Requirements:
Make sure you have Python 3 and the following libraries installed. You can install them using pip:

pip install pandas numpy matplotlib scikit-learn jupyter




(Or create a requirements.txt file with the list above and run pip install -r requirements.txt)

Download the Data:

Go to the UCI Dataset Page.

Download the data folder.

Extract the contents. Find the file named Beijing Multisite air Quality data.csv and move it into the root of this project folder.

IMPORTANT: Update Notebook Path

Open BMAQ.ipynb.

Go to Cell 3 (the one with pd.read_csv(...)).

The notebook currently has a hardcoded local path:
df = pd.read_csv(r"C:\Users\USER\Desktop\PROJECT 001\Beijing Multisite air Quality data.csv")

Change this line to read the local file you just downloaded:

# (Cell 2 has a placeholder variable, but Cell 3 uses a hardcoded path.
# We will fix Cell 3.)

# Change this line in Cell 3:
df = pd.read_csv("Beijing Multisite air Quality data.csv")




Run Jupyter:

In your terminal, run:

jupyter notebook





Open BMAQ.ipynb in your browser and run the cells.
