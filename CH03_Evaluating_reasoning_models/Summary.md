- There are four main evaluation methods for LLMs: multiple choice, verifiers,
  leaderboards, and LLM judges.

- Verification-based evaluation methods allow free-form answers and use external tools to check correctness.

- This chapter focuses on verification-based evaluation by building a math verifier that extracts, normalizes, and checks answers with SymPy.
  - The verification pipeline involves several core steps, from loading the LLM to running the evaluation on a dataset.
  - As part of the verification pipeline, answer extraction uses string parsing to
    locate boxed content (with fallback mechanisms for missing boxes).
  - Another step implements normalization, which standardizes diverse answer formats by stripping LaTeX and converting mathematical notation.
- Finally, the pipeline uses mathematical equivalence checking (via SymPy) to compare expressions symbolically.
- The MATH-500 dataset provides 500 curated math problems for evaluation.
- Prompt templates significantly impact model performance.(especially on small models)
- The reasoning model achieves higher accuracy than the base model, but it requires a much longer running time.
