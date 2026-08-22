# Summary

- Training reasoning models with GRPO can become unstable over longer runs, even when the implementation is correct and rewards initially improve.
- Interpreting GRPO training requires tracking multiple metrics jointly (average rewards, response length, evaluation accuracy, advantage statistics, and entropy):
  - Basic metrics such as loss mainly serve as sanity checks in GRPO and should not be overinterpreted in isolation.
  - Advantage statistics provide useful diagnostics: the mean should remain near zero by design, while the standard deviation reflects the strength and stability of the learning signal.
  - Entropy measures how uncertain the model is during generation. Very low entropy can signal collapse, and very large entropy can indicate unstable updates and randomness in the model responses.
- Clipped policy ratios limit how much the policy can change between updates and can substantially improve training stability over longer runs.
- Adding a KL divergence term constrains long-term drift from a reference model but can destabilize training when the rewards collapse.
- For math reasoning tasks, several recent systems report better stability and performance by omitting the KL term altogether.
- Auxiliary format rewards can improve the response structure, such as encouraging the use of <think> and </think> tokens.
- Beyond the original GRPO algorithm, many recent extensions modify advantage normalization, importance sampling, clipping strategies, and KL handling to improve stability and efficiency.
