# Difference between Loss Function & Cost function:
* Suppose if just one record is passed to the neural network, we get prediction (ŷ) and then error calculation. So this is called as Loss Function for example in SGD where it takes only record at a time.
* Suppose if batch of records is passed to the neural network and performs BPP and FPP, at that time Loss will L(w) = Σ<sup>t</sup><sub>i=1</sub>(y - ŷ)<sup>2</sup> where, t is the batch-size. So, whenever summation of multiple error takes place at that it becomes Cost Function.

# Types of Loss/Cost functions:
## For Regression:
### 1. Squared Error Loss:
> Formula :<br>
> Loss Function: L = (y - ŷ)<sup>2</sup>  
> Cost Function/Mean squared Error: J = (1/t)Σ<sup>t</sup><sub>i=1</sub>(y - ŷ)<sup>2</sup> where, t is the batch-size
* **Advantage:**
  * In the form quadratic equation (ax<sup>2</sup>+bx+c)
    * Plot of Quadratic equation is with only Global Minima.
    * Does not have any Local Minima
    <img src="https://textimgs.s3.amazonaws.com/boundless-algebra/trygx7sythwhphxv8rg3.jpe#fixme"/> 
  * MSE Loss penalizes the model for making large errors by squaring them. 
* **Dis-advantage:**
  * It is not robust to outliers. 

### 2. Absolute Error Loss:
> Formula :<br>
> Loss Function: L = |y - ŷ|  
> Cost Function/Mean absolute Error: J = (1/t)Σ<sup>t</sup><sub>i=1</sub>|y - ŷ| where, t is the batch-size.
* Advantage:
  * Plot of Linear equation is with only Global Minima.
  * MAE is more robust to outliers are compared to MSE because evethough outliers are present, MAE is not penalizing enough
* Dis-advantage:
  * Computation of modulus operator is very very difficult because handling the absolute term or modulus operator is not very easy in mathematics.
  * Because of Linear equation, it may have Local minima.
 
### 3. Huber Loss:
* Combines both MSE (Quadratic Equation) and MAE(Linear Equation).
* Formula: 
   <img src="https://miro.medium.com/max/1508/1*2QDciI--0L5Zqd8UXgXaWg.jpeg"/>
   * 𝛿 is hyperparameter and selected my network based on outliers. 
   * Suppose if there's an outlier, the diifference y - ŷ will atleast be greater than 𝛿 because of an outlier and uses MAE. If it's not an outlier it will simply use MSE.

* Dis-advantage:
  * Huber Loss may have local minima.

## For Classification:
### 4. Cross-Entropy Loss
* Cross-Entropy is used for Binary Classification problem statement.
> Formula:<br>
> Loss = [-y * log(ŷ)] - [(1-y) * log(1-ŷ)] <br>
> where, ŷ is computed using Sigmoid AF => 1/(1 + e<sup>-z</sup>) ; y is actual value

### 5. Multiclass Cross-Entropy Loss
* Used for multiclass classification problem.
  > Formula: <br>
  > Loss(x<sub>i</sub>, y<sub>i</sub>) = - Σ<sup>c</sup><sub>j=1</sub> (y<sub>ij</sub> * log(ŷ<sub>ij</sub>))<br>
  > where; <br>y<sub>i</sub> is one hot encoded value represented in the form of BITS, <br>y<sub>ij</sub>=1 if the i<sup>th</sup> element is in class j and 0 otherwise.<br>
  > ŷ<sub>ij</sub> is calculated using Softmax AF which returns the probability of each of the class.

Sparse categorical cross entropy returns the index of highest probablity value. 


















### Global minima vs Local Minima:
* During back propagation, there is always some kind Loss function (e.g. Mean Squared Error -> L(w) = Σ<sup>k</sup><sub>i=1</sub>(y - ŷ)<sup>2</sup>). Optimizer will reduce the value of Loss.
* In deep learning there are other Loss function which does not create Convex Function(U-shaped gradient descent) curve, mostly it creates different shape (Non-convex function curve) and there is where Local minima comes into existence.
* In convex-function, there's always one global minima. 
<img src="http://citadel.sjfc.edu/faculty/kgreen/MSTI130/MSTI130Text/Text_Fall_2014265x.png"/>
