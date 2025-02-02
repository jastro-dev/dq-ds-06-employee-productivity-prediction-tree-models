# Employee Productivity Prediction

This project aims to predict employee productivity using machine learning techniques. We analyzed a dataset of garment worker productivity to understand the factors that influence output.

## Project Structure

The project consists of the following:

*   `main_notebook.ipynb`: The Jupyter Notebook containing the data analysis, model building, and results.
*   `data/garments_worker_productivity.csv`: The dataset used for the analysis.

## Key Features

*   **Data Cleaning**: Handles missing data, corrects errors, and prepares the dataset.
*   **Data Classification**: Creates a binary target variable for classifying productive and unproductive employees
*   **Model Building**: Implements and tests various machine learning models, including Decision Trees, Random Forests, and XGBoost.
*   **Model Evaluation**: Assesses models with accuracy scores, classification reports, and confusion matrices.
*   **Class Balancing**: Addresses class imbalance issues by re-balancing the data and re-evaluating the model's performance.
*   **Visualization**: Provides visual representation of target distributions and feature importance.

## Implementation Notes

*   The core of this project is implemented in a Jupyter Notebook, which allows for step-by-step analysis, code execution and explanation.
*   The notebook is structured to perform exploratory data analysis, data cleaning, model building, and evaluation.
*   The notebook also contains an optional class-balancing section, which can be enabled by altering the `BALANCE_CLASSES` variable within the notebook's first code block. This will re-train and re-evaluate the Random Forest model with grid search using a class-balanced dataset.
*  The main focus of the notebook is oriented towards showcasing the importance of proper data exploration, preprocessing, and the considerations that should be taken with the data when creating a model.

## Data

The dataset is sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Productivity+Prediction+of+Garment+Employees) and includes information about:

*   **date**: The date of the production record.
*   **quarter**: The quarter of the year.
*   **department**: The department (sewing or finishing).
*   **day**: The day of the week.
*   **team**: The team number.
*   **targeted_productivity**: The target productivity set for each team.
*   **smv**: The standard minute value (time allocated for a task).
*   **wip**: Work in progress (number of unfinished items).
*   **over_time**: Overtime hours.
*   **incentive**: Financial incentives given to the team.
*   **idle_time**: Time when production was interrupted.
*   **idle_men**: Number of idle workers during interruptions.
*   **no_of_style_change**: Number of changes in product style.
*   **no_of_workers**: Number of workers on the team.
*  **actual_productivity**: The actual productivity achieved by the team.

## Analysis

We performed the following steps to prepare the data for analysis:

*   **Cleaned inconsistencies:** Corrected typos and inconsistencies in the data (e.g., "sweing" to "sewing").
*   **Handled missing values**:  Replaced missing "work in progress" (wip) values with 0, assuming no work in progress for the finishing department.
*   **Corrected abnormal values:** Capped maximum actual productivity values to 1 (100%).
*   **Created a target variable:**  Created a new column to classify each observation, either as `productive` if actual productivity met or exceeded target productivity or `unproductive` if it did not.

## Modeling

We used machine learning models to predict whether a team would meet their productivity targets. These included:

*   **Decision Trees:** Simple models that use a tree-like structure to make decisions, which allow us to identify key features.
*   **Random Forest:** An ensemble of decision trees that can provide more accurate predictions.
*   **XGBoost:** A more complex algorithm to try for higher performance.

## Results

*   The **Random Forest model with hyperparameter tuning** was the most accurate (83% accuracy on test data) at predicting if a team would meet their targets.
*   Key features that influenced the model's predictions include: `incentive`, `smv`, `no_of_workers`, `wip`, and `over_time`.

## Class Balancing

*   We noticed that our data contained more "productive" than "unproductive" observations, which could bias the model.
*   We attempted to balance the classes to improve the ability to predict `unproductive` cases, which resulted in better recall for `unproductive` at the cost of overall accuracy.

## Recommendations

*   The Random Forest model can be used to predict which teams are likely to miss their productivity targets.
*   Using the class-balanced version of the Random Forest model may be more beneficial for identifying at-risk teams
*   Focus on optimizing factors like `incentive`, `smv`, `no_of_workers`, `wip`, and `over_time` which had the biggest influence in our models.

## Limitations

*   Our dataset was relatively small, which may have hindered the performance of more complex models like XGBoost.
*   Class imbalance also caused our models to be biased towards predicting `productive` entries, which can be mitigated using the method of class balancing.
*   The limited number of features may have limited the models predictive capabilities

## Next Steps

*   Gather more data to improve model accuracy and robustness.
*   Experiment with feature engineering by combining existing features or creating new ones.
*   Further optimize model hyperparameters to potentially fine tune predictive capabilities.
*   Continue to test a combination of existing features and compare its effect on the model's overall performance.