# Repeller_Method

This code uses standard NN to categorize the MNIST data set. After a first model is found a second is found performing nearly identicall fitting with the exception that a repeller term is added to the loss function. When the weights of the new model are close (in the Frobeneus norm sense) to the old model, there is a steep penalty. Basically this penalty looks like f(new)=1/(new-old)^2, which is differentiable everywhere it's needed (we want weights far apart and gradient descent will seek it).

Experiments show that the new model will find a truly distinct solution with similar accuracy, and hundreds of isntances where the first and second model disagree. This process can obviously be iterated.

The Repeller Method should allow one to make an infininte ensemble. The next phase of this research project would be to combine predictions with a moving average (EMA is probably right). The weights that each new models repells from is less clear. The naive idea would be to use a standard or moving average as well, to avoid the time complexity of trying to repell away from several weight matrices. Other ideas for weighting could be by accuracy on the training data. First over fit, then regularize.
