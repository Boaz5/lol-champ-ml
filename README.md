# League of Legends Champion Prediction Model

The goal of this project is to develop a custom neural network model to predict champion picks in professional League of Legends matches. The goal is to recommend the most probable champion pick given existing team compositions, the specific role, and historical performance data.

The dataset used in this model can be retrieved here https://oracleselixir.com/tools/downloads/

## Overview

The project uses match data from OraclesElixir to train a champion prediction model. It focuses on several key aspects:

1.  **Data Collection & Preprocessing:**
    *   Loading match data from multiple years.
    *   Filtering for complete games and standardizing champion roles (e.g., 'jng' to 'jungle', 'bot' to 'adc').
    *   Ensuring each match contains exactly 10 players.

2.  **Feature Engineering:**
    *   Calculating historical winrates for each champion.
    *   Calculating historical winrates for each champion-role combination. These features are calculated based on past patches, avoiding data leakage.

3.  **Model Architecture:**
    *   A custom neural network built using NumPy.
    *   Utilizes champion embeddings to represent champions.
    *   Incorporates one-hot encoded role features, side (blue/red), and the engineered historical winrate features.
    *   Implementing a simple forward and backward pass with 2 hidden layers and a output layer

4.  **Training & Evaluation:**
    *   Data is split into training, validation, and test sets based on unique `gameid` to maintain integrity.
    *   The model is trained to predict the `target_champion` given the rest of the draft and player specific features.
    *   Evaluated using metrics such as Top-1, Top-3, Top-5 accuracy, and Macro F1 score.

5.  **Model Persistence & Inference:**
    *   The trained model parameters are saved and can be loaded for future use.
    *   A demonstration function `make_single_prediction_and_evaluate` showcases how to use the loaded model to predict a champion pick for a single sample, displaying the proposed champion along with ally and enemy team compositions.

## Results

My current deep learning model significantly improved since the baseline model, showcasing its effectiveness in predicting champion picks within League of Legend drafting.
