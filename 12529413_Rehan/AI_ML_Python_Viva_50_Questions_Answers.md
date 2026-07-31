# AI/ML & Python Viva Questions with Answers

## 1. Why are tuples immutable? What advantage does that provide?

**Answer:** Tuples cannot be modified after creation. This makes them
memory-efficient, hashable (usable as dictionary keys), and safer when
data should not change.

## 2. What happens internally when you write `a = b` in Python?

**Answer:** No new object is created. Both `a` and `b` reference the
same object until one is reassigned (or a mutable object is modified).

## 3. Why are Python lists slower than NumPy arrays for numerical computation?

**Answer:** Python lists store references to objects, while NumPy arrays
store homogeneous data in contiguous memory and perform operations using
optimized C code.

## 4. What is the difference between `append()` and `extend()`?

**Answer:** `append()` adds a single object to the end of a list.
`extend()` adds every element from another iterable.

## 5. Why are dictionaries so fast for searching?

**Answer:** Dictionaries use hash tables, giving average-case O(1)
lookup time.

## 6. What is the difference between a mutable and immutable object?

**Answer:** Mutable objects can be changed after creation (list, dict,
set). Immutable objects cannot (tuple, string, int).

## 7. What happens if you modify a list while iterating over it?

**Answer:** Elements may be skipped or processed multiple times because
the iterator is affected by changes to the list.

## 8. Why is NumPy faster than normal Python lists?

**Answer:** It uses contiguous memory, vectorized operations, and
optimized C implementations.

## 9. What is list comprehension and why is it preferred?

**Answer:** It is a compact way to create lists. It is usually more
readable and often faster than using loops.

## 10. When should you use a set instead of a list?

**Answer:** Use a set when uniqueness matters or when you need fast
membership checking.

## 11. Why do we split the dataset into train and test instead of training on all the data?

**Answer:** To measure how well the model generalizes to unseen data.

## 12. Why can increasing model complexity reduce performance?

**Answer:** A very complex model may overfit the training data and
perform poorly on new data.

## 13. Why do we shuffle data before training?

**Answer:** To prevent learning from the order of the samples and
improve generalization.

## 14. Why do we normalize or standardize data?

**Answer:** It keeps feature scales similar, helping optimization
converge faster and more reliably.

## 15. Can a model have high accuracy but still be bad?

**Answer:** Yes. With imbalanced datasets, a model can achieve high
accuracy while failing on the minority class.

## 16. Why does adding more features not always improve accuracy?

**Answer:** Irrelevant or noisy features can confuse the model and
increase overfitting.

## 17. What happens if the training and testing data come from different distributions?

**Answer:** Model performance usually drops because it learned patterns
that do not match the test data.

## 18. Why is feature selection important?

**Answer:** It removes irrelevant features, reduces overfitting, and
speeds up training.

## 19. Why is more data usually better than a more complex model?

**Answer:** More quality data helps the model learn better patterns and
generalize better.

## 20. Why should missing values be handled before training?

**Answer:** Many algorithms cannot process missing values directly, and
they may bias the model.

## 21. Why can't a neural network work without activation functions?

**Answer:** Without activation functions, multiple layers behave like
one linear transformation.

## 22. Why is ReLU preferred over Sigmoid in hidden layers?

**Answer:** ReLU is computationally simpler and reduces the vanishing
gradient problem.

## 23. Why do deep neural networks require more data?

**Answer:** They have many parameters and need more examples to learn
effectively.

## 24. Why does increasing the number of epochs sometimes decrease performance?

**Answer:** Too many epochs can lead to overfitting.

## 25. Why is Dropout only used during training?

**Answer:** It prevents overfitting by randomly disabling neurons.
During testing, all neurons are used.

## 26. Why do we use batches instead of training on the whole dataset at once?

**Answer:** Batches reduce memory usage and make training faster and
more stable.

## 27. Why is learning rate one of the most important hyperparameters?

**Answer:** It controls the size of parameter updates during
optimization.

## 28. What happens if the learning rate is too high?

**Answer:** The model may overshoot the optimum and fail to converge.

## 29. What happens if the learning rate is too low?

**Answer:** Training becomes very slow and may get stuck before reaching
the optimum.

## 30. Why is Adam optimizer used so frequently?

**Answer:** It adapts the learning rate automatically and usually
converges faster than basic SGD.

## 31. Why do CNNs use small filters like 3×3 instead of one large filter?

**Answer:** Small filters reduce parameters while still capturing
complex features through multiple layers.

## 32. Why do deeper CNNs usually perform better than shallow CNNs?

**Answer:** They learn hierarchical features, from edges to complex
objects.

## 33. Why can't computers understand raw text directly?

**Answer:** Computers process numbers, so text must first be converted
into numerical representations.

## 34. Why do we convert words into vectors?

**Answer:** Machine learning models require numerical input.

## 35. What is the limitation of one-hot encoding?

**Answer:** It creates sparse vectors and cannot represent relationships
between words.

## 36. Why are embeddings better than one-hot vectors?

**Answer:** Embeddings capture semantic similarity between words.

## 37. Why did Transformers replace RNNs in many NLP tasks?

**Answer:** They process sequences in parallel and capture long-range
dependencies more effectively.

## 38. Why is attention called "attention"?

**Answer:** Because the model learns to focus on the most relevant words
for each prediction.

## 39. Why do Transformers need positional encoding?

**Answer:** Self-attention alone has no notion of word order.

## 40. Why is BERT called bidirectional?

**Answer:** It learns from both the left and right context
simultaneously.

## 41. Why is GPT called autoregressive?

**Answer:** It predicts the next token using only previously generated
tokens.

## 42. Why is context important in NLP?

**Answer:** The meaning of a word often depends on surrounding words.

## 43. Why do we use `model.eval()` before testing?

**Answer:** It switches layers like Dropout and BatchNorm into inference
mode.

## 44. Why do we use `torch.no_grad()` during inference?

**Answer:** It disables gradient computation, reducing memory usage and
speeding up inference.

## 45. Why should the training and testing datasets never overlap?

**Answer:** Overlap causes data leakage and gives misleadingly high
performance.

## 46. Why do we save model weights instead of the entire training process?

**Answer:** Weights are sufficient for inference and require much less
storage.

## 47. What is the difference between an epoch and an iteration?

**Answer:** An epoch is one complete pass over the dataset. An iteration
is one parameter update, usually after one batch.

## 48. Why do GPUs train deep learning models faster than CPUs?

**Answer:** GPUs perform thousands of parallel mathematical operations
simultaneously.

## 49. During training, the loss decreases but the accuracy does not improve. Why could this happen?

**Answer:** The model's prediction confidence may improve without
changing the predicted class, or the threshold may not change the
classification.

## 50. If your model performs well on training data but poorly on unseen data, what would you check first?

**Answer:** Check for overfitting. Then consider regularization, more
data, data leakage, and whether the train/test distributions match.
