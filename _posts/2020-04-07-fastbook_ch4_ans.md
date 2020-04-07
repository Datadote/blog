1. How is a greyscale image represented on a computer? How about a color image?
> For greyscale, 1 number indicating range from white to black
> For color, 3 numbers indicating intensity of red, green, blue

2. How are the files and folders in the `MNIST_SAMPLE` dataset structured? Why?
> Structured similar to imagenet
> Main folder -> valid, train
> valid,train -> separate folders for each category

3. Explain how the "pixel similarity" approach to classifying digits works.
> Pixel similarity is where you find the ideal number by averaging all the images of the "number", then you take the mean absolute difference or mean squared difference between your input and the ideal image

4. What is a list comprehension? Create one now that selects odd numbers from a list and doubles them.
> List comprehension is a fast way to create a list from an iterator
> a = [x for x in range(10)]; [2*x for x in a if x%2 > 0]

5. What is a "rank 3 tensor"?
> a tensor with 3 dimensions

6. What is the difference between tensor rank and shape? How do you get the rank from the shape?
> shape gives you information on how big each axis is. Rank is length(shape)

7. What are RMSE and L1 norm?
> RMSE and L1 norm are methods to measure difference between two things. RMSE stands for root mean squared error. L1 norm is the mean absolute difference.

8. How can you apply a calculation on thousands of numbers at once, many thousands of times faster than a Python loop?
> Vectorize the calculations, and then use a gpu

9. Create a 3x3 tensor or array containing the numbers from 1 to 9. Double it. Select the bottom right 4 numbers.
> a = (torch.tensor(range(9))*2).view(3,3); a[1:3, 1:3]

10. What is broadcasting?
> broadcasting is when a math operation happens between two inputs with different shapes (usually 1 dimension), and the smaller shape automatically becomes the shape of the larger shape 

11. Are metrics generally calculated using the training set, or the validation set? Why?
> validation set in order to make sure model is generalizing and not overfitting 

12. What is SGD?
> SGD stands for stochastic gradient descent, and is a method to optimize neural network weights.

13. Why does SGD use mini batches?
> Speeds up training, rather than going 1 example at a time

14. What are the 7 steps in SGD for machine learning?
> Initialize parameters, forward prop, calculate loss, backprop, update weights, repeat, stop

15. How do we initialize the weights in a model?
> Randomly. Although with certain activations, there are certain statistics we use with the random initialization. Eg ReLU -> he intialization

16. What is "loss"?
> loss is a measure the algorithm uses to optimize itself

17. Why can't we always use a high learning rate?
> a high learning rate could cause the loss to increase after each update

18. What is a "gradient"?
> gradient is the slope of a function at a point

19. Do you need to know how to calculate gradients yourself?
> If you use a framework, no. PyTorch does it for you

20. Why can't we use accuracy as a loss function?
> Accuracy is not fine-grain enough. Most gradients would be close to 0, and the updating would be slow

21. Draw the sigmoid function. What is special about its shape?
> Goes between 0 and 1. 1/(1+exp(-x)). Crosses 0.5 at x=0

22. What is the difference between loss and metric?
> Loss is the measure the algorithm uses to evaluate performance. Metric is what humans use.

23. What is the function to calculate new weights using a learning rate?
> w = w - lr*params.grad, or params.data -= lr*params.grad

24. What does the `DataLoader` class do?
> dataloader takes a list of tuples of (x,y), and batches/shuffles them for your model

25. Write pseudo-code showing the basic steps taken each epoch for SGD.
> forward prop, calc loss, backprop, update weight
> pred = model(x)
> loss = loss_func(pred, y)
> loss.backward()
> p -= p.grad*lr
> p.grad.zero_()

26. Create a function which, if passed two arguments `[1,2,3,4]` and `'abcd'`, returns `[(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd')]`. What is special about that output data structure?
> [x for x in zip([1,2,3,4], 'abcd')]

27. What does `view` do in PyTorch?
> view does reshaping

28. What are the "bias" parameters in a neural network? Why do we need them?
> bias parameters are randomly initialized parameters used in the forward prop equation. y = w*x + b. B lets the equation center itself.

29. What does the `@` operator do in python?
> @ = np.matmul = element-wise matrix multiplication

30. What does the `backward` method do?
> backward calculates the gradients from the given point
> eg loss.backward()

31. Why do we have to zero the gradients?
> so that the update is reflective of the current step, and not of previous steps
> loss.backward() accumulates gradients in each function

32. What information do we have to pass to `Learner`?
> Learner(dls, net, metrics)
> Learner(dls, net, opt_func, loss_func, metrics)

33. Show python or pseudo-code for the basic steps of a training loop.
> for i in range(epochs):
> for xb,yb in dl:
> calc_grad(xb, yb, model)
> p.data -= p.grad.data*lr
> p.grad.zero_()

34. What is "ReLU"? Draw a plot of it for values from `-2` to `+2`.
> relu(x) = max(x,0). Relu is 0 for x 0 or less, and = x for x > 0

35. What is an "activation function"?
> activation function is a nonlinearity applied to the linear y=wx+b equation

36. What's the difference between `F.relu` and `nn.ReLU`?
> F.relu is the function.
> nn.Relu is a PyTorch module (layer) that does the same thing.

37. The universal approximation theorem shows that any function can be approximated as closely as needed using just one nonlinearity. So why do we normally use more?
> We use more nonlinearities, which means more layers, for better performance. For the same performance, deeper networks tend to need less memory/calculations.
