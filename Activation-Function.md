# Commonly used Activation Function:
### 1. Sigmoid Function:
> #### `Sigmoid function = 1 / 1 + exp(-x)`
* When sigmoid activation function is applied, the output value will be ranging between 0 ans 1.
* During Back Propagation, whenever the weights are getting updated, activation function contributes in terms of calculation because we are trying to take the differential of activation function and loss function to compute new value of weights.
* Differentiation of Sigmoid function ranges from 0 to 0.25.
* Dis-advantages:
  * Sigmoid function is prone to Vanishing Gradinet Problem.
  * Function output is not zero-centered so, the gradient will always have a positive value.
  * If the function output or data is not zero centered, more computation time will be required and takes more time to reach global minima.

### 2. tanh function:
> #### `tanh function = 2 (sigmoid function - 1) => (exp(x) - exp(-x)) / (exp(x) + exp(-x))`

* The output of tanh function will be ranging between -1 to +1.
* the output of derivative of tanh function ranges between 0 to 1.
* tanh function is zero-centric, which is better than sigmoid function.
* Dis-advantage : tanh function is also prone to Vanishing Gradient problem & computationally expensive.
* In general binary classification problem, the tanh function is used for the hidden layers and the sigmoid function is used for the output layer.

### 3. ReLU(Rectified Linear Unit) function:
> #### `ReLU = max(0, x)`
* Whenever the `x` value is greater than `0`, then the output is basically that particular `x`.
* Derivative of ReLU is either `0` or `1`
* Derivate of ReLU function will be `1` if value of `x > 0`. (derivative of `x` w.r.t `x` is 1). If the value of `x ≤ 0`, derivative of function will be `0`. NOT between 0 to 1. 
* Mostly used in hidden layers as it solves the Vanishing Gradient Problem.
* **Dis-advantage:** During back-propagation, suppose one of the value of gradient/derivative is `0` in chain rule, at that time new weight will be equal to existing/old weight when using weight updation formula `W_new = W_old - (LR * gradient)`. So, here weight updation will not happen. This scenario is called Dying ReLU or Dead Activation Function.
* To solve the problem of dead ReLU, Leaky ReLU is used.

### 4. Leaky ReLU function:
> #### `Leaky ReLU = max(0.01x, x)`
* Small constant is multiplied to `x`. Derivative of Leaky ReLU function w.r.t. `x` is 1 and derivative w.r.t. `0.01x` will be `0.01`. This solves dying ReLU problem.
* In some of the scenarios, Leaky ReLU brings up the Vanishing Gradient Problem. Because if suppose  most of the weights are negative at that time w.r.t. derivative, weights are multiplied with `0.01`, because of this value of gradient will be smaller, so during weight updation, new weight will approximately be equal to old/existing weight. 

### 5. ELU (Exponential Linear Units) function:
* ELU tries to handle -ve values in efficient way.
> #### `ELU = x ; if x>0`
> #### `ELU = α(exp(x) - 1); otherwise`<br>
α is hyperparameter
* ELU solves one major problem, don't have find derivative of zero.
* ELU solves dead ReLU problem.
* The mean of the output is close to 0, so it is zeo-centered.
* Dis-advantage: ELU is computationally expensive because of exponential term.

### 6. PReLU (Parametric ReLU) function:
* All the functionalities are same as ReLU and Leaky ReLU.
> #### `PReLU = x ; if x > 0`
> #### `PReLU = α * x; if x ≤ 0` 
* `α` can considered as learning parameter which will dynamically change based on this activation function.
* PReLU solves dead ReLU problem and Leaky ReLU problem.

### 7. Swish (A self-gated) function:
> #### `Swish Activation Formula: Y = X * sigmoid(X)`
> `where X = (weight * input) + bias`
* Swish AF is mostly used for gating in LSTMs and highway network.
* Swish AF can used when Neural Network has greater than 40 layers.
* Swish AF is zero-centric and also solves dead ReLU problem because derivative will always be greater than zero.

### 8. Softplus function:
> #### `Softplus AF Formula: f(x) = ln(1 + exp(x))`
* Derivative of `0` is not possible in the real world scenario, but in some case whenever we have to take derivative of zero, we try to use Softplus AF.
* Softplus AF solves the major problem, don't have find derivative of zero.

### 9. Softmax function:
* Softmax AF is used for multiclass classification problem statement, in the output layer with more than 2 neurons.
* Calculates the probablity of each of the input classes.
* Softmax is differentfrom the normal max function: the max function only outputs the largest value, and Softmax ensures that smaller values have a smaller probability and will not be discarded directly.

 
## these activation functions have theirown advantages and disadvantages. There is no statement that indicates which ones are not working, andwhich activation functions are good. All the good and badmust be obtained by experiments.


#### Some Terminologies to note:

#### Gradient Descent:
* Loss is computed by comparing y_actual and y_prediction (eg. (y-y_hat)^2) from output of neural network. In order to reduce loss, Optimizers are used and Gradient Descent is one of the optimizer.
* In short, Gradient is descent will try to find out the weights that has to be updated in a very effiecient way. The best weights to calculate y_pred.
* Updation of weights happens with the help of Back Propagation. `new_weight = existing_weight — learning_rate * gradient`. Gradient is derivative of Loss w.r.t exisiting weight, basically a slope computed on gradient descent curve(Weight vs Loss).
* Gradient/Slope depends on learning rate. If learning rate is very small, takes more time to reach global minima point in gradient descent curve where the loss is minimum. In case of very high value of learning rate, weight will jump inside the gradient descent curve and never reaches global minima point.

#### Vanishing Gradient Problem:
* During Back propagation, existing weights gets updated. Gradients are calculated using Chain Rule.
* As the number of layers in NN increases, the value of Gradient/derivative will be decreasing and becomes very small number. As a result, new weights will be approximately equal to existing/old weight.
This scenario is called as Vanishing Gradient problem.
* Vanishing Gradient problem occurs usually when using `sigmoid` and `tanh` activation function.

#### Exploding Gradient Problem:
* Exploding gradient problem occurs mainly because of higher values of initialized weights. 
* During Back Propagation, because of high value of initialized weights, the calculated value of gradient will also be very high andthe new calculated weights will vary a lot when compared to existing weights. As a result, the gradient descent value will never converge to global minima, instead it will be jumping left and right in the gradient descent curve.
* That's why it is important to use weight initialization techniques.
