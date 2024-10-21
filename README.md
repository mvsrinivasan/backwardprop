This jupiter notebook shows a simple Neural network built from scratch with just numpy operations.
Each Neuron operates on an input vector X. The shape of X determines how many weights are in the W vector it stores internally. There is a scalar value b for bias.
The Neuron is initialized with the size of input it should expect, an activation function and a derivative of the activation function.
The weights and bias are chosen randomly when the neuron is initialized.

During forward propagation, the neuron does a linear transformation of the weights with the inputs it is given, feeds this to an activation function to learn non-linear relationships.
It also stores the gradient of the activation (to be used during backward prop).

During training, once the final layer produces the output, the loss is calculated. The loss is then propagated backwards layer by layer starting from the output layer, where at each layer
the loss is recalculated and the weights are bias are updated.

Each neuron calculates the derivative of the loss with respect to its 
*  current weights vector W
*  current bias - b
*  current inputs vector X -> this is propagated backward as the derivative of loss with respect to the output of the previous layer.

Once the loss to be propagated to the previous layer is calculated,  the current weights and bias are updated.

Parallelization is hinted at two steps. 
* During forward prop, all neurons in a single layer receive the same input and produce their activation output in parallel.
* During backward prop the following two steps happen in sequence.
  * all neurons in a single layer update the loss from the subsequent layer in parallel.
  * they propagate their loss to the neurons of the previous layer in parallel. 

However both forward and backward prop can only be done in sequence layer by layer.

Once the desired loss is arrived at, we stop the training and try to do inference with the Predict function.
