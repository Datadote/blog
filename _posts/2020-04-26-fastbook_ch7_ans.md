# Chapter 7 Answers

1. What is the difference between ImageNet and Imagenette? When is it better to experiment on one versus the other?
> Imagenet original is a dataset with ~1.3M images and 1000 classes. Imagenette is a much smaller subset of 10 distinct classes

2. What is normalization?
> Normalization is the process of making the data input have 0 mean and std 1

3. Why didn't we have to care about normalization when using a pretrained model?
> If no Normalization.from_stats() is passed to batch_tfms, FA calculates 
> the stats from a single batch of your data

4. What is progressive resizing?
> Training on images that gradually increase in size as training progresses.
> For example, first fit_one_cycle on size 128, then fine_tune on 224

5. Implement progressive resizing in your own project. Did it help?
> *** Did not try

6. What is test time augmentation? How do you use it in fastai?
> TTA is when you data augment test images, and average the predictions
> In FA, do learn.tta(n=4)

7. Is using TTA at inference slower or faster than regular inference? Why?
> Slower, because we need each additional image needs an inference as well

8. What is Mixup? How do you use it in fastai?
> Mixup is when you mixup images by adding weighted versions together.
> This means the image pixels are added together. Weighted labels are added together as well
> Implemented in fa2 by adding a callback into the learner
> You will also want to use the LabelSmoothingCrossEntropy loss func
> Example: cnn_learner(dls, ..., cbs = MixUp(), loss_func=LabelSmoothingCrossEntropy())

9. Why does Mixup prevent the model from being too confident?
> Because it allows the model to optimize predictions to values between 0, and 1. Instead of always forcing to 0/1

10. Why does a training with Mixup for 5 epochs end up worse than a training without Mixup?
> It is harder to see what's in a MixUp image. Also, now it needs to predict continuous numbers instead of a 1/0

11. What is the idea behind label smoothing?
> If there are mislabels in your dataset, trying to optimize to 1/0 predictions can be harmful. 
> Encourage model to be less confident by having labels between 1/0, and then adding a little "epsilon" error to every other prediction
> Example for one hot-encoded -> [0, 1, 0, 0] -> [0.1, 0.7, 0.1, 0.1]

12. What problems in your data can label smoothing help with?
> Mislabeled data or harder to label data. I think label smoothing can
> give a higher fidelity to data if you start adding in prediction + confidence level
> For example [0, 1, 0, 0] -> [0, 0.9, 0, 0] -> Do you care if all sum to 1? Or 
just that they are constrainted between 0 and 1 (a range)

13. When using label smoothing with 5 categories, what is the target associated with the index 1?
> 1 - epsilon + epsilon/N -> where N = 5

14. What is the first step to take when you want to prototype quick experiments on a new dataset.
> If the dataset is large, find a smaller subset that is representative of the whole. This will let you try experiments much faster. Key is finding smallest 
dataset that is representative and able to discriminate between techniques
> For example, Imagenet (1000 classes) -> Imagenette (10 classes)
