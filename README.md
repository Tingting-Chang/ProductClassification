# ProductClassification
Classify the fashion products by category

This code embeds the images and text, then runs KMeans clustering. A manual review of a few samples from each cluster chosen by minimum distance to cluster center is done to assign labels to each cluster.
To get the image embedding, we prepare the images by rescaling them, then use VGG16 pretrained on imagenet, then apply PCA to reduce to 100 dimensions.
To get text embedding, we use doc2vec to get 100 dimensional embedding.
We then concat the embeddings, normalize, and run clustering.

# Questions:
1. Why are you designing the solution in this way?
- Because the dataset is small, we want to use transfer learning for both images and text.

2. What are the aspects that you considered when designing?
- Scalability, if the number of samples we want to classify go up, we should be able to still classify them without having to do much extra work. If all we ever want is to classify 1k samples, this could probably even be done manually.

3. What are the cases your solution covers, how are they covered and why are they important?
- This solution allows classifying new samples as they come in, without having to do any additional work, since it just requires running the embedding through the kmeans model.

4. What are the cases your solution does not cover and what are the ways you can extend your current solution for them?
- If the number of product categories changes, then we would have to repeat this exercise and redo the manual labeling.
