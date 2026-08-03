# Job Role: Machine Learning Engineer

## Interview Questions & Answers

### General Machine Learning
**1. What is the difference between supervised and unsupervised learning?**
Supervised learning uses labeled data to train models (e.g., predicting house prices), while unsupervised learning finds hidden patterns in unlabeled data (e.g., customer segmentation).

**2. What is overfitting, and how do you prevent it?**
Overfitting happens when a model learns the training data too well, including the noise, causing poor performance on new data. It can be prevented using techniques like dropout, regularization, early stopping, and data augmentation.

**3. Explain the Bias-Variance Tradeoff.**
Bias is the error from overly simplistic assumptions (underfitting), while variance is the error from hypersensitivity to small fluctuations in training data (overfitting). The goal is to find a balance where both are minimized.

**4. What is Cross-Validation?**
It is a resampling method used to evaluate a model by dividing the data into subsets, training on some, and validating on others (e.g., k-fold cross-validation) to ensure the model generalizes well.

**5. How do you handle missing data in a dataset?**
Missing data can be handled by dropping the rows/columns if the missing percentage is high, or by imputing values using the mean, median, mode, or predictive modeling.

**6. What is the difference between classification and regression?**
Classification predicts discrete category labels (e.g., spam or not spam), whereas regression predicts continuous numerical values (e.g., temperature).

**7. Define Precision and Recall.**
Precision is the ratio of true positive predictions to the total predicted positives. Recall is the ratio of true positive predictions to the actual total positives.

**8. What is the F1 Score?**
The F1 score is the harmonic mean of Precision and Recall, useful when you need a balance between the two, especially on imbalanced datasets.

**9. What is a Confusion Matrix?**
A table used to evaluate the performance of a classification model, showing True Positives, True Negatives, False Positives, and False Negatives.

**10. Why is data scaling/normalization important?**
It ensures that numerical features are on a similar scale so that algorithms (especially distance-based ones like KNN or gradient descent-based ones) converge faster and are not biased by larger numbers.

### Deep Learning Basics
**11. What is an Activation Function?**
A mathematical function applied to a neural network node to introduce non-linearity, allowing the network to learn complex patterns.

**12. Name common activation functions.**
ReLU (Rectified Linear Unit), Sigmoid, Tanh, and Softmax.

**13. What is the vanishing gradient problem?**
During backpropagation in deep networks, gradients can become extremely small, preventing earlier layers from updating their weights effectively.

**14. What is the role of an Optimizer?**
Optimizers adjust the neural network's weights and learning rates to minimize the loss function. Common examples are Adam, RMSprop, and SGD.

**15. What is Backpropagation?**
The process of calculating the gradient of the loss function with respect to each weight by the chain rule, updating weights backwards from the output to the input layer.

**16. What is a Loss Function?**
It measures how far the model's predictions are from the actual labels. Examples include Cross-Entropy for classification and Mean Squared Error (MSE) for regression.

**17. What is the difference between an Epoch and a Batch?**
An epoch is one complete pass through the entire training dataset. A batch is a smaller subset of the dataset processed before the model updates its weights.

**18. What is Dropout?**
A regularization technique where randomly selected neurons are ignored during training to prevent overfitting.

**19. Why is ReLU widely used in deep learning?**
ReLU is computationally efficient and helps mitigate the vanishing gradient problem by not capping positive values.

**20. What is Transfer Learning?**
Taking a pre-trained model developed for a specific task and reusing it as the starting point for a different but related task, saving compute resources and time.

### Computer Vision (CV)
**21. What is a Convolutional Neural Network (CNN)?**
A class of neural networks highly effective for analyzing visual imagery. They use convolutional layers to automatically extract spatial features like edges and textures from images.

**22. What is the purpose of a Pooling Layer?**
Pooling (e.g., Max Pooling) reduces the spatial dimensions of an image representation, decreasing the number of parameters and computational load while retaining important features.

**23. What problem does the ResNet architecture solve?**
ResNet (Residual Networks) solves the degradation problem (vanishing gradients) in very deep networks by introducing "skip connections" that bypass some layers.

**24. What makes EfficientNet unique?**
EfficientNet uses a compound scaling method that uniformly scales the network's width, depth, and resolution in a principled way, providing high accuracy with fewer parameters.

**25. What is Data Augmentation in image processing?**
Artificially expanding the training dataset by applying random transformations like rotations, flips, scaling, and color adjustments to prevent overfitting.

**26. What is Image Segmentation?**
The process of partitioning an image into multiple segments (pixel-level classification) to simplify its representation and locate boundaries/objects.

**27. Explain the difference between Object Detection and Image Classification.**
Classification assigns a single label to an entire image. Object detection assigns labels and draws bounding boxes around multiple specific objects within an image.

**28. What is a stride in a CNN?**
Stride is the number of pixels by which a filter shifts across the input image. A larger stride produces a smaller output feature map.

**29. What is padding in a CNN?**
Adding extra pixels (usually zeros) around the border of an input image so the filter can process edge pixels properly and maintain the output's spatial size.

**30. Why do we flatten data before the fully connected layers in a CNN?**
Fully connected layers require a 1D array as input, so the 2D/3D output matrices from the convolutional and pooling layers must be flattened into a single continuous vector.

### Natural Language Processing (NLP)
**31. What is Tokenization?**
The process of breaking raw text down into smaller, meaningful pieces called tokens, such as words, subwords, or characters.

**32. What are Word Embeddings?**
Dense vector representations of words where words with similar meanings have similar vector values. Examples include Word2Vec and GloVe.

**33. What is TF-IDF?**
Term Frequency-Inverse Document Frequency. It evaluates how relevant a word is to a document in a collection by measuring word frequency against its rarity across all documents.

**34. How does an NLP classification pipeline generally work?**
Text cleaning -> Tokenization -> Vectorization (e.g., Embeddings) -> Passing to an ML/DL model -> Outputting a probability for a category (e.g., spam vs non-spam).

**35. What is the difference between Stemming and Lemmatization?**
Stemming aggressively chops off word endings to find the root, often resulting in non-words. Lemmatization uses vocabulary and morphological analysis to return a proper dictionary root word.

**36. What are Stop Words?**
Commonly used words (e.g., "the", "is", "in") that are often removed during NLP preprocessing because they carry very little unique information.

**37. What is an RNN (Recurrent Neural Network)?**
A type of neural network designed to handle sequential data by maintaining a hidden state that captures information about previous inputs.

**38. Why are Transformers preferred over RNNs today?**
Transformers process entire sequences simultaneously rather than sequentially, allowing for massive parallelization and better handling of long-range dependencies in text.

**39. What is the Attention Mechanism?**
A technique that allows a model to weigh the importance of different words in an input sequence dynamically, focusing heavily on contextually relevant words.

**40. Name a popular text classification architecture.**
BERT (Bidirectional Encoder Representations from Transformers) is highly popular for text classification, sentiment analysis, and question answering.

### Frameworks & Practical Implementation
**41. What is the primary difference between PyTorch and TensorFlow?**
Historically, PyTorch uses a dynamic computational graph (created on the fly), making debugging easier, while TensorFlow used a static graph. Today, both are highly capable, but PyTorch is heavily favored in research, and TensorFlow is popular for production deployment.

**42. What is a Tensor?**
A fundamental data structure in ML frameworks. It is a multi-dimensional array containing elements of a single data type (scalars are 0D, vectors 1D, matrices 2D, etc.).

**43. How do you move a model to a GPU in PyTorch?**
By using the `.to(device)` method, e.g., `model.to('cuda')`.

**44. What is `model.train()` and `model.eval()` in PyTorch?**
`model.train()` sets the network to training mode (enabling dropout and batch normalization updates), while `model.eval()` sets it to evaluation mode for inference.

**45. What is the purpose of `optimizer.zero_grad()` in PyTorch?**
It clears the old gradients from the previous step before calculating new ones. Otherwise, PyTorch accumulates gradients by default.

**46. How do you save and load a PyTorch model?**
You save the model's state dictionary using `torch.save(model.state_dict(), 'model.pth')` and load it using `model.load_state_dict(torch.load('model.pth'))`.

**47. What is a DataLoader?**
A utility in frameworks like PyTorch that wraps a dataset and provides an iterable over it, managing batching, shuffling, and multi-process data loading.

**48. Why is freezing layers useful in transfer learning?**
It prevents the pre-trained weights from being updated during early training, preserving the general features already learned and reducing computation time.

**49. What is Git, and why is it important for ML Engineers?**
Git is a version control system. It is vital for tracking changes in code, collaborating with other engineers, and maintaining a history of model experiments and data pipelines.

**50. How would you design an AI crop classification system?**
I would gather and preprocess an image dataset of crops, apply data augmentation, use a pre-trained CNN architecture like ResNet50 or EfficientNetB0 for feature extraction, train the model, evaluate using a confusion matrix, and deploy it as an API.