# Chapter 2 answers to questions

1. Provide an example of where the bear classification model might work poorly, due to structural or style differences to the training data.
> Night time where the lighting is darker and images are more grayscale

2. Where do text models currently have a major deficiency?
> Text models can mimic text well, but don't seem to understand what they are mimicing. Text models are not good at generating correct responses

3. What are possible negative societal implications of text generation models?
> Biases can be built into these models. These text models could be used for online trolling or spreading misinfromation on social media

4. In situations where a model might make mistakes, and those mistakes could be harmful, what is a good alternative to automating a process?
> Add a human into the process to check the model's predictions

5. What kind of tabular data is deep learning particularly good at?
> Text, eg titles, reviews, comments

6. What's a key downside of directly using a deep learning model for recommendation systems?
> Deep learning models are predictors, not recommenders. So, the models look at your history, and find similar items. Rather than try to push your boundaries a little to see if you might like something new

7. What are the steps of the Drivetrain approach?
> 1) Define objective 2) Figure out the levers 3) Get data 4) Use the data to model how the objective changes using the available levers

8. How do the steps of the Drivetrain approach map to a recommendation system?
The Drivetrain approach is a methodology to create actionable outcomes from data, and not just predictions.
1) Want more sales through recommendations
2) Rank the recommendations
3) Run experiments to see if new recommendations cause new sales
4) Compare new model with existing/baseline model to see if changes caused more sales from recommendations

9. Create an image recognition model using data you curate, and deploy it on the web.
> Done

10. What is `DataLoaders`?
> A dataloaders is a collection of dataloader objects from the FASTAI library
A dataloader object contains information on how to retrieve the data (paths, names, labels, splits)

11. What four things do we need to tell fastai to create `DataLoaders`?
1) What kind of data we are working with
2) How to get the list of items
3) How to label these images
4) How to create a validation set

12. What does the `splitter` parameter to `DataBlock` do?
> Splitter tells the dataloaders function how to split the data into training and validation sets

13. How do we ensure a random split always gives the same validation set?
> Pass a seed=### argument into the RandomSplitter. Use the same seed number each time

14. What letters are often used to signify the independent and dependent variables?
> Independent = x
> Dependent = y

15. What's the difference between crop, pad, and squish resize approaches? When might you choose one over the other?
> Crop takes a centered crop of the image
> Pad adds 0's to the perimeter of images if the images are too small (black borders)
> Squish squeezes an image into the specified size. *Distorts image*
> If the images are always centered, crop is ok. If you want the whole image without any changes, and have different sizes, then padding works. Use squish if you need faster compute, and the application actually has similar distortions.

16. What is data augmentation? Why is it needed?
> Data augmentation is when you add transforms (change contrast, brightness, rotate, skew, flip, etc.) to images. Data augmentation is used when the training data is small, which seems to be the case for all image data sets.

17. What is the difference between `item_tfms` and `batch_tfms`?
> Item_tfms does transformations on a per item basis, and is usually just used for resizing images. Item_tfms works before batch_tfms
> Batch_tfms applies transforms on a batch at a time. As a result, it assumes the inputs are all the same shape
> item_tfms and batch_tfms are arguments for the DataLoader class

18. What is a confusion matrix?
> A confusion matrix is a table showing correct/wrong predictions, as well as false positives and false negatives. On the table, the y>axis are the actual labels. On the x>axis are the model predictions. Given a table x,y point, that point represents the number of times the actual label, and predicted label happened together. The diagonal of the table represents when the actual label and predicted label were the same.

19. What does `export` save?
> Export saves a '.pkl' file. This file contains the model architecture, parameters, and also 
the definition of how to create the dataloaders

20. What is it called when we use a model for getting predictions, instead of training?
> Inference

21. What are IPython widgets?
> Software that allows you to use JavaScript and Python in a web browser

22. When might you want to use CPU for deployment? When might GPU be better?
> Use CPU for deployment when the user experience is adequate. CPU is generally cheaper. May want a GPU if you get enough traffic, and are able to batch together jobs

23. What are the downsides of deploying your app to a server, instead of to a client (or edge) device such as a phone or PC?
> Deploying to your server means you have to maintain the hardware, and also the scaling burden is on you. On a phone, it is horizontal scaling and the client "takes" the scaling cost

24. What are 3 examples of problems that could occur when rolling out a bear warning system in practice?
> 1) Out of domain data, 2) Domain shift
> Examples of "out of domain data" are low resolution photos, night time photos, latency between prediction and response to user

25. What is "out of domain data"?
> Input data that has a distribution a lot different than the training data distribution

26. What is "domain shift"?
> Domain shift is when your input data distribution changes, and moves away from the original training data distribution

27. What are the 3 steps in the deployment process?
1) Manual process, run models in parallel and check outputs by hand
2) Limited scope deployment, try the model in the wild for a limited time/area and supervise the performance
3) Gradual expansion, expand the scope. This will require a good reporting system in order to get debugging information if things go wrong. For example, out of domain data or domain shift.

28. For a project you're interested in applying deep learning to, consider the thought experiment "what would happen if it went really, really well?"
> Done

29. Start a blog, and write your first blog post. For instance, write about what you think deep learning might be useful for in a domain you're interested in.
> Done. Thinking about an invasive flower classifier.

Furthur research
1. Consider how the Drivetrain approach maps to a project or problem you're interested in.
> I think the approach let's you understand how different parts interact

2. When might it be best to avoid certain types of data augmentation?
> When the data augmentation transforms images to look like another image label. For example, on MNIST, you do not want to do a horizontal flip because a b and d could look the same. Another example are numbers where you do not want to flip vertically because a 6 and a 9 could look the same 
