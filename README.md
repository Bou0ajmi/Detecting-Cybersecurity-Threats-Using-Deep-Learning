# Detecting-Cybersecurity-Threats-Using-Deep-Learning
A binary classification deep learning model that detects suspicious system events from real-world-style logs using the BETH dataset.
# Cyber Threat Detection with Deep Learning

A binary classification model built with PyTorch to detect suspicious events in system logs using the BETH dataset.

## Overview

This project trains a neural network to classify system log events as either suspicious (1) or benign (0). The model achieves ~99.6% accuracy on the validation set.

## Dataset

The BETH dataset contains simulated real-world system logs with the following features:

- `processId` — unique identifier of the process that generated the event
- `threadId` — ID of the thread spawning the log
- `parentProcessId` — ID of the parent process
- `userId` — ID of the user spawning the log
- `mountNamespace` — mounting restrictions for the process
- `argsNum` — number of arguments passed to the event
- `returnValue` — value returned from the event log

Target: `sus_label` (1 = suspicious, 0 = benign)

## Model Architecture

A fully connected neural network with the following layers:

```
Input (7) → Linear(128) → ReLU → Linear(64) → ReLU → Linear(1) → Sigmoid
```

- Loss: Binary Cross-Entropy
- Optimizer: SGD (lr=1e-3, weight_decay=1e-4)
- Epochs: 10

## Results

| Dataset    | Accuracy |
|------------|----------|
| Train      | 99.83%   |
| Test       | 9.27%    |
| Validation | 99.58%   |

> Note: The low test accuracy reflects severe class imbalance in the test set (90.7% suspicious events vs. 0.17% in training).

## Requirements

```
pandas
scikit-learn
torch
torchmetrics
```


1. Place `labelled_train.csv`, `labelled_test.csv`, and `labelled_validation.csv` in the project directory.
2. Run the notebook `notebook.ipynb` top to bottom.
