This jupiter notebook shows a simple Neural network built from scratch with just numpy operations.
Each Neuron operates on an input vector X. The shape of X determines how many weights are in the W vector it stores internally. There is a scalar value b for bias.
The Neuron is initialized with the size of input it should expect, an activation function and a derivative of the activation function.
The weights and bias are chosen randomly when the neuron is initialized.

During forward propagation, the neuron does a linear transformation of the weights with the inputs it is given, adds an element of non-linearity by converting that to the output of an activation function chosen for this purpose.
It also stores the gradient of the activation (to be used during backward prop).

During training, when the final layer produces the output, the loss is calculated.

The loss is propagated backwards layer by layer starting from the output layer. 

Each neuron calculates the derivative of the loss with respect to its 
*  current weights vector W
*  current bias - b
*  current inputs vector X -> this is propagated backward as the derivative of loss with respect to the output of the previous layer.

Once the loss to be propagated to the previous layer is calculated,  the current weights and bias are updated.

Parallelization is hinted at two steps. 
* During forward prop, all neurons in a single layer receive the same input and produce their activated output.
* During backward prop, all neurons in a single layer update the loss for the previous layer. 
However these steps can only happen in sequence layer by layer.

Once the desired loss is arrived at, we stop the training and try to do inference with the Predict function.
