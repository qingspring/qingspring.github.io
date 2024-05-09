---
title: Llama3
description: Examples of text, typography, math equations, diagrams, flowcharts, pictures, videos, and more.
author: cotes
date: 2019-08-08 11:33:00 +0800
categories: [Blogging, Demo]
tags: [typography]
pin: true
math: true
mermaid: true
---


# Llama3
## Blog
[https://ai.meta.com/blog/meta-llama-3/](https://ai.meta.com/blog/meta-llama-3/)
### Model

- we opted for a relatively standard decoder-only transformer architecture in Llama 3
- Llama 3 uses a tokenizer with a vocabulary of 128K tokens that encodes language much more efficiently
- To improve the inference efficiency of Llama 3 models, we’ve adopted grouped query attention (GQA) across both the 8B and 70B sizes

- We trained the models on sequences of 8,192 tokens, using a mask to ensure self-attention does not cross document boundaries.
### Data

- Llama 3 is pretrained on over 15T tokens that were all collected from publicly available sources
- we developed a series of data-filtering pipelines. These pipelines include using heuristic filters, NSFW filters, semantic deduplication approaches, and text classifiers to predict data quality.
- we used Llama 2 to generate the training data for the text-quality classifiers that are powering Llama 3.
### Pretraining

- To train our largest Llama 3 models, we combined three types of parallelization: data parallelization, model parallelization, and pipeline parallelization.
- We performed training runs on two custom-built [24K GPU clusters](https://engineering.fb.com/2024/03/12/data-center-engineering/building-metas-genai-infrastructure/).

### Instruct fine-tuning

- Our approach to post-training is a combination of supervised fine-tuning (SFT), rejection sampling, proximal policy optimization (PPO), and direct preference optimization (DPO). 
- Some of our biggest improvements in model quality came from carefully curating this data and performing multiple rounds of quality assurance on annotations provided by human annotators.
- Learning from preference rankings via PPO and DPO also greatly improved the performance of Llama 3 on reasoning and coding tasks.
![image](https://github.com/qingspring/qingspring.github.io/assets/18527768/c13cddf9-cb8c-4141-bce4-e251aebee197)


## Get started
Huggingface：[https://huggingface.co/meta-llama/Meta-Llama-3-8B-Instruct](https://huggingface.co/meta-llama/Meta-Llama-3-8B-Instruct)
[**https://github.com/meta-llama/llama-recipes**](https://github.com/meta-llama/llama-recipes)

###  Download
HF-mirror下载模型
```bash
# 下载模型
export HF_ENDPOINT=https://hf-mirror.com
huggingface-cli download --resume-download NousResearch/Meta-Llama-3-8B --local-dir NousResearch/Meta-Llama-3-8B

# 下载数据集
huggingface-cli download --repo-type dataset --resume-download mlabonne/orpo-dpo-mix-40k --local-dir mlabonne/orpo-dpo-mix-40k
```
### Fine-tune
Fine-tune Llama 3 with ORPO： https://huggingface.co/blog/mlabonne/orpo-llama-3

Fine-tuning libraries
- TRL
- Axolotl
- LLaMa-Factory

## Evaluation
### Open LLM Leaderboard
https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard

### lm-evaluation-harness
https://github.com/EleutherAI/lm-evaluation-harness
```bash
!lm_eval --model hf \
    --model_args pretrained=NousResearch/Meta-Llama-3-8B,load_in_4bit=True \
    --tasks hellaswag \
    --device cuda:0 \
    --batch_size 8 \
    --limit 1000 \
    --log_samples \
    --write_out \
    --output_path output/Meta-Llama-3-8B
```
使用方法：https://github.com/EleutherAI/lm-evaluation-harness/blob/main/docs/interface.md

https://colab.research.google.com/drive/1HEXbYBnf9lG65xCPmU5lBGC1bA77tqLJ#scrollTo=XNldTYc2OTVt
