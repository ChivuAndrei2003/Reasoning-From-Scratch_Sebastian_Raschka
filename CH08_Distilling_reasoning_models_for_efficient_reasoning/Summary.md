# Summary

- Distillation trains a smaller student LLM on outputs produced by a larger teacher LLM.
- Hard distillation is usually more practical than soft distillation because teacher logits are often unavailable and teacher text outputs are much cheaper to store and reuse.
- We used DeepSeek-R1 as the teacher model and Qwen3 0.6B as the student model.
- The distillation dataset was built from the 12,000 MATH training problems that do not overlap with MATH-500.
- Each training sample combines a rendered prompt with the teacher reasoning trace and final answer, optionally separated via <think>...</think> tags.
- For efficiency, we tokenize the dataset once, filter it by sequence length, and reuse the processed examples across multiple epochs.
- The training objective is answer-only cross-entropy, which is equivalent to the negative average log probability of the correct next tokens.
- A distillation training loop is a standard supervised learning loop that includes shuffling the training examples each epoch, computing the loss, backpropagating, updating the model weights, and tracking validation loss.
- The validation loss is the main signal to watch during training. Additionally, it is useful and recommended that you evaluate checkpoints periodically on benchmark datasets.
