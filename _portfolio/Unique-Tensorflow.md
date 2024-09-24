---
title: "Unique Tensorflow architecture"
excerpt: "Created a unique neural network architecture and tested its performance against other established architectures 🧠🕸️. <br/><img src='/images/loopyrnn.jpeg' width='50%'>"
collection: portfolio
order: 5
---

The Google Colab notebook linkd below is focused on a research project involving several neural network models intendent to predict cryptocurrency prices. A brief overview of the key sections and activities are:

- **Setup**: The notebook begins by mounting a Google Drive to access files and importing various Python libraries necessary for data analysis and machine learning.

- **Cleaning Data**: This section deals with preprocessing the cryptocurrency data by removing duplicates and filling in missing data points using linear interpolation.

- **Visualization**: The notebook includes code to visualize the cleaned dataset using candlestick charts, which are commonly used in financial analysis to represent price movements.

- **Normalization**: It discusses the normalization of data using exponential smoothing, a technique to smooth out data for better predictions in time series forecasting.

- **Data Pipeline**: The notebook outlines the creation of a data pipeline using a custom `Window Generator` class, which prepares the data for the machine learning models.

- **Training Parameters**: It sets up training parameters, including the use of the Adamax optimizer and early stopping based on validation loss.

- **Modeling**: Several machine learning models are constructed and trained, including a baseline RNN model, an autoregressive LSTM model, a ClockWork RNN model, and a custom architecture called LoopyRNN.

- **Evaluation**: The models are evaluated based on their performance, particularly using the Mean Absolute Error (MAE) metric.

- **Personal Architecture**: The notebook concludes with the creation of a personal architecture called LoopyRNN, which is an experimental model designed by the notebook's author.

[Repository](https://colab.research.google.com/drive/1hRhKZnoJoxp4uazYOwXVTjAaZdZZI2Ho?usp=sharing).

python libarires: tensorflow, keras, plotty, seaborn, matplotlib, pandas, numpy. 
