Introduction

Federated Learning is a distributed machine learning paradigm in which multiple clients collaboratively train a shared global model without sharing their raw data. Instead of sending data to a central server, clients perform local training and only share model parameters or updates. This approach preserves data privacy, reduces communication costs, and is suitable for decentralized and sensitive data scenarios.

However, in real-world federated systems, client data is often heterogeneous and non-IID. A single global model may perform poorly for individual clients due to differences in data distributions. Personalized Federated Learning addresses this limitation by allowing each client to maintain a locally personalized model while still benefiting from shared global knowledge.

This project implements a Personalized Federated Learning framework that trains a global parent model along with personalized client models across multiple communication phases, while preserving data privacy.

Project Description

This repository contains an implementation of Personalized Federated Learning for image classification using deep learning. The system supports training across decentralized clients with heterogeneous data distributions and evaluates both global and client-specific performance in a phase-wise manner.

The project includes:

Federated training logic

Client-specific personalization

Non-IID data partitioning

Detailed logging of training and evaluation

Phase-wise result analysis and visualization

Project Type

Group Project

This work was developed collaboratively as part of an academic project.
I served as the primary and major contributor, responsible for the core system design, implementation, experimentation, and result analysis.

My Contributions

I was responsible for the complete technical implementation of the project, including:

Designing the Personalized Federated Learning workflow

Implementing non-IID data partitioning with client-prevalent and shared classes

Developing phase-wise federated training across multiple rounds

Implementing client-side personalization through local fine-tuning

Designing and implementing the hierarchical convolutional neural network

Implementing aggregation logic between global and client models

Logging detailed phase-wise performance metrics

Saving experimental results in CSV format

Conducting experiments on multiple datasets

Generating performance plots and runtime statistics

Methodology

The training process follows a multi-phase federated learning pipeline.

Initial Global Training
A global parent model is trained on a centrally available parent dataset.

Phase-wise Federated Training
Training is conducted over multiple phases. In each phase:

The parent model weights are shared with all clients

Each client performs local training on its own data

Updated client models are aggregated with the parent model

Client models are personalized using combined global and local knowledge

Personalization
Each client maintains its own personalized model by partially updating parameters after aggregation. This improves client-level performance under heterogeneous data distributions.

Data Distribution Strategy

To simulate realistic federated environments, data is split as follows:

Parent dataset for global training

Client 1 dataset with prevalent classes

Client 2 dataset with different prevalent classes

A set of common shared classes across clients

This creates a non-IID data scenario where each client has a unique data distribution.

Model Architecture

The system uses a hierarchical convolutional neural network consisting of:

Multiple convolutional paths with different kernel sizes

Adaptive pooling layers

Fully connected layers

Dropout for regularization

This architecture enables robust feature extraction from image data.

Evaluation Metrics

For every phase, the following metrics are computed:

Accuracy

Precision

Recall

F1-score

Metrics are evaluated for:

Global parent model

Client-specific personalized models

Training and validation or test datasets

All results are logged to text files and stored in CSV format for analysis.

Repository Structure

.
├── PFL_2_main_dataset1_5e_10r
│ ├── PFL_main_dataset1_5.py
│ ├── pfl_dataset1_main_detailed_log.txt
│ └── pfl_dataset1_main_detailed_results.csv
│
├── PFL_main_dataset2_5e_10r
│ ├── PFL_2_5.py
│ ├── final_detailed_5_log.txt
│ └── final_detailed_5_results.csv
│
├── README.md

Experimental Setup

Epochs per phase: 5
Number of phases: 10
Batch size: 16
Optimizer: Adam
Learning rate: 0.001
Weight decay: 0.0001
Data augmentation: resizing, random horizontal flipping, random rotation

Results

The experimental results demonstrate:

Stable convergence of the global model across phases

Improved client-level performance through personalization

Clear performance differences between global and personalized models in non-IID settings

Detailed numerical results and training logs are provided in the repository.
