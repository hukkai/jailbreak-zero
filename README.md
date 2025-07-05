# Jailbreak-Zero

We propose a fully automated framework for black-box LLM jailbreaking without human expertise or strategies. 

No human knowledge, no engineered prompts.

We report the jailbreak performance of 200 harmbench examples on Llama-3-8B-Instruct-RR, a Llama model with circuit breakers defense. 

| Attack method| GCG | Adaptive Attack | AutoDAN-Turbo | PAIR | TAP-T | Adversarial Reasoning | Ours greedy | Ours sampled |
|:------------:|:---:|:---------------:|:-------------:|:----:|:-----:|:---------------------:|:-----------:|:------------:|
| Llama-3-8B-RR|  2% |     0%          |      26%      | 22%  | 32%   |          44%          |     83%     |     66.5%    |


Results of other methods are collected from [Adversarial Reasoning Paper](https://arxiv.org/pdf/2502.01633). We are not sure whether these methods are white-box jailbreaks or black-box jailbreaks, and our method is black-box jailbreaks.

We use the Llama-2 13B judger from [HarmBench](https://huggingface.co/cais/HarmBench-Llama-2-13b-cls).

[`greedy`](harmbench_llama3_rr_greedy.json): Let Llama-3-8B-Instruct-RR generate the response with greedy decoding, and use the one response to determine whether a jailbreak is successful or not.

`sampled`: Let Llama-3-8B-Instruct-RR generate the response with randomness using it default generation config, and generate 5 different responses. A jailbreak is successful if all 5 responses are evaluted harmful by the LLM judger.
