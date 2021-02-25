# Types of Optimizers:

### 1. Gradient Descent:
* Loss/Cost is calculates during the first forward propagration. Main aim is to reduce the Loss function with the help of Optimizers.
* Optimizers update the weights during back propagation.
* Weight updation formula:
  > ### `new_weight = existing_weight — learning_rate * gradient`
* Takes all the records (rows) as an input at every epoch. If the dataset is huge, it requires more RAM. So, this process is computationally expensive and will take more time to reach the point of convergence i.e. global minima.
* To prevent this , SGD-Stochastic Gradient Descent was introduced.

### 2. Stochastic Gradient Descent:
* Suppose we have 10K records in the dataset.
* In SGD, it takes only 1 record at a time does the bach propagation, which means each epoch will have 10K iterations and if the number of epochs are 20 then it will have 20 * 10K iterations. This will again take more time to reach the global minima and the convergence will happen very very slow.
* SGD is less computationally expensive as compared to Gradient Descent.
* To prevent this problem, minibatch SGD was introduced.

### 3. Minibatch Stochastic Gradient Descent (Minibatch SGD):
* Suppose we have 10K records, Minibatch Gradient Descent takes specified batch of records at each  epoch. E.g. 1000 records at each epoch and does the back propagation. If the number of epochs are 20, then each epoch will have 10 iterations (10000/1000=10). So, in each epoch, foward and backward propagation happens 10 times.
* In minibatch SGD, as it takes a certain batch of data, there will be noise involved while reching to the minima point. So, the convergence is not smooth when compared with GD and SGD.
* To reduce this noise, SGD with momentum was introduced.

### 4. Stochastic Gradient Descent with momentum:
* SGD with momentum helps in smoothening the noisy data. Here instead of computing derivative of Loss w.r.t weight, Exponential weighted average (V<sub>dw</sub>) is calculated which helps smoothening the noise.
* Formula:
  * Weight updation formula:
  > W<sub>t</sub> = W<sub>t-1</sub> - learning_rate * exponential_weighted_average<br>
    > where, V<sub>dwt</sub> = V<sub>dw(t-1)</sub> + ((1-β) * ∂L/∂W<sub>(t-1)</sub>)
  * Bias updation formuls:
  > b<sub>t</sub> = b<sub>t-1</sub> - learning_rate * exponential_bias_average<br>
    > where, V<sub>dbt</sub> = V<sub>db(t-1)</sub> + ((1-β) * ∂L/∂b<sub>(t-1)</sub>)
* Initially V<sub>dw</sub> will initialized to zero for both weight and bias.

### 5. Adagrad-Adaptive Gradient Descent:
* Till now in the above optimizers, learning rate was fixed and it was taking same step size to reach minima.
* In Adagrad, learning rate is changed dynamically as the training is going on. This process will be faster, initially it takes bigger step towards the point of convergence
* Formula:
  > W<sub>t</sub> = η'<sub>t</sub> * ∂L/∂W<sub>(t-1)</sub>)<br>
  > where, η' = η / sqrt(α<sub>t</sub> + ε)<br>
  > where, α<sub>t</sub> = Σ<sup>t</sup><sub>i=1</sub>(∂L/∂W<sub>t-1</sub>)<sup>2</sup> <br> η is initial learning_rate <br> ε is very small +ve number because if α<sub>t</sub> becomes zero then it return ZeroDivisionError.
* α<sub>t</sub> considers the squared summation of all the derivatives w.r.t. previous timestamps, which means α<sub>t</sub> will be higher value. In η' formula where we try to divide by higher value of α<sub>t</sub> will result in reducesd value of η'. So, our learning rate will keep on decreasing.
* Dis-advantage: After some point, α<sub>t</sub> will be very very hugh value if it is very deep neural network, then the value of learning rate will be very very small value and so, the new weight will be approx equal to existing weight (i.e. vanishing gradient problem). To solve this problem, RMSProp optimizer is introduced.

### 6. Adadelta:
* Adadelta is an extension of Adagrad and it also tries to reduce Adagrad’s aggressive, monotonically reducing the learning rate.
* Here exponential weighted average is introduced to restrict the high value in the formula of learning rate instead of α<sub>t</sub>.
* Formula:
  > W<sub>t</sub> = η'<sub>t</sub> * ∂L/∂W<sub>(t-1)</sub>)<br>
  > η' = η / sqrt(S<sub>dw</sub> + ε)<br>
  > where, S<sub>dwt</sub> = (β * S<sub>dw(t-1)</sub>) + ((1 - β) * (∂L/∂W<sub>t-1</sub>)<sup>2</sup>) <br> β =0.9 or 0.95 <br> ε is very small +ve number because if α<sub>t</sub> becomes zero then it return ZeroDivisionError. <br>
  > Restricting the increase in the value of (∂L/∂W<sub>t-1</sub>)<sup>2</sup> by multiplying it with (1 - β) a small number.
 
### 6.  RMSProp - Root Mean Square Prop:
* RMSProp is an adaptive learning rate optimization algorithm.
* RMSProp tries to resolve Adagrad’s radically diminishing learning rates by using a moving average of the squared gradient. It utilizes the magnitude of the recent gradient descents to normalize the gradient.
* In RMSProp learning rate gets adjusted automatically and it chooses a different learning rate for each parameter.
* RMSProp divides the learning rate by the average of the exponential decay of squared gradients.

### 7. Adam - Adaptive Moment Estimation:
* Adam optimizer is the combination of Momentum and RMSProp.
* Adam is another method that computes adaptive learning rates for each parameter, in addition to storing an exponentially decaying average of past squared gradients like Adadelta and RMSprop.
* With the help of momentum, gets the smoothening.
* With the help of RMSProp, able to change the learning rate in an efficient manner succt alpha t value will not go high.

## Overall, Adam is the best choice.

