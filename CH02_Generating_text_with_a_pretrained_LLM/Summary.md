- Using LLMs to generate text involves multiple key steps:
  - Setting up the coding environment to run LLM code and install necessary dependencies
  - Loading a pretrained base LLM (such as Qwen3 0.6B), which will be extended
    with reasoning capabilities in later chapters

  - Initializing and using a tokenizer, which converts text input into token IDs and decodes output back to human-readable form

- Text generation in LLMs follows a sequential (autoregressive) process, where the
  model generates one token at a time by predicting the next most likely token.

- The speed and efficiency of text generation can be improved through
  - KV caching, which stores intermediate states to avoid recomputing previously
    encountered input tokens at each step
  - Model compilation using torch.compile, which optimizes runtime performance

- This chapter lays the technical foundation for reasoning capabilities in upcom-
  ing chapters by implementing a functional, efficient text generation pipeline
  using a pretrained base LLM.
