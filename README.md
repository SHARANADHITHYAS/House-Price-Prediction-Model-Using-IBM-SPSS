# House Price Prediction Model Using IBM SPSS

## Overview
This repository contains the code and documentation for building a predictive model to estimate house prices in a particular location using IBM SPSS. The model leverages various features of houses, such as size, number of bedrooms, and location, to predict their market prices.

## Steps to Create the Predictive Model

1. **Data Collection and Preparation**
   - Obtained dataset containing house prices and related features.
   - Cleaned the data to remove duplicates and handle missing values.

2. **Data Exploration and Visualization**
   - Generated summary statistics to understand data distribution.
   - Created visualizations (histograms, scatter plots) to explore relationships between features and house prices.

3. **Feature Selection and Engineering**
   - Conducted correlation analysis to identify important features.
   - Created new features like price per square foot.

4. **Model Building and Training**
   - Split data into training and testing sets.
   - Selected and trained the model using SPSS's regression tools.

5. **Model Evaluation**
   - Evaluated model performance using metrics like MAE, MSE, and R-squared.
   - Used cross-validation for model validation.

6. **Deployment and Predictions**
   - Exported the trained model for deployment.
   - Used the model to predict house prices for new data points.

## Using IBM SPSS for Model Building

1. **Import Data**: Load the dataset into SPSS.
2. **Data Cleaning**: Handle missing values using the Data Editor.
3. **Exploratory Analysis**: Utilize Chart Builder and Descriptive Statistics tools.
4. **Feature Selection**: Perform correlation analysis.
5. **Model Training**:
   - Go to `Analyze > Regression > Linear` for linear regression models.
   - Use `Analyze > Classify > Tree` or `Analyze > Classify > Random Forest` for more complex models.
6. **Model Evaluation**: Check output for performance metrics and diagnostic plots.
7. **Save Model**: Export the model for future use.

## Example SPSS Syntax for Linear Regression

```spss
* Load the dataset.
GET FILE='house_prices.sav'.

* Check for missing values and handle them.
MISSING VALUES ALL (SYSMIS).
RECODE ALL (SYSMIS = 0).

* Descriptive statistics.
DESCRIPTIVES VARIABLES=price size bedrooms location.

* Correlation matrix.
CORRELATIONS
  /VARIABLES=price size bedrooms location
  /PRINT=TWOTAIL NOSIG.

* Split data into training and testing sets.
SORT CASES BY RANDOM().
SPLIT FILE BY random(2).
FILTER BY random(2).

* Linear regression model.
REGRESSION
  /DEPENDENT price
  /METHOD=ENTER size bedrooms location
  /SAVE PRED (predicted_price).

* Evaluate model.
EXAMINE VARIABLES=price predicted_price
  /PLOT BOXPLOT STEMLEAF NPPLOT.

