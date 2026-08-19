# Summary

Reinforcement learning (RL) can be used to train LLMs on human preference labels and verifiable rewards.

- RL is typically applied as post-training on top of a pretrained base model, and it can be inserted at different stages of an LLM pipeline, including reasoning training and preference tuning.
- RL with human feedback (RLHF) optimizes for human preferences via a two-stage setup: train a reward model from ranked responses, and then use reward scores to update the LLM.
- RL with verifiable rewards (RLVR) simplifies RLHF by replacing learned reward models with deterministic, automatically computed verifiers (for example, math answer checking).
- GRPO is a policy optimization algorithm that turns verifier rewards into parameter updates. Because GRPO directly optimizes the model using sequence-level rewards without requiring a separate value model, it is particularly convenient.
- GRPO is a more resource-friendly alternative to other RL algorithms for LLMs because it avoids training a separate value model and instead derives learning signals from comparisons within a group of sampled rollouts.
- A “rollout” refers to a full model answer (completion) for a prompt; rewards, advantages, and log probabilities are computed from the rollout in later steps.
- Rewards are computed by a verifier that grants a reward only if the final answer is both correct and extractable in a required format, like "\boxed{}".
- Raw rewards are transformed into advantages by normalizing each rollout reward relative to the group mean and standard deviation.
- GRPO also relies on sequence-level log probabilities, which are computed by summing token log probabilities over the generated answer tokens. Sequence log probabilities, together with the advantages, form the core policy-gradient objective in GRPO.
- The full GRPO loss computation is combined into a single function that performs rollout sampling, reward computation, advantage calculation, log probability computation, and policy-gradient loss calculation.
- The surrounding training loop is a standard deep learning loop, with the key difference being that the loss comes from GRPO rather than conventional classification losses.
- Training is resource intensive because each step requires generating multiple, potentially long rollouts, but even short GRPO runs can increase MATH-500 accuracy from 15% to 47%.
