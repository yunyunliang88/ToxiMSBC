# ToxiMSBC

This repository contains code for "**ToxiMSBC: A novel deep learning architecture for peptide toxicity prediction based on multi-scale depthwise separable bottleneck convolution.**"


## 1 Description


ToxiMSBC is a deep learning framework for predicting peptide toxicity. First, the model employs ProtT5, a Transformer-based protein language model, to encode peptide sequences. Then, a 1×1 convolution increases the channel dimension, and parallel depthwise separable bottleneck convolutions with kernel sizes of 3, 5, and 7 extract local patterns at different scales. The extracted features are concatenated, fused via a 1×1 convolution, and added to the residual connection. Finally, a fully connected network outputs binary classification probabilities. The model is trained on the training set and demonstrates good predictive performance and generalization ability on independent test sets.



## 2 Software versions and hardware environment
The ToxiMSBC model is implemented and trained within the PyTorch framework. All experiments are conducted on a system equipped with an 11th Gen Intel Core i5-1135G7 processor (operating at a base frequency of 2.40 GHz, with burst capability up to 2.42 GHz) and 16.0 GB of RAM. Training employs the cross-entropy loss function, with parameter optimization carried out via the Adam algorithm. The model is trained for 100 epochs using a batch size of 64 and learning rate of 0.0001.


## 3 Project Structure

*   **`Datasets/`**: Include two types of datasets, namely datasets with similarity thresholds of 0.8 and 0.9.
     - `0.8`:`train0.8.csv`, `Indtest10.8.csv`, `Indtest2.csv`.
     - `0.9`:`train0.9.csv`, `Indtest10.9.csv`, `Indtest2.csv`.
*   **`Codes/`**: It contains the main codes required for the implementation and experiment of the ToxiMSBC model. The functions of the main files are described as follows:
     - `mainmodel.py`: Define the overall framework of the ToxiMSBC model.
     - `predict.py`: Load the trained model `Best model.pt` and perform predictions on two independent test sets based on `ProtT5_0.8Indtest1_features.csv` and `ProtT5_Indtest2_features.csv` respectively.
     - `ROC and PRC curve.py`: Based on the results of training set cross-validation, plot the model's ROC curve and PRC curve.
     - `sequence lengths distribution.py`: Visualize the distribution of sequence lengths in each dataset using a horizontal violin plot.
     - `visualization.py`: t-SNE distribution results is used to demonstrate the evolution of model feature representations as the number of epochs increases.

## 4 Predict

Using `ProtT5_0.8Indtest1_features.csv`, `ProtT5_Indtest2_features.csv`, and `predict.py` allows you to reproduce the prediction results for the independent test sets in the experiment.
Specifically, `predict.py` calls the model structure defined in `mainmodel.py` and loads the trained model parameter file `Best model.pt`.

