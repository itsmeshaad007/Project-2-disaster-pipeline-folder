# Disaster Response ETL, ML pipelines and Web application.

## Motivation
The project's goal is to create an API model that can classify disaster messages, allowing emergency workers to input new messages and receive classification results in various categories such as "water," "shelter," and "food," helping them identify the type of aid required. In addition, the web application presents data visualizations.

![6 visual](https://user-images.githubusercontent.com/121497007/235472304-4f4db1a8-817f-4360-8e06-acd6d7a8c3ae.png)

This project is a web application that categorizes text messages related to disaster events into one or more of 35 possible categories. The project uses machine learning algorithms to classify the messages and display the results on a web page. This README file provides instructions on how to run the project and an overview of its code and data.

## Dependencies
The following Python libraries are required to run this project:

NumPy
Pandas
Matplotlib
Json
Plotly
Nltk
Flask
Sklearn
Sqlalchemy
Sys
Re
Pickle
Additionally, you will need to have software installed to run and execute an iPython Notebook.

## Code and data
This project consists of the following files:

* process_data.py: This code extracts data from both CSV files, messages.csv (containing message data) and categories.csv (containing classes of messages) and creates an SQLite database containing a merged and cleaned version of this data.
* train_classifier.py: This code takes the SQLite database produced by process_data.py as input and uses the data contained within it to train and tune a machine learning model for categorizing messages. The output is a pickle file containing the fitted model. Test evaluation metrics are also printed as part of the training process.
* ETL Pipeline Preparation.ipynb: This Jupyter notebook was used in the development of process_data.py. process_data.py automates this notebook.
* ML Pipeline Preparation.ipynb: This Jupyter notebook was used in the development of train_classifier.py. In particular, it contains the analysis used to tune the machine learning model and determine which model to use. train_classifier.py automates the model fitting process contained in this notebook.
* disaster_messages.csv and disaster_categories.csv: These files contain sample messages and categories datasets in CSV format.
templates folder: This folder contains all of the files necessary to run and render the web app.
* custom_transformer.py: This file contains custom functions that were used in ML Pipeline Preparation.ipynb to find the best way of model tuning.

## Running the project
To run the project, follow these steps:

Open a terminal and navigate to the top-level project directory (the one that contains this README).

Run the following command to extract data and create an SQLite database:
python process_data.py disaster_messages.csv disaster_categories.csv DisasterResponse.db

Run the following command to train a machine learning model and create a pickle file containing the fitted model:
python train_classifier.py DisasterResponse.db classifier.pkl

Run the following command to start the web application:
python run.py

Once the application is running, open a web browser and go to http://0.0.0.0:3001/ (if facing problems, try http://localhost:3001).

## Data observations
As can be seen from the test data visualization, most of the classes (categories) are highly imbalanced. This can affect the model's F1 prediction score. Users of this project should take this into consideration and apply measures such as synthetic data generation, model selection and parameter fine-tuning, etc.

![5 visual](https://user-images.githubusercontent.com/121497007/235472870-cca03706-14c5-42e3-9987-ccb22c080753.png)
