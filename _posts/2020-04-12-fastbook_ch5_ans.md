# Chapter 5 Answers

1. Why do we first resize to a large size on the CPU, and then to a smaller size on the GPU?
> Resize to large size in order to perform augmentations. This allows margin to do augmentations without creating empty zones. Then resize to smaller size.
All data augmentations, after item_tfms resize, are performed together on GPU and only have 1 interpolation step.

2. If you are not familiar with regular expressions, find a regular expression tutorial, and some problem sets, and complete them. Have a look on the book website for suggestions.
> ** Not done

3. What are the two ways in which data is most commonly provided, for most deep learning datasets?
> Either label in name, or labels are separated as folders. split(train,valid), then folders for each category in each folder

4. Look up the documentation for `L` and try using a few of the new methods is that it adds.
> ** Not done

5. Look up the documentation for the Python pathlib module and try using a few methods of the Path class.
> Done

6. Give two examples of ways that image transformations can degrade the quality of the data.
> 1) Reflection padding artifacts 2) Parts of images being interpolated incorrectly

7. What method does fastai provide to view the data in a DataLoader?
> ".show_batch()"

8. What method does fastai provide to help you debug a DataBlock?
> ".summary() -> datablock.summary(filePath_with_images)"

9. Should you hold off on training a model until you have thoroughly cleaned your data?
> No, you can use your trained model to help you clean your data

10. What are the two pieces that are combined into cross entropy loss in PyTorch?
> softmax and negative log likelihood
> log_softmax + nll_loss

11. What are the two properties of activations that softmax ensures? Why is this important?
> softmax ensures probabilities lie between 0-1, and the sum of all the predictions = 1

12. When might you want your activations to not have these two properties?
> in your loss function because a 0.99 and 0.999 probability might not affect much in gradients even though 0.999 is 10x more confident than 0.99

13. Calculate the "exp" and "softmax" columns of <<bear_softmax>> yourself (i.e. in a spreadsheet, with a calculator, or in a notebook).
> Done

14. Why can't we use torch.where to create a loss function for datasets where our label can have more than two categories?
> torch.where finds true/false scenarios. While you could have a lot of torch.where statements, it is not as efficient as doing softmax

15. What is the value of log(-2)? Why?
> nan or undefined because log is not defined for numbers less than or equal to 0

16. What are two good rules of thumb for picking a learning rate from the learning rate finder?
> Use either 10x less than the min, or use where the loss downward slope is steepest

17. What two steps does the fine_tune method do?
> fit_one_cycle on just the head, then unfreeze all with discriminative learning rates, and fit_one_cycle

18. In Jupyter notebook, how do you get the source code for a method or function?
> ?? before or after a function, eg ??learn.fine_tune or learn.fine_tune??

19. What are discriminative learning rates?
> each layer has a different learning rate. You are discriminating learning rates among the layers

20. How is a Python slice object interpreted when past as a learning rate to fastai?
> slice(1e-6, 1e-4). First argument goes to shallowest layer. Last argument goes to deepest layer. Layers in between get a multiplicative equidistant value.

21. Why is early stopping a poor choice when using one cycle training?
> With 1cycle training, there is a chance that early stopping picks a model before the 1cycle learning rate reaches small values. So, perhaps the accuracy lowers, increase a little, and then goes lower towards the end

22. What is the difference between resnet 50 and resnet101?
> resnet101 has 51 more layers than resnet50

23. What does to_fp16 do?
> Enables calculations to use less precise numbers where possible during training
> Speeds up training, and reduces memory load
