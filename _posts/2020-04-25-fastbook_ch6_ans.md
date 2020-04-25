# Chapter 6 Answers

1. how could multi-label classification improve the usability of the bear classifier?
> It could predict when there is no bear present, and not only restrict to the 3 classes

2. How do we encode the dependent variable in a multi-label classification problem?
> One hot encoding with MultiCategoryBlock

3. How do you access the rows and columns of a DataFrame as if it was a matrix?
> df.iloc[r,c]

4. How do you get a column by name from a DataFrame?
> df.column or df['column']

5. What is the difference between a dataset and DataLoader?
> a dataset is a list of x,y tuples. A dataloader takes a dataset and creates + shuffles mini-batches

6. What does a Datasets object normally contain?
> a list with 2 lists. One list is of the x input, and the other list contains the y inputs

7. What does a DataLoaders object normally contain?
> List of Minibatch lists of (x,y) tuples

8. What does lambda do in Python?
> Shorthand way to create functions on the fly

9. What are the methods to customise how the independent and dependent variables are created with the data block API?
> get_x, get_y. You put in your functions base on what the dataloader input data is (eg image path vs df)

10. Why is softmax not an appropriate output activation function when using a one hot encoded target?
> Softmax tries to maximize one output. If we have multiple labels/targets, then softmax might push labels out

11. Why is nll_loss not an appropriate loss function when using a one hot encoded target?
> nll_loss is for single label datasets where that target is labeled as a single integer and not one-hot encoded

12. What is the difference between `nn.BCELoss` and `nn.BCEWithLogitsLoss`?
> first one does not do a sigmoid. Second one performs a sigmoid on the activations.

13. Why can't we use regular accuracy in a multi-label problem?
> accuracy used predictions from the highest class, and only had 1 output. Whereas, multi-label probles have multiple outputs, and we need to check the accuracy for each class separately
> we will separately sigmoid each class, threshold, and then compare to target labels

14. When is it okay to tune an hyper-parameter on the validation set?
> when the validation set accuracy sweep curve is flat -> generalizes

15. How is `y_range` implemented in fastai? (See if you can implement it yourself and test it without peaking!)
> y_range gives you the min and max range. Sigmoid squishes input between 0 and 1.
> Now, you just need to change the range -> sigmoid(x)*(max-min)
> Recenter -> sigmoid(x)*(max-min) + min

16. What is a regression problem? What loss function should you use for such a problem?
> a regression problem is where the labels/targets are continuous variables. Use absolute difference or mean squared loss

17. What do you need to do to make sure the fastai library applies the same data augmentation to your inputs images and your target point coordinates?
> Inside datatablock -> blocks=(ImageBlock, PointBlock) , Pointblock lets FA know the labels are coordinates, and to perform the same augmentation as the image
