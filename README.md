Please acknowledge the use of these scripts in any publications which make use of them.

Personal question is as follows:
    
- For small-scale datasets (less than 10,000 samples), is it really necessary to pursue the “context-level dependencies” that LSTMs and Transformers are good at?

So I compared with various ML models for 1D Lorenz data (for the detail, see summary_of_compare_LSTM_GRU_Reservoir.pdf).

Parameters are fixed for fair accuracy comparison:

- Number of trainable parameters: 20,000 
(nodes: Reservoir $\sim 150$, LSTM $\sim 70$, GRU $\sim 80$)

- Training data size: 5,000

- Prediction horizon: 100 steps ahead

- $L^2$ regularization parameter: 0.0001

In this setting, a low-spec machine on Google Colab (free version) is sufficient!

Learning models for accuracy comparison:

- Standard LSTM implemented with TensorFlow (Adam optimizer for gradient descent)

- LSTM with a novel gradient descent method without backpropagation

- GRU with a novel gradient descent method without backpropagation

- Fast-lightweight LSTM

- Reservoir computing (online) with double-loop training via Bayesian Optimization



Conclusions:

- For time series prediction with around 5,000 data points, designing an architecture based on the data characteristics achieves better learning performance than using standard libraries directly.


- Even a simple architecture, such as the fast-lightweight LSTM, can achieve excellent learning results.


- The reservoir with double-loop online learning can achieve strong performance even with only 1,500 + 150 data points (see also Nakai-Saiki 2024).
