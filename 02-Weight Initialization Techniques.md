# Common techniques for weight initialization:

### Key points:
1. Initialized weights should not be very very small, shouls also not be very very large. Small weights causes Vanishing problems. High value of weights causes Exploding gradient problem.
2. Initialized weights should NOT be equal/same. 
3. Initialized weights shouls have good variance.
4. Weights must initialized in a proper way to avoid vanishing gradient problem and exploding gradient problem.

### 1. Uniform Distribution:
* Weights sample from the Uniform Distribution 
> #### `W<sub>ij</sub> ~ Uniform [-(1/sqrt(fan_in)), 1/sqrt(fan_in)]`
> #### where `fan_in` is the no. of inputs
* Weights will initialized between lower bound`(i.e. -(1/sqrt(fan_in)))` and upper bound`(i.e. 1/sqrt(fan_in))`
* Works well with Sigmoid Activation Function.

### 2. Xavier/Gorat Distribution:
* Consist of 2 techniques:
  1. Xavier/Gorat Normal:
    * Initialize weights sampled from normal distribution with mean=0 and std=σ
    > #### `W<sub>ij</sub> ~ Normal [0, σ]`
    > #### `where σ = sqrt(2 / (fan_in + fan_out))` 
  2. Xavier/Gorat Uniform:
    > #### `W<sub>ij</sub> ~ Uniform [(-sqrt(6) / sqrt(fan_in+fan_out)), (+sqrt(6) / sqrt(fan_in+fan_out))]`
    * Works well with Sigmoid Activation function.
    
### 3. He init:
* Consist of 2 technique:
  1. He Normal:
    > #### `W<sub>ij</sub> ~ Normal [0, σ]`
    > #### `where σ = sqrt(2 / fan_in)` 
  3. He Uniform:
    > #### `W<sub>ij</sub> ~ Uniform [-(sqrt(6 / fan_in)), +(sqrt(6 / fan_in))]`
 * Works very well ReLU activation function.



    
