How the Model Learns Weights
in actual neural networks, the model learns the features automatically, and they are not predefined by humans in that way.
The core mechanism behind weight learning is called "backpropagation," which works in conjunction with an optimization algorithm like "gradient descent." Here's a simplified explanation:

Initialization:

The process begins with the weights being initialized to small, random values. This is essential to break symmetry and allow the network to learn diverse patterns.
Forward Pass:

Training data (sentences with their correct sentiment labels) is fed into the network.
The signals propagate through the network, from the input layer to the hidden layer, and finally to the output layer, producing a prediction.
Loss Calculation:

The network's prediction is compared to the actual, correct label.
A "loss function" calculates the error between the prediction and the true label. This error represents how "wrong" the network's prediction was.
Backpropagation:

This is the key learning step. The error calculated in the previous step is propagated backward through the network, layer by layer.
During backpropagation, the network calculates the "gradient" of the loss function with respect to each weight. The gradient indicates the direction and magnitude of the change needed to minimize the error.
Weight Update (Gradient Descent):

The optimization algorithm (e.g., gradient descent) uses the calculated gradients to update the weights.
The weights are adjusted in the direction that reduces the loss. The "learning rate" is a crucial parameter that controls the size of these adjustments.
Essentially, the network tweaks the weights to make its predictions more accurate.
Iteration:

Steps 2-5 are repeated many times, iterating through the training data.
With each iteration, the network gradually refines its weights, becoming better at making accurate predictions.
In essence:

The model learns by trial and error, adjusting its internal parameters (weights) to minimize the difference between its predictions and the correct answers.
Backpropagation and gradient descent are the mathematical tools that enable this learning process.
