### Links
* https://towardsdatascience.com/hyper-parameter-tuning-techniques-in-deep-learning-4dad592c63c8
* https://github.com/sandhyaparna/Data-Science/blob/e617d0d1a54293cd157d0ae65477c6a6329625e4/Deep%20Learning/Neural%20Networks.md



### Learning Rate
* Step size = (Gradient or slope) * (learning rate)
* If learning rate is small, loss keeps decreasing and finally converges, but if learning rate is high, loss oscillates/diverges. But lower learning rate takes more time. Large learning rates help to regularize the training but if the learning rate is too large, the training will diverge. 
![](https://github.com/sandhyaparna/Data-Science/blob/master/Deep%20Learning/Images/learning%20rate.png)

Run Code: code with example in https://github.com/sandhyaparna/Data-Science/blob/master/Deep%20Learning/Images/Implementing_LR_range_test_Learning_rate_finder.ipynb
* Run the function here: https://github.com/surmenok/keras_lr_finder/blob/master/keras_lr_finder/lr_finder.py
* Then run code in README of https://github.com/surmenok/keras_lr_finder

### Optimzation Algos
* Gradient Descent with Momentum: With each iteration of gradient descent, we move towards the local optima with up and down oscillations. If we use larger learning rate then the vertical oscillation will have higher magnitude. So, this vertical oscillation slows down our gradient descent and prevents us from using a much larger learning rate. Additionally, too small a learning rate makes the gradient descent slower.**We want a slower learning in the vertical direction and a faster learning in the horizontal direction which will help us to reach the global minima much faster**


### Weight Decay
* Weight decay is one form of regularization and it plays an important role in training so its value needs to be set properly [7]. Weight decay is defined as multiplying each weight in the gradient descent at each epoch by a factor λ [0<λ<1].
* Smaller datasets and architectures seem to require larger values for weight decay while larger datasets and deeper architectures seem to require smaller values. Our hypothesis is that complex data provides its own regularization and other regularization should be reduced.
* The optimal weight decay is different if you search with a constant learning rate versus using a learning rate range. This aligns with our intuition because the larger learning rates provide regularization so a smaller weight decay value is optimal.

### Batch size
* larger batch sizes make larger gradient steps than smaller batch sizes
* Large batch sizes may result in different outputs during run and may fall into local mimima
* Use smaller batch size for consistent results
* Small batch sizes add regularization while large batch sizes add less, so utilize this while balancing the proper amount of regularization






