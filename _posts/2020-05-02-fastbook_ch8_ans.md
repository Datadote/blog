# Chapter 8 Answers

1. What problem does collaborative filtering solve?
> Bring recommendations to users

2. How does it solve it?
> Create an embedding vector for users and items, and then compare vector distances

3. Why might a collaborative filtering predictive model fail to be a very useful recommendation system?
> If there is a positive feedback loop that reinforces a small group. For example, anime watchers watch a lot of anime, and the recommender may bias towards anime

4. What does a crosstab representation of collaborative filtering data look like?
> Left side y axis represents users+user_embeddings, x axis represents items+item_embeddings. The cross section represents the dependent variable

5. Write the code to create a crosstab representation of the MovieLens data (you might need to do some web searching!)
> *** Not done

6. What is a latent factor? Why is it "latent"?
> Latent factor are indirect variables, not directly observed, but seen through a combination of other variables. Latent means hidden or concealed

7. What is a dot product? Calculate a dot product manually using pure python with lists.
> Dot product is the element wise multiplication of two vectors, and then summing all the products

8. What does `pandas.DataFrame.merge` do?
> Combines data frames together along, and aligns data with a specific column

9. What is an embedding matrix?
> Embedding matrix is a matrix of users/items and latent factors

10. What is the relationship between an embedding and a matrix of one-hot encoded vectors?
> You use the one-hot encoded vector to pull the embeddings of 1 user. You can think of an embedding as a compressed version of the one-hot encoded vectors

11. Why do we need `Embedding` if we could use one-hot encoded vectors for the same thing?
> Embeddings save a lot more memory especially if the there is high cardinality. Also, embeddings allow turning categories into continuous variables

12. What does an embedding contain before we start training (assuming we're not using a prertained model)?
> Randomly initialized numbers

13. Create a class (without peeking, if possible!) and use it.
> *** Not done

14. What does `x[:,0]` return?
> Every row of column 0 (first column)

15. Rewrite the `DotProduct` class (without peeking, if possible!) and train a model with it
> *** Not done

16. What is a good loss function to use for MovieLens? Why? 
> Mean squared error because we have a range of values (1,2,3,4,5)

17. What would happen if we used `CrossEntropy` loss with MovieLens? How would we need to change the model?
> ??? It wouldn't work because it looks for a 1 or 0. You need to do categorical cross entropy

18. What is the use of bias in a dot product model?
> The bias centers the function in order to balance with other neurons

19. What is another name for weight decay?
> L2 regularization

20. Write the equation for weight decay (without peeking!)
> total_loss = loss + sum(wd*(w**2))

21. Write the equation for the gradient of weight decay. Why does it help reduce weights?
> weight = weight - lr*grad
> grad = grad + 2*weight
> weight = weight - lr*(grad + 2*weight)
> weight = (1-2*lr)*weight - lr*grad

22. Why does reducing weights lead to better generalization?
> More neurons/weights are used, and therefore have to share features among themselves versus just 1 weight

23. What does `argsort` do in PyTorch?
> argsort gives you the indices of the sorted values

24. Does sorting the movie biases give the same result as averaging overall movie ratings by movie? Why / why not?
> No, sorting the movie biases gives additional information that given a movie, the people who like that genre, may not like that movie. Whereas the overall movie rating just gives the average across people

25. How do you print the names and details of the layers in a model?
> layer.model

26. What is the "bootstrapping problem" in collaborative filtering?
> How to recommend things to new users who have no previous history. You can't bootstrap them to previous knowledge, because you don't have any

27. How could you deal with the bootstrapping problem for new users? For new movies?
> Start people at the average, or ask questions, or get meta data

28. How can feedback loops impact collaborative filtering systems?
> They could impact systems negatively if there is a reinforcing bias

29. When using a neural network in collaborative filtering, why can we have different number of factors for movie and user?
> Each represent different complexities. We will flatten, and concatenate all these features before feeding into the neural network

30. Why is there a `nn.Sequential` in the `CollabNN` model?
> To create a small NN model

31. What kind of model should be use if we want to add metadata about users and items, or information such as date and time, to a collaborative filter model?
> EmbeddingNN, which inherits from TabularModel
