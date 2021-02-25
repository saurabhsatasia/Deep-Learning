# Commonly used Activation Function:
### 1. Sigmoid Function:
* When sigmoid activation function is applied, the output value will be ranging between 0 ans 1.
* During Back Propagation, whenever the weights are getting updated, activation function contributes in terms of calculation because we are trying to take the differential of activation function and loss function to compute new value of weights.
* Differentiation of Sigmoid function ranges from 0 to 0.25.
* Dis-advantages:
  * Sigmoid function is prone to Vanishing Gradinet Problem.
  * Function output is not zero-centered so, the gradient will always have a positive value.
  * If the function output or data is not zero centered, more computation time will be required and takes more time to reach global minima.


### Some Terminologies to note:

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
