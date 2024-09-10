# Reliable LLM: From Factuality Perception to Expression

\
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/hee9joon/Awesome-Diffusion-Models) 
[![Made With Love](https://img.shields.io/badge/Made%20With-Love-red.svg)](https://github.com/chetanraj/awesome-github-badges)
![License](https://img.shields.io/badge/license-MIT-yellow)
![github license](https://img.shields.io/github/license/AmourWaltz/Reliable-LLM)

## Introduction

The project demonstrates the background about LLM hallucination 👻 as well as the mitigation methods regarding uncertainty 🤔 & knowledge 📓. The research works are collected and systematically clustered in various directions and methods for reliable AI development. The project provides a framework of improving LLMs' factuality **perception** and eliciting factual **expressions** to address the hallucination issue.

*Welcome to participate in this project to share valuable papers and exchange great ideas!* 


## Outline

- [Reliable LLM: From Factuality Perception to Expression](#reliable-llm-from-factuality-perception-to-expression)
  - [Introduction](#introduction)
  - [Outline](#outline)
- [👻 Hallucination \& Factuality](#-hallucination--factuality)
  - [Definition of LLM Hallucination](#definition-of-llm-hallucination)
  - [Causes of LLM Hallucination](#causes-of-llm-hallucination)
  - [Related Works of LLM Hallucination](#related-works-of-llm-hallucination)
    - [Hallucination Detection](#hallucination-detection)
      - [Consistency-based Detection](#consistency-based-detection)
      - [Internal State based Detection](#internal-state-based-detection)
- [📓 LLM Perception of Knowledge](#-llm-perception-of-knowledge)
  - [Knowledge Boundary](#knowledge-boundary)
  - [Related Works of LLM Knowledge](#related-works-of-llm-knowledge)
    - [Knowledge Boundary](#knowledge-boundary-1)
- [🤔 Uncertainty Quantification and Expression](#-uncertainty-quantification-and-expression)
  - [Traditional Model Calibration](#traditional-model-calibration)
  - [Uncertainty Estimation of Generative Models](#uncertainty-estimation-of-generative-models)
  - [Related Works of Uncertainty \& Confidence \& Calibration](#related-works-of-uncertainty--confidence--calibration)
    - [Survey \& Investigation](#survey--investigation)
    - [Uncertainty Quantification](#uncertainty-quantification)
    - [Linguistic Uncertainty Expressions](#linguistic-uncertainty-expressions)
    - [Confidence Expressions Improvements](#confidence-expressions-improvements)
    - [Hallucination Detection by Uncertainty](#hallucination-detection-by-uncertainty)
    - [Factuality Alignment by Confidence](#factuality-alignment-by-confidence)
    - [Generative Model Calibration](#generative-model-calibration)
- [🔭 Future Directions](#-future-directions)

<br/>
<br/>
<br/>

# 👻 Hallucination & Factuality

## Definition of LLM Hallucination

The definitions of hallucination vary and depend on specific tasks. This project focuses on hallucination issues in knowledge-intensive tasks (closed-book QA, dialogue, RAG, commonsense reasoning, translation, etc.), where hallucinations refer to the non-factual, incorrect knowledge in generations unfaithful with world knowledge.

## Causes of LLM Hallucination

The causes of hallucinations vary in unfiltered incorrect statements in pertaining data, limited input length of model architecture, maximum likelihood training strategy, and diverse decoding strategies.

<img src="figs/causes.png"  width=70%/>

Architectures and input lengths, pertaining data and strategy of released LLMs are fixed. Tracing incorrect texts in substantial pertaining data is challenging. This project mainly focuses on detecting hallucinations by tracing what LLMs learn in the pertaining stage and mitigating hallucinations in fine-tuning and decoding.

Comparing open-generation tasks, knowledge-intensive tasks have specific grounding-truth reference - world knowledge. Therefore, we can estimate the knowledge boundary map of an LLM to specify what it knows. It is crucial to ensure the certainty level or honesty of LLMs to a piece of factual knowledge for hallucination detection (from grey area to green area).

## Related Works of LLM Hallucination

### Hallucination Detection

#### Consistency-based Detection

| Title | Conference/Journal | Notes |
| ---- | ---- | ---- |
| [SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models](https://aclanthology.org/2023.emnlp-main.557) | EMNLP 2023 |
| [RCOT: Detecting and Rectifying Factual Inconsistency in Reasoning by Reversing Chain-of-Thought](http://arxiv.org/abs/2305.11499) | prePrint |

#### Internal State based Detection

| Title | Conference/Journal | Notes |
| ---- | ---- | ---- |
| [The Internal State of an LLM Knows When It's Lying](http://arxiv.org/abs/2304.13734) | prePrint |
| [Unsupervised Real-Time Hallucination Detection based on the Internal States of Large Language Models](http://arxiv.org/abs/2403.06448) | prePrint |
| [On the Universal Truthfulness Hyperplane Inside LLMs](http://arxiv.org/abs/2407.08582) | prePrint |
| [INSIDE: LLMs' Internal States Retain the Power of Hallucination Detection](http://arxiv.org/abs/2402.03744) | prePrint |
| [LLM Internal States Reveal Hallucination Risk Faced With a Query](http://arxiv.org/abs/2407.03282) | prePrint |
| [Discovering Latent Knowledge in Language Models Without Supervision](http://arxiv.org/abs/2212.03827) | prePrint |


<br/>
<br/>
<br/>

# 📓 LLM Perception of Knowledge

## Knowledge Boundary

<img src="figs/boundary.png"  width=70%/>

The above diagram can roughly and simply represent the knowledge boundary. However, in reality, like humans, for much knowledge, we exist in a state of uncertainty, rather than only in a state of knowing or not knowing. 
Moreover, maximum likelihood prediction in pertaining makes LLMs be prone to generate over-confident responses. Even if the LLM knows a fact, how to make LLMs accurately tell what they know is also important.

This adds complexity to determining the knowledge boundary, which leads to two challenging questions:

1. How to accurately **perceive (Perception)** the knowledge boundary?
    
    > (Example: Given a question, such as "What is the capital of France?", the model is required to provide its confidence level for this question.)
    > 
2. How to accurately **express (Expression)** knowledge where the boundary is somewhat vague? (Previous work U2Align is a method to enhance expressions. Current interests for the second stage “expression” also lie in “alignment” methods.)
    
    > (Example: If the confidence level for answering "Paris" to the above question is 40%, should the model refuse to answer or provide a response in this situation?)
    >

## Related Works of LLM Knowledge

### Knowledge Boundary

| Title | Conference/Journal | Notes |
| ---- | ---- | ---- |
| [Knowledge of Knowledge: Exploring Known-Unknowns Uncertainty with Large Language Models](https://arxiv.org/abs/2305.13712) | prePrint |
| [Can AI Assistants Know What They Don’t Know?](https://arxiv.org/abs/2401.13275) | prePrint |
| [Do Large Language Models Know What They Don't Know?](http://arxiv.org/abs/2305.18153) | prePrint |
| [Investigating the Factual Knowledge Boundary of Large Language Models with Retrieval Augmentation](http://arxiv.org/abs/2307.11019) | EMNLP 2023 |
| [Does Fine-Tuning LLMs on New Knowledge Encourage Hallucinations?](http://arxiv.org/abs/2405.05904) | prePrint |

<br/>
<br/>
<br/>

# 🤔 Uncertainty Quantification and Expression

## Traditional Model Calibration

-  Models are prone to be **over-confident** in predictions using maximizing likelihood (MLE) training, it is crucial to identify the **confidence score or uncertainty estimation** for reliable AI applications.
-  A model is considered **well-calibrated** if the **confidence score of predictions** (SoftMax probability) are well-aligned with the **actual probability** of answers being correct.
-  **Expected Calibration Error (ECE)** and **Reliability Diagram** is used to measure the calibration performance.

<img src="figs/calibration.png"  width=60%/>

Uncalibrated (left), over-confident (mid) and well-calibrated (right) models.

## Uncertainty Estimation of Generative Models

- To calibrate generative LLMs, we should quantify the **confidence & uncertainty** on generated sentences.
- Uncertainty: Categorized into **aleatoric (data) and epistemic (model)** uncertainty. Frequently measured by the entropy of the prediction to indicate the dispersion of the model prediction.
- Confidence: Generally associated with both the input and the prediction.
- The terms uncertainty and confidence are often used interchangeably.


Although the knowledge boundary is important for knowledge-intensive tasks, there are no specific definitions or concepts in previous works. Current methods for estimating knowledge boundaries refer to confidence/uncertainty estimation methods including ① logit-based methods using token-level probabilities; ② prompt-based methods to make LLMs express confidence in words; ③ sampling-based methods to calculate consistency; and ④ training-based methods to learn the ability to express uncertainty. 

<img src="figs/uncertainty.png"  width=65%/>

## Related Works of Uncertainty & Confidence & Calibration

### Survey & Investigation

| Title | Conference/Journal |
| ---- | ---- |
| [A Survey of Confidence Estimation and Calibration in Large Language Models](https://arxiv.org/abs/2311.08298) | prePrint |
| [Uncertainty Quantification with Pre-trained Language Models: A Large-Scale Empirical Analysis](https://openreview.net/forum?id=gjeQKFxFpZ) | EMNLP 2022 |
| [Uncertainty Estimation and Quantification for LLMs: A Simple Supervised Approach](https://arxiv.org/abs/2404.15993) | prePrint |
| [Confidence Under the Hood: An Investigation into the Confidence-Probability Alignment in Large Language Models](https://arxiv.org/abs/2405.16282) | prePrint |
| [Large Language Models Must Be Taught to Know What They Don’t Know](https://arxiv.org/abs/2406.08391) | prePrint |

### Uncertainty Quantification

| Title | Conference/Journal |
| ---- | ---- |
| [Language Models (Mostly) Know What They Know](https://arxiv.org/abs/2207.05221) | prePrint |
| [Semantic Uncertainty: Linguistic Invariances for Uncertainty Estimation in Natural Language Generation](https://openreview.net/forum?id=VD-AYtP0dve) | ICLR 2023 |
| [Generating with Confidence: Uncertainty Quantification for Black-box Large Language Models](https://arxiv.org/abs/2305.19187) | prePrint |
| [When Quantization Affects Confidence of Large Language Models?](https://arxiv.org/abs/2405.00632) | prePrint |
| [Can LLMs Express Their Uncertainty? An Empirical Evaluation of Confidence Elicitation in LLMs](https://arxiv.org/abs/2306.13063) | ICLR 2024 |
| [Kernel Language Entropy: Fine-grained Uncertainty Quantification for LLMs from Semantic Similarities](https://arxiv.org/abs/2405.20003) | prePrint |
| [Semantically Diverse Language Generation for Uncertainty Estimation in Language Models](https://arxiv.org/abs/2405.20003) | prePrint |
| [Uncertainty is Fragile: Manipulating Uncertainty in Large Language Models](https://www.arxiv.org/abs/2407.11282) | prePrint |


### Linguistic Uncertainty Expressions

| Title | Conference/Journal |
| ---- | ---- |
| [Navigating the Grey Area: Expressions of Overconfidence and Uncertainty in Language Models](https://openreview.net/forum?id=fxotfo1j8T&noteId=2Sajm3fx2g) | EMNLP 2023 |
| [Teaching Models to Express Their Uncertainty in Words](https://openreview.net/forum?id=8s8K2UZGTZ) | TMLR 2022 |
| [Relying on the Unreliable: The Impact of Language Models’ Reluctance to Express Uncertainty](https://arxiv.org/abs/2401.06730) | prePrint |
| ["I'm Not Sure, But...": Examining the Impact of Large Language Models' Uncertainty Expression on User Reliance and Trust](https://arxiv.org/abs/2405.00623) | FAccT 2024 |
| [Can Large Language Models Faithfully Express Their Intrinsic Uncertainty in Words?](https://arxiv.org/abs/2405.00623) | prePrint |


### Confidence Expressions Improvements

This part of works focus on improving confidence expressions of LLMs in a two-stage form by 1) self-prompting LLMs to generate responses to queries and then collecting the samples to construct a dataset with specific features, and 2) fine-tuning LLMs on the collected dataset to improve the specific capability of LLMs.

| Title | Conference/Journal |
| ---- | ---- |
| [Enhancing Confidence Expression in Large Language Models Through Learning from Past Experience](https://arxiv.org/abs/2404.10315) | prePrint |
| [Improving the Reliability of Large Language Models by Leveraging Uncertainty-Aware In-Context Learning](https://arxiv.org/abs/2310.04782) | prePrint |
| [Uncertainty in Language Models: Assessment through Rank-Calibration](https://arxiv.org/abs/2404.03163) | prePrint |
| [SaySelf: Teaching LLMs to Express Confidence with Self-Reflective Rationales](https://arxiv.org/abs/2405.20974) | prePrint |
| [Linguistic Calibration of Language Models](https://arxiv.org/abs/2404.00474) | prePrint |
| [R-Tuning: Instructing Large Language Models to Say ‘I Don’t Know’](https://arxiv.org/pdf/2311.09677) | prePrint |


### Hallucination Detection by Uncertainty

| Title | Conference/Journal |
| ---- | ---- |
| [On Hallucination and Predictive Uncertainty in Conditional Language Generation](https://aclanthology.org/2021.eacl-main.236/) | EACL 2021 |
| [Learning Confidence for Transformer-based Neural Machine Translation](https://aclanthology.org/2022.acl-long.167.pdf) | ACL 2022 |
| [Towards Reliable Misinformation Mitigation: Generalization, Uncertainty, and GPT-4](https://openreview.net/forum?id=cCJGuKJYG8&referrer=%5Bthe%20profile%20of%20Kellin%20Pelrine%5D(%2Fprofile%3Fid%3D~Kellin_Pelrine1)) | EMNLP 2023 |
| [SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models](https://openreview.net/forum?id=RwzFNbJ3Ez&referrer=%5Bthe%20profile%20of%20Mark%20Gales%5D(%2Fprofile%3Fid%3D~Mark_Gales1)) | EMNLP 2023 |
| [Detecting Hallucinations in Large Language Models using Semantic Entropy](https://www.nature.com/articles/s41586-024-07421-0) | Nature |
| [LLM Internal States Reveal Hallucination Risk Faced With a Query](https://arxiv.org/abs/2407.03282) | prePrint |


### Factuality Alignment by Confidence

| Title | Conference/Journal |
| ---- | ---- |
| [When to Trust LLMs: Aligning Confidence with Response Quality](https://arxiv.org/abs/2404.17287) | prePrint |
| [Fine-tuning Language Models for Factuality](http://arxiv.org/abs/2311.08401) | ICLR 2024 |
| [Uncertainty Aware Learning for Language Model Alignment](https://arxiv.org/abs/2406.04854) | ACL 2024 |
| [FLAME: Factuality-Aware Alignment for Large Language Models](http://arxiv.org/abs/2405.01525) | prePrint|
| [Learning to Trust Your Feelings: Leveraging Self-awareness in LLMs for Hallucination Mitigation](http://arxiv.org/abs/2401.15449) | prePrint |
| [Self-Alignment for Factuality: Mitigating Hallucinations in LLMs via Self-Evaluation](http://arxiv.org/abs/2402.09267) | ACL 2024 |


### Generative Model Calibration

| Title | Conference/Journal |
| ---- | ---- |
| [Reducing Conversational Agents’ Overconfidence Through Linguistic Calibration](https://aclanthology.org/2022.tacl-1.50/) | TACL 2022 |
| [Preserving Pre-trained Features Helps Calibrate Fine-tuned Language Models](https://openreview.net/forum?id=NI7StoWHJPT) | ICLR 2023 |
| [Calibrating the Confidence of Large Language Models by Eliciting Fidelity](https://arxiv.org/abs/2404.02655) | prePrint |
| [Few-Shot Recalibration of Language Models](https://arxiv.org/abs/2403.18286) | prePrint |
| [How Can We Know When Language Models Know? On the Calibration of Language Models for Question Answering](https://aclanthology.org/2021.tacl-1.57/) | TACL 2022 |
| [Knowing More About Questions Can Help: Improving Calibration in Question Answering](https://aclanthology.org/2021.findings-acl.172.pdf) | ACL 2021 Findings | [[Link]()] |
| [Just Ask for Calibration: Strategies for Eliciting Calibrated Confidence Scores from Language Models Fine-Tuned with Human Feedback](https://aclanthology.org/2023.emnlp-main.330/) | EMNLP 2023 |
| [Re-Examining Calibration: The Case of Question Answering](https://aclanthology.org/2022.findings-emnlp.204/) | TACL 2021 |
| [Calibrating Large Language Models Using Their Generations Only](https://arxiv.org/abs/2403.05973) | prePrint |
| [Calibrating Large Language Models with Sample Consistency](https://arxiv.org/abs/2402.13904) | prePrint |
| [Linguistic Calibration of Language Models](https://arxiv.org/abs/2404.00474) | prePrint |

<br/>
<br/>
<br/>

# 🔭 Future Directions

1. More advanced methods to assist LLMs hallucination detection and human decisions. (A new paradigm) 
2. Confidence estimation for long-term generations like code, novel, etc. (Benchmark) 
3. Learning to explain and clarify its confidence estimation and calibration. (Natural language)
4. Calibration on human variation (Misalignment between LM measures and human disagreement).
5. Confidence estimation and calibration for multi-modal LLMs.
