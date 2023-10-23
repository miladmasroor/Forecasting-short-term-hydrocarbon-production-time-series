# Forecasting short-term hydrocarbon production time-series with TensorFlow
This repository introduces methodologies for short-to-long term forecasting of hydrocarbon production using TensorFlow. The focus is on building a variety of model styles, including Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs).

The codes are categorized into two primary parts:

1. Forecast for a Single Time Step:
Single Feature Forecast (single_step_and_uni.ipynb): Forecasting using a singular feature.
All Features Forecast (single_step_and_uni.ipynb): Forecasting employing all available features.
2. Forecast Multiple Steps:
Single-shot (multi_step_multi_vari_final.ipynb): This approach makes predictions for the entire future time series in one go.
Autoregressive (multi_step_multi_vari_final.ipynb): This model makes step-by-step predictions, using the output of the last prediction as input for the subsequent forecast.
Hyper-parameter Tuning with Ax:
All the data-driven forecasting techniques applied here have specific hyper-parameters. Properly tuning these hyper-parameters is crucial as they significantly influence the model's accuracy and performance.

In this repository, we've leveraged the Adaptive Experimentation Platform (Ax) for hyper-parameter tuning, focusing on validation samples. Ax is an innovative platform designed to optimize a broad range of experiments, extending from machine learning to simulations. Notably, it's a creation of Facebook and currently stands as part of their Open-Source projects.

Getting Started:
Familiarize yourself with the individual Jupyter notebooks:

single_step_and_uni.ipynb for single time step forecasting.
multi_step_multi_vari_final.ipynb for multiple step forecasting.
Before training any model, ensure to adjust the hyper-parameters using Ax for optimization.

Follow the guidelines and comments in each notebook for a systematic approach to time series forecasting.

We hope this repository aids in comprehending and applying TensorFlow for hydrocarbon production forecasting effectively. Happy forecasting!

# data preparation:

Data windowing: It is supposed that the data-driven approaches presented in this research can build a set of predictions on the basis of the windows of consecutive data samples, which have the following major specifications:
1)	The width (number of time steps) of the label and input windows;
2)	The time offset between them;
3)	The features utilized as labels, inputs, or both.
The purpose of this section is to describe how to generate the data windows in order to develop and train data-driven forecasting techniques using time series data. Depending on the type of model, and the prediction objectives ((i) single-output or multiple-output predictions, (ii) single-time-step or multiple-time-step predictions), we may use different windowing styles. Here are some examples:
Example 1: When you wish to make a single prediction of 24 days into the future based on 24 days of historical data, you can define a window with an input width of 24 days, a time offset of 24 days, and a label width of 1 day.
![1](https://github.com/miladmasroor/Forecasting-short-term-hydrocarbon-production-time-series/assets/79324919/52edfe5b-5a1c-414b-929f-d2a9283d6901)

Example 2: In order to make a prediction of 1 day into the future, given 20 days of historical data, a window should be constructed with an input width of 20 days, a time offset of 1 day, and a label width of 1 day. It is worth noting that production data of this study have been windowed in a similar scheme explained in this example.
![2](https://github.com/miladmasroor/Forecasting-short-term-hydrocarbon-production-time-series/assets/79324919/a92ef4dd-c3bc-4ef1-a211-e5936f923724)

Split window: By employing the split window technique, a list of consecutive inputs is converted to a window of labels and a window of inputs. As the following figure shows, the second example of data windowing, which was defined previously, is divided into a window of labels and a window of inputs.
![3](https://github.com/miladmasroor/Forecasting-short-term-hydrocarbon-production-time-series/assets/79324919/b5208981-6713-4628-91c7-c30f9d7533de)

# Predictive strategy: 
![4](https://github.com/miladmasroor/Forecasting-short-term-hydrocarbon-production-time-series/assets/79324919/3d8ba6dd-1da3-4ecc-b269-c1f251c5a2b2)

# Forecasting process: 
![5](https://github.com/miladmasroor/Forecasting-short-term-hydrocarbon-production-time-series/assets/79324919/35adffea-4d39-442f-af44-72a3273ca7cc)


