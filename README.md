# Jailbreak-Zero

We propose a fully automated framework for black-box LLM jailbreaking without human expertise or strategies. 

No human knowledge, no engineered prompts.

We report the jailbreak performance of 200 harmbench examples on [Llama-3-8B-Instruct-RR](https://huggingface.co/GraySwanAI/Llama-3-8B-Instruct-RR), a Llama model with circuit breakers defense. 

| Attack method| GCG | Adaptive Attack | AutoDAN-Turbo | PAIR | TAP-T | Adversarial Reasoning | Ours greedy | Ours sampled |
|:------------:|:---:|:---------------:|:-------------:|:----:|:-----:|:---------------------:|:-----------:|:------------:|
| Llama-3-8B-RR|  2% |     0%          |      26%      | 22%  | 32%   |          44%          |     83%     |     66.5%    |

The results of other methods are obtained from the [Adversarial Reasoning Paper](https://arxiv.org/pdf/2502.01633). Some of those methods are white or gray box jailbreaks. In contrast, our approach is a black-box jailbreak.

We evaluate jailbreak success using the [LLaMA-2-13B judge](https://huggingface.co/cais/HarmBench-Llama-2-13b-cls) provided by HarmBench.


[`greedy`](harmbench_llama3_rr_greedy.json): We prompt LLaMA-3-8B-Instruct-RR with greedy decoding to generate a single response. The jailbreak is considered successful if that response is judged harmful by the LLM judge.

[`sampled`](harmbench_llama3_rr_sample.json): We prompt LLaMA-3-8B-Instruct-RR using its default generation settings to produce 5 diverse responses with randomness. The jailbreak is considered successful only if all 5 responses are judged harmful.

Paper and code will come soon.
