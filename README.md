This jupiter notebook shows a simple Neural network built from scratch with just numpy operations.
Each Neuron operates on an input vector X. The shape of X determines how many weights are in the W vector it stores internally. There is a scalar value b for bias.
The Neuron is initialized with the size of input it should expect, an activation function and a derivative of the activation function.
The weights and bias are chosen randomly when the neuron is initialized.

During forward propagation, the neuron does a linear transformation of the weights with the inputs it is given, adds an element of non-linearity by converting that to the output of an activation function chosen for this purpose.
It also stores the gradient of the activation (to be used during backward prop).

When the final layer produces the output, the loss is calculated.

The loss is propagated layer by layer. 

Each neuron calculates the derivative of the loss with respect to its 
*  current weights vector W
*  current bias - b
*  current inputs vector X -> this is propagated backward as the derivative of loss with respect to the output of the previous layer.

Once the loss is propagated to all the neurons up to the first layer, the weights and bias are updated to minimize the loss.

Parallelization is hinted at two steps. During backward prop, all neurons in a single layer update the loss for the previous layer in parallel. 
However this can only happen in sequence layer by layer starting from the output layer to the first layer.

Once all the neurons have calculated the derivative of loss with respect to their weights and biases, all of them update their weights in parallel.
Once the desired loss is arrived at, we stop the training and try to do inference with the Predict function.
