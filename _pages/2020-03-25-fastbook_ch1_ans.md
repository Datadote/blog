# Chapter 1 Answers to questions

1) Do you need these for deep learning?
Lots of math T / F
Lots of data T / F
Lots of expensive computers T / F
A PhD T / F

>FFFF

2) Name five areas where deep learning is now the best in the world.
>Vision, NLP, robotics, image generation, playing games, recommendation systems

3) What was the name of the first device that was based on the principle of the artificial neuron?
>The Mark I Perceptron

4) Based on the book of the same name, what are the requirements for "Parallel Distributed Processing"?
>Needs the following: set of processing units, a state of activation, an output function for each unit, a pattern of connectivity among units, a propagation rule for propagating patterns of activity through the network of connectivities, an activation rule to combine inputs, a learning rule where patterns of connectivity are modified by experience, an environment within which the system must operate

?? 5) What were the two theoretical misunderstandings that held back the field of neural networks?
>Marvin Minsky showing 1 layer of NN couldn't perform some math functions (eg XOR)

6) What is a GPU?
>Graphics processing unit, good for matrix multiplication

7) Open a notebook and execute a cell containing: 1+1. What happens?
>Prints out 2

8) Follow through each cell of the stripped version of the notebook for this chapter. Before executing each cell, guess what will happen
>Done

9) Complete the Jupyter Notebook online appendix.
>Done

10) Why is it hard to use a traditional computer program to recognize images in a photo?
>You have to write out rules explicitly. To recognize images would take an unreasonable amount of rules.

11) What did Samuel mean by "Weight Assignment"?
>Each processing unit has a weight associated with it. This weight is updated through training.

12) What term do we normally use in deep learning for what Samuel called "Weights"?
>model parameters

13) Draw a picture that summarizes Arthur Samuel's view of a machine learning model
>Done

14) Why is it hard to understand why a deep learning model makes a particular prediction?
>Model learns from data, and does not explain the rules explicitly

15) What is the name of the theorem that a neural network can solve any mathematical problem to any level of accuracy?
>Universal Approximation Theorm

16) What do you need in order to train a model?
>Data

17) How could a feedback loop impact the rollout of a predictive policing model?
>Positive feedback increasing a bias. Examples include predictive models for arrests or collaborative filtering for youtube videos.

18) Do we always have to use 224x224 pixel images with the cat recognition model?
>Historical reasons on imagenet

19) What is the difference between classification and regression?
>Classification has discrete outputs. Linear regression has continuous outputs

20) What is a validation set? What is a test set? Why do we need them?
>Validation set is a portion of the dataset set aside for the human to evaluate performance. It is not used for training, but for evaluation of the training

21) What will fastai do if you don't provide a validation set?
>Fastai will automatically make a validation set based off 20% of your training data

22) Can we always use a random sample for a validation set? Why or why not?
>No, because there is a chance the validation set does not represent the actual use case. An example is time series forecasting, we want to predict the future given the past. If our training data contains data in the future of the validation set, then there is data leakage.

23) What is overfitting? Provide an example.
>Overfitting is when the model memorizes pictures, and does not learn general features. An indicator of overfitting is when there is a large difference between the training and validation loss. An example might be a car dataset where the model sees a lot of Toyota cars, but can't tell Honda cars are cars as well. Maybe the model learned to associate cars with the Toyota logo.

24) What is a metric? How does it differ to "loss"?
>A metric is a performance indicator for humans to understand. A loss is a performance indicator for models to use in order to train, and adjust weights.

25) How can pretrained models help?
>Pretrained models help by leveraging knowledge learned on other tasks. An example is image classification. Models trained on ImageNet learn low level features such as edges, textures, gradients, and can transfer this learned knowledge. Small datasets might not have enough data to let untrained models learn these low level features.

26) What is the "head" of a model?
>The head of a model is a smaller neural network added to the last layer of a pretrained model. This head is trainable, and fine-tuned to the applicable dataset.

27) What kinds of features do the early layers of a CNN find? How about the later layers?
>Early layers of a CNN learn low level features such as edges, lines, textures, gradients. Later layers combine the low level features, and contain more complex features such as shapes, text, faces.

28) Are image models only useful for photos?
>No, image models can used for other types of data as well. The caveat is the other types of data must be converted into images at some point. One example is speech. Speech spectrograms can be turned into pictures, and then fed into a model.

29) What is an "architecture"?
>An architecture is the skeleton of a neural network. This architecture includes the number of layers, number of weights, pattern of connections, and activation functions.

30) What is segmentation?
>Segmentation is the act of semantically classifying every pixel of an image.

31) What is y_range used for? When do we need it?
>y_range is used to indicate continuous variables for tabular data.

32) What are "hyperparameters"?
>Hyperparameters are parameters set by the human, and not learned by the model training. Examples of hyperparameters are the learning rate, activation functions, number of layers, number of weights to use. An example of not a parameter, but not a hyperparameter, are the weights of the neural network neurons. These weights are learned through training.

33) What's the best way to avoid failures when using AI in an organization?
>Best way to avoid failures is to understand the importance of validation and test sets. Validation sets are used to verify the training performance. If the validation sets are used too often, there is a chance to overfit to the validation set. As a result, a test set is used to "double check" a model's performance. A test set should be used seldomly to avoid overfitting to the test set.
