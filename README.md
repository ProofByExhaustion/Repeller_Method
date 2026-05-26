# Repeller_Method

This code uses standard NN to categorize the MNIST data set. The purpose of this experiment is to create distinct "learning perspectives" by altering the geometry of the loss surface. After a first model is found, a second is found performing nearly identical fitting with the exception that a repeller term is added to the loss function. When the weights of the new model are close (in the Frobenius norm sense) to the old model, there is a steep penalty. Basically this penalty term looks like f(new)=1/(new-old)^2, which is differentiable everywhere it's needed (we want weights far apart and gradient descent will seek it).

Experiments show that the new model will find a truly distinct solution with similar accuracy, and hundreds of instances where the first and second model disagree. This process can obviously be iterated.

The Repeller Method should allow one to make an infinite ensemble. The next phase of this research project would be to combine predictions with an online average or online pairwise max to keep the prediction from the model that is most certain. The weights that each new model repels from is less clear. The naive idea would be to use an online standard or moving average as well, to avoid the time complexity of trying to repel away from several weight matrices. Other ideas for weighting could be by accuracy on the training data. (First over fit, then regularize.)

Deeper, but more expensive, computations would involve cosine similarity with Frobenius inner product and centered kernel alignment as a means to measure "nearness" of model weights.
