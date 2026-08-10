# Summary

- Conventional LLM training occurs in several stages:
  - Pretraining, in which the model learns language patterns from vast amounts of text
  - Instruction fine-tuning, which improves the model’s responses to user prompts
  - Preference tuning, which aligns model outputs with human preferences
- Reasoning methods are applied on top of a conventional LLM.
- Reasoning in LLMs refers to improving a model so that it explicitly generates intermediate steps (chain of thought) before producing a final answer, which often increases accuracy on multistep tasks.

- Reasoning in LLMs is different from rule-based reasoning, and it likely also works differently from human reasoning. Currently, the consensus is that reasoning in LLMs relies on statistical pattern matching.
- Pattern matching in LLMs relies purely on statistical associations learned from data, enabling fluent text generation but lacking explicit logical inference.
- Improving reasoning in LLMs can be achieved in a few ways:
  - Inference-time compute scaling improves reasoning without retraining (e.g., chain-of-thought prompting).
  - Reinforcement learning involves training models explicitly with reward signals.
  - Supervised fine-tuning and distillation, using examples from stronger reasoning models.
- Building reasoning models from scratch provides practical insights into LLM capabilities, limitations, and computational tradeoffs.
