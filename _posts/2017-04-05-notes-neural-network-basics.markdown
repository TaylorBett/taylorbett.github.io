---
layout: post
title:  "Notes: Neural Network Basics"
date:   2017-04-05 10:03:00 +1000
categories: notes
tags: [ml, neural network, machine learning]
---

Notes on [Crash Course On Multi-Layer Perceptron Neural Networks - Machine Learning Mastery](http://machinelearningmastery.com/neural-networks-crash-course/)

* Universal approximation algorithm
* Built out of artificial neurons or sometimes ‘perceptrons’
### Inputs  > Weights > Activation > Output

### Weights
* Bias
* Often initialised as random small values, ie. 0-0.3
* Larger weights indicate increased complexity and fragility
* Desirable to keep them small

### Activation
* Weighted inputs summed and put through activation function
* AKA Transfer function
* Maps summed weighted input to output of neuron
* Historically used with threshold, ie. summed input > 0.5 then activate (binary output, 1.0 or 0.0)
* **Sigmoid** function outputs value between 0.0 and 1.0 with S shaped distribution
* **Tanh** function outputs S shaped dist. over -1 to 1

## Networks
### Input or Visible Layer
* Often drawn one neuron per input datapoint. These just pass the value into the next layer, and *do not* have a transformative activation function

### Hidden Layers
* (Not directly exposed to input)
* **Deep** learning can refer to a large number of hidden layers in the neural net being used

### Output Layer
* May have an activation function and output float values or a binary outcome
* May have multiple neurons producing values that are then used for  Multiple-Class Classification (ie. Iris problem)

## Training Networks
### Data Preparation
* Data must be numerical. Categorical data can be transformed into numerical data for this purpose
* Data must be scaled in a consistent way. Often normalised between 0 and 1, or standardised to have a mean of 0 and standard deviation of 1.

### Stochastic Gradient Descent
* Classical and still  preferred training methodd
* One row exposed to the NN at a time which processes it upwards/forwards (a forward pass).
* Output of NN is compared to expected output, and error is calculated.
* Error propagated back through the NN one layer at  a time and weights are updated according to how much they contributed to the error.
* This is called [Backpropagation - Wikipedia](https://en.wikipedia.org/wiki/Backpropagation)
* This is repeated for all rows of training data. One session of training is called an ‘Epoch’, and there may be many of these, up to thousands.

### Weight Updates
* Backpropagation on every example is called ‘online learning’. This can result in very fast but also chaotic changes to the network.
* Alternatively, errors can be saved up till the end of the Epoch and the NN can be updated at the end. This is called ‘Batch’ training and is often more stable
* Might break up datasets into 10s or 100s for this purpose, for an intermediate solution
* Amount by which weights are updated is controlled by config parameters called the ‘learning rate’ AKA ‘step size’. Often very small weight sizes are used such as 0.1 or 0.01 or smaller.
* ‘Momentum’ can be used to update weights in the same direction even when there is less error detected (getting closer).
* Learning rate can be decayed over epochs to make larger changes at first and fine tune later, as part of a training schedule.

### Predictions
* Forward pass through the NN
* All you need is the NN topology and final set of weights from NN
* Output is used as prediction
