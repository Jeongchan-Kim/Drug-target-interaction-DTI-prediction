# Drug target interaction(DTI) prediction using Sequence model

Implementation of a Convolutional Neural Network (CNN) model for predicting Drug-Target Interactions (DTIs) using sequence data. Specifically, the model takes as input two sequences: the protein sequence and the drug sequence. The protein sequence represents the amino acid sequence of a protein, while the drug sequence represents the chemical structure of a drug molecule.

The CNN architecture used in this code consists of several convolutional layers with max-pooling and dropout layers in between them. The convolutional layers are used to extract relevant features from the input sequences. Max-pooling is used to reduce the dimensionality of the output feature maps, while dropout is used to prevent overfitting during training.

The final layer of the model is a sigmoid layer, which outputs a probability score between 0 and 1, representing the likelihood of a drug and a protein interacting. During training, the model learns to adjust its weights in order to minimize the binary cross-entropy loss between the predicted and actual labels of the training data.

In the testing phase, the model is evaluated on a separate set of test data using various metrics such as area under the receiver operating characteristic curve (AUROC), area under the precision-recall curve (AUPRC), F1 score, and cross-entropy loss.

Finally, the code includes functions for visualizing the performance of the model using ROC and precision-recall curves. These curves are commonly used to visualize the trade-off between true positive rate and false positive rate, and between precision and recall, respectively, for different classification threshold values.


## Dataset

[DAVIS](https://www.nature.com/articles/nbt.1990)
## Data Preprocessing

**Load data**: First, the codes load the data in a CSV file format, which contains the sequences of amino acids for each protein and the SMILES notation for each drug molecule.

**Encode sequences and SMILES notation**: Then, the protein sequences and SMILES notations are encoded into numerical representations using one-hot encoding. This means that each amino acid or character in the SMILES notation is represented by a binary vector of the same length, with a value of 1 in the position corresponding to that amino acid or character, and 0s everywhere else.

**Split data into training and test sets**: The data is then split into training and test sets with a ratio of 8:2.

**Create PyTorch Dataset and DataLoader**: The training and test data are transformed into PyTorch Dataset objects, which allow for easy handling and loading of the data. These Datasets are then used to create PyTorch DataLoader objects, which are iterable over the data.

**Define labels**: The labels, which indicate whether a drug targets a protein or not, are extracted from the CSV file and transformed into numerical binary values (0 or 1).

**Balancing data**: The training data is balanced to ensure that there is an equal representation of positive and negative samples.

**Normalize data**: The data is normalized to have zero mean and unit variance to make the training process more stable.
## About Model

### Feature Extractor

The feature extractor used in this code is a convolutional neural network (CNN) that takes in as input the drug and protein sequences. The drug sequence is represented by a one-hot encoding of the SMILES strings, while the protein sequence is represented by a one-hot encoding of the amino acid sequence. The CNN then applies a series of convolutional layers and pooling layers to the input sequences to extract features from them. The final output of the CNN is a feature vector that represents the input sequences.

### Model

The model used in this code is a multi-layer perceptron (MLP) that takes as input the concatenated drug and protein feature vectors produced by the CNN. The MLP consists of several fully connected layers, each followed by a ReLU activation function. The output layer of the MLP uses a sigmoid activation function to produce a binary classification output, indicating whether or not the drug and protein interact. During training, the model is optimized using binary cross-entropy loss. During testing, the model's performance is evaluated using several metrics, including area under the ROC curve (AUROC), area under the precision-recall curve (AUPRC), F1 score, and cross-entropy loss.
## Result

Validation at Epoch 15, AUROC: 0.89008 , AUPRC: 0.59927 , F1: 0.45315 , Cross-entropy Loss: 3.00963
