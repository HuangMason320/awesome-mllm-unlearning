<div align="center">

# Awesome MLLM Unlearning

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![GitHub Stars](https://img.shields.io/github/stars/HuangMason320/awesome-mllm-unlearning?style=flat)](https://github.com/HuangMason320/awesome-mllm-unlearning/stargazers)
[![Last Commit](https://img.shields.io/github/last-commit/HuangMason320/awesome-mllm-unlearning)](https://github.com/HuangMason320/awesome-mllm-unlearning/commits/main)
[![License](https://img.shields.io/github/license/HuangMason320/awesome-mllm-unlearning)](LICENSE)

A curated list of papers, benchmarks, and resources on **machine unlearning for multimodal large language models (MLLMs)** and **vision-language models (VLMs)**.

</div>

## About

Multimodal models trained on web-scale image-text data can memorize private identities, copyrighted characters, and harmful visual concepts. **MLLM unlearning** aims to remove a specific piece of knowledge (a person, a concept, or a harmful behavior) from a trained model without retraining from scratch, while keeping unrelated capabilities intact. Compared with text-only LLM unlearning, the multimodal setting raises its own questions:

- **Where does the knowledge live?** In the vision encoder, the projector, or the language backbone, and does forgetting in one modality transfer to the other?
- **What counts as forgotten?** Refusing, answering wrongly, and truly erasing are different outcomes, and suppressed knowledge can often be recovered by attacks or relearning.
- **How do we evaluate it?** Fictitious-identity benchmarks, real-world entities, continual deletion requests, and fairness and safety settings each test a different part of the problem.

**Scope.** This list covers generative MLLMs/LVLMs (e.g., LLaVA, Qwen-VL, InternVL), contrastive VLMs (e.g., CLIP), and multimodal models beyond vision (audio, video, vision-language-action). Text-only LLM unlearning and text-to-image diffusion concept erasure are out of scope; see [Related Awesome Lists](#related-awesome-lists) for those.

> **90 papers** so far, ordered newest first within each section. Contributions are welcome: see [CONTRIBUTING.md](CONTRIBUTING.md) or open an issue.

## Contents

- [Surveys](#surveys) (2)
- [Benchmarks & Datasets](#benchmarks--datasets) (20)
- [Unlearning Methods for MLLMs](#unlearning-methods-for-mllms) (28)
- [Safety, Hallucination & Spurious Correlations](#safety-hallucination--spurious-correlations) (8)
- [Evaluation, Robustness & Attacks](#evaluation-robustness--attacks) (9)
- [CLIP & Contrastive Vision-Language Models](#clip--contrastive-vision-language-models) (18)
- [Beyond Vision: Audio, Video & Embodied Models](#beyond-vision-audio-video--embodied-models) (4)
- [Toolkits & Frameworks](#toolkits--frameworks) (1)
- [Related Awesome Lists](#related-awesome-lists)
- [Contributing](#contributing)
- [Citation](#citation)

## Surveys

| Title | Venue | Date | Code |
| :---- | :---: | :--: | :--: |
| [Multimodal Unlearning Across Vision, Language, Video, and Audio: Survey of Methods, Datasets, and Benchmarks](https://arxiv.org/abs/2607.07907) | ACL 2026 Findings | 2026-07 | - |
| [Machine Unlearning in Generative AI: A Survey](https://arxiv.org/abs/2407.20516) | arXiv | 2024-07 | [![Star](https://img.shields.io/github/stars/franciscoliu/Awesome-GenAI-Unlearning.svg?style=social&label=Star)](https://github.com/franciscoliu/Awesome-GenAI-Unlearning) |

<p align="right"><a href="#awesome-mllm-unlearning">⬆ back to top</a></p>

## Benchmarks & Datasets

| Title | Venue | Date | Code |
| :---- | :---: | :--: | :--: |
| **[IDUnlearn-Bench]** [What Does It Mean to Forget a Person? Individual-Level Unlearning in Vision-Language Models](https://arxiv.org/abs/2609.33481) | arXiv | 2026-09 | - |
| [PRMU: A Corpus-Free Benchmark for Person-Centric Knowledge Unlearning in Multimodal Large Language Models](https://arxiv.org/abs/2608.11149) | arXiv | 2026-08 | [![Star](https://img.shields.io/github/stars/2231122/PRMU.svg?style=social&label=Star)](https://github.com/2231122/PRMU) |
| **[UNLINK-VL]** [Does Forgetting Transfer Across Modalities? A Real-World Benchmark for Cross-Modal Knowledge Unlearning Evaluation](https://arxiv.org/abs/2608.03791) | arXiv | 2026-08 | - |
| **[FAIRGET]** [Unlearning Under Imbalance: Benchmarking Fairness in Multimodal LLM Unlearning](https://arxiv.org/abs/2607.21300) | arXiv | 2026-07 | - |
| [PPE-Bench: A Benchmark for Evaluating MLLM Unlearning under Private-Public Entanglement](https://arxiv.org/abs/2607.02897) | EMNLP 2026 | 2026-07 | - |
| [MLUBench: A Benchmark for Lifelong Unlearning Evaluation in MLLMs](https://arxiv.org/abs/2606.12809) | ICML 2026 | 2026-06 | [![Star](https://img.shields.io/github/stars/lihe-maxsize/Lifelong_Unlearning_main.svg?style=social&label=Star)](https://github.com/lihe-maxsize/Lifelong_Unlearning_main) |
| [PPU-Bench: Real World Benchmark for Personalized Partial Unlearning in Vision Language Models](https://arxiv.org/abs/2605.08800) | arXiv | 2026-05 | - |
| [ICU-Bench: Benchmarking Continual Unlearning in Multimodal Large Language Models](https://arxiv.org/abs/2605.05938) | arXiv | 2026-05 | [![Star](https://img.shields.io/github/stars/AstorYH/ICU-Bench.svg?style=social&label=Star)](https://github.com/AstorYH/ICU-Bench) |
| [Erase Persona, Forget Lore: Benchmarking Multimodal Copyright Unlearning in Large Vision Language Models](https://arxiv.org/abs/2605.03547) | LREC 2026 | 2026-05 | - |
| **[MedForget]** [Hierarchy-Aware Multimodal Unlearning for Medical AI](https://arxiv.org/abs/2512.09867) | arXiv | 2025-12 | [![Star](https://img.shields.io/github/stars/fengli-wu/MedForget.svg?style=social&label=Star)](https://github.com/fengli-wu/MedForget) |
| [UMU-Bench: Closing the Modality Gap in Multimodal Unlearning Evaluation](https://papers.neurips.cc/paper_files/paper/2025/hash/18b0ee1e95f4007541e57fe507b5167e-Abstract-Datasets_and_Benchmarks_Track.html) | NeurIPS 2025 (D&B) | 2025-12 | - |
| [OFFSIDE: Benchmarking Unlearning Misinformation in Multimodal Large Language Models](https://arxiv.org/abs/2510.22535) | arXiv | 2025-10 | [![Star](https://img.shields.io/github/stars/zh121800/OFFSIDE.svg?style=social&label=Star)](https://github.com/zh121800/OFFSIDE) |
| **[MLLMU-Med]** [From Learning to Unlearning: Biomedical Security Protection in Multimodal Large Language Models](https://arxiv.org/abs/2508.04192) | arXiv | 2025-08 | - |
| [PULSE: Practical Evaluation Scenarios for Large Multimodal Model Unlearning](https://arxiv.org/abs/2507.01271) | NeurIPS 2025 Workshop | 2025-07 | - |
| **[UnLOK-VQA]** [Unlearning Sensitive Information in Multimodal LLMs: Benchmark and Attack-Defense Evaluation](https://arxiv.org/abs/2505.01456) | TMLR | 2025-05 | [![Star](https://img.shields.io/github/stars/Vaidehi99/UnLOK-VQA.svg?style=social&label=Star)](https://github.com/Vaidehi99/UnLOK-VQA) |
| [PEBench: A Fictitious Dataset to Benchmark Machine Unlearning for Multimodal Large Language Models](https://arxiv.org/abs/2503.12545) | arXiv | 2025-03 | - |
| **[FIUBench]** [Benchmarking Vision Language Model Unlearning via Fictitious Facial Identity Dataset](https://arxiv.org/abs/2411.03554) | ICLR 2025 | 2024-11 | [![Star](https://img.shields.io/github/stars/SaFo-Lab/FIUBench.svg?style=social&label=Star)](https://github.com/SaFo-Lab/FIUBench) |
| **[MLLMU-Bench]** [Protecting Privacy in Multimodal Large Language Models with MLLMU-Bench](https://arxiv.org/abs/2410.22108) | NAACL 2025 | 2024-10 | [![Star](https://img.shields.io/github/stars/franciscoliu/MLLMU-Bench.svg?style=social&label=Star)](https://github.com/franciscoliu/MLLMU-Bench) |
| [CLEAR: Character Unlearning in Textual and Visual Modalities](https://arxiv.org/abs/2410.18057) | ACL 2025 Findings | 2024-10 | [![Star](https://img.shields.io/github/stars/somvy/multimodal_unlearning.svg?style=social&label=Star)](https://github.com/somvy/multimodal_unlearning) |
| [MU-Bench: A Multitask Multimodal Benchmark for Machine Unlearning](https://arxiv.org/abs/2406.14796) | NeurIPS 2024 Workshop | 2024-06 | [![Star](https://img.shields.io/github/stars/CLU-UML/MU-Bench.svg?style=social&label=Star)](https://github.com/CLU-UML/MU-Bench) |

<p align="right"><a href="#awesome-mllm-unlearning">⬆ back to top</a></p>

## Unlearning Methods for MLLMs

| Title | Venue | Date | Code |
| :---- | :---: | :--: | :--: |
| [CUSE: Fine-Grained Multimodal Unlearning with Counterfactual Guidance and On-Policy Self-Distillation](https://arxiv.org/abs/2610.14763) | arXiv | 2026-10 | - |
| [Decoupling Knowledge Forgetting and Refusal Learning in MLLM Unlearning](https://arxiv.org/abs/2610.14605) | arXiv | 2026-10 | - |
| [SIEVE: Selective attention-value Suppression for Vision-Language Models Unlearning](https://arxiv.org/abs/2610.01962) | arXiv | 2026-10 | - |
| **[PAVA]** [Where Identity Lives: Localized, Retain-Free Identity Unlearning in Multimodal Large Language Models](https://arxiv.org/abs/2608.30649) | EMNLP 2026 Findings | 2026-08 | - |
| [AIM: Anchor Identity Features, Then Match for Multimodal Large Language Model Unlearning](https://arxiv.org/abs/2608.28312) | EMNLP 2026 Findings | 2026-08 | - |
| [A Model Merging Approach for Continual MLLM Unlearning](https://arxiv.org/abs/2608.04548) | arXiv | 2026-08 | - |
| **[CLRP / AMU-Bench]** [Toward Fine-Grained Forgetting: Attribute Unlearning for Multimodal Large Language Models](https://arxiv.org/abs/2608.01008) | arXiv | 2026-08 | - |
| **[SMU]** [Stochastic Meta-Unlearning: Bridging Language Backbone and Multimodal Unlearning](https://arxiv.org/abs/2607.18615) | arXiv | 2026-07 | - |
| [One Modality to Forget Them All: Enhancing Cross-Modal Unlearning in Vision-Language Models](https://arxiv.org/abs/2607.16442) | arXiv | 2026-07 | - |
| [SPACE: Source-free Proxy Anchor Concept Erasure for MLLMs](https://arxiv.org/abs/2606.09868) | arXiv | 2026-06 | - |
| [Visual-Noise Guided In-Context Distillation for Multimodal Large Language Model Unlearning](https://arxiv.org/abs/2606.00105) | arXiv | 2026-05 | - |
| [ASRU: Activation Steering Meets Reinforcement Unlearning for Multimodal Large Language Models](https://arxiv.org/abs/2605.15687) | arXiv | 2026-05 | - |
| [Null Space Constrained Contrastive Visual Forgetting for MLLM Unlearning](https://arxiv.org/abs/2605.05909) | arXiv | 2026-05 | - |
| [Which Concepts to Forget and How to Refuse? Decomposing Concepts for Continual Unlearning in Large Vision-Language Models](https://arxiv.org/abs/2603.21484) | CVPR 2026 | 2026-03 | - |
| [Visual-Guided Key-Token Regularization for Multimodal Large Language Model Unlearning](https://arxiv.org/abs/2601.22020) | arXiv | 2026-01 | - |
| **[KVW]** [Knowledge Vector Weakening: Efficient Training-free Unlearning for Large Vision-Language Models](https://arxiv.org/abs/2601.21794) | arXiv | 2026-01 | - |
| [Robust MLLM Unlearning via Visual Knowledge Distillation](https://arxiv.org/abs/2512.11325) | arXiv | 2025-12 | - |
| [Towards Reasoning-Preserving Unlearning in Multimodal Large Language Models](https://arxiv.org/abs/2512.17911) | arXiv | 2025-11 | - |
| [Towards Benign Memory Forgetting for Selective Multimodal Large Language Model Unlearning](https://arxiv.org/abs/2511.20196) | ECCV 2026 | 2025-11 | [![Star](https://img.shields.io/github/stars/zeng-zhen/S-MLLMUn.svg?style=social&label=Star)](https://github.com/zeng-zhen/S-MLLMUn) |
| [SineProject: Machine Unlearning for Stable Vision Language Alignment](https://arxiv.org/abs/2511.18444) | CVPR 2026 | 2025-11 | - |
| [AUVIC: Adversarial Unlearning of Visual Concepts for Multi-modal Large Language Models](https://arxiv.org/abs/2511.11299) | AAAI 2026 | 2025-11 | [![Star](https://img.shields.io/github/stars/HaokunChen245/AUVIC.svg?style=social&label=Star)](https://github.com/HaokunChen245/AUVIC) |
| **[MIP-Editor]** [Cross-Modal Unlearning via Influential Neuron Path Editing in Multimodal Large Language Models](https://arxiv.org/abs/2511.06793) | AAAI 2026 (Oral) | 2025-11 | [![Star](https://img.shields.io/github/stars/PreckLi/MIP-Editor.svg?style=social&label=Star)](https://github.com/PreckLi/MIP-Editor) |
| [Cross-Modal Attention Guided Unlearning in Vision-Language Models](https://arxiv.org/abs/2510.07567) | arXiv | 2025-10 | - |
| [MLLMEraser: Achieving Test-Time Unlearning in Multimodal Large Language Models through Activation Steering](https://arxiv.org/abs/2510.04217) | arXiv | 2025-10 | - |
| [SAUCE: Selective Concept Unlearning in Vision-Language Models with Sparse Autoencoders](https://arxiv.org/abs/2503.14530) | ICCV 2025 | 2025-03 | - |
| **[MANU]** [Modality-Aware Neuron Pruning for Unlearning in Multimodal Large Language Models](https://arxiv.org/abs/2502.15910) | ACL 2025 | 2025-02 | [![Star](https://img.shields.io/github/stars/franciscoliu/MANU.svg?style=social&label=Star)](https://github.com/franciscoliu/MANU) |
| [MMUnlearner: Reformulating Multimodal Machine Unlearning in the Era of Multimodal Large Language Models](https://arxiv.org/abs/2502.11051) | ACL 2025 Findings | 2025-02 | [![Star](https://img.shields.io/github/stars/Z1zs/MMUnlearner.svg?style=social&label=Star)](https://github.com/Z1zs/MMUnlearner) |
| **[SIU / MMUBench]** [Single Image Unlearning: Efficient Machine Unlearning in Multimodal Large Language Models](https://arxiv.org/abs/2405.12523) | NeurIPS 2024 | 2024-05 | - |

<p align="right"><a href="#awesome-mllm-unlearning">⬆ back to top</a></p>

## Safety, Hallucination & Spurious Correlations

| Title | Venue | Date | Code |
| :---- | :---: | :--: | :--: |
| [Partition-Aware Unlearning for Removing Spurious Correlations in Large Vision-Language Models](https://arxiv.org/abs/2608.29996) | arXiv | 2026-08 | - |
| [Object Hallucination-Free Reinforcement Unlearning for Vision-Language Models](https://arxiv.org/abs/2605.08031) | arXiv | 2026-05 | [![Star](https://img.shields.io/github/stars/XMUDeepLIT/HFRU.svg?style=social&label=Star)](https://github.com/XMUDeepLIT/HFRU) |
| [Relationship-Aware Safety Unlearning for Multimodal LLMs](https://arxiv.org/abs/2603.14185) | arXiv | 2026-03 | - |
| [Beyond Superficial Unlearning: Sharpness-Aware Robust Erasure of Hallucinations in Multimodal LLMs](https://arxiv.org/abs/2601.16527) | arXiv | 2026-01 | - |
| [Safety Mirage: How Spurious Correlations Undermine VLM Safety Fine-Tuning and Can Be Mitigated by Machine Unlearning](https://arxiv.org/abs/2503.11832) | ICLR 2026 | 2025-03 | [![Star](https://img.shields.io/github/stars/OPTML-Group/VLM-Safety-Unlearn.svg?style=social&label=Star)](https://github.com/OPTML-Group/VLM-Safety-Unlearn) |
| [SafeEraser: Enhancing Safety in Multimodal Large Language Models through Multimodal Machine Unlearning](https://arxiv.org/abs/2502.12520) | ACL 2025 Findings | 2025-02 | [![Star](https://img.shields.io/github/stars/yuu250/SafeEraser.svg?style=social&label=Star)](https://github.com/yuu250/SafeEraser) |
| [Cross-Modal Safety Alignment: Is textual unlearning all you need?](https://arxiv.org/abs/2406.02575) | EMNLP 2024 Findings | 2024-05 | - |
| [EFUF: Efficient Fine-grained Unlearning Framework for Mitigating Hallucinations in Multimodal Large Language Models](https://arxiv.org/abs/2402.09801) | EMNLP 2024 | 2024-02 | - |

<p align="right"><a href="#awesome-mllm-unlearning">⬆ back to top</a></p>

## Evaluation, Robustness & Attacks

| Title | Venue | Date | Code |
| :---- | :---: | :--: | :--: |
| [Are We Really Measuring Forgetting? Pitfalls in Evaluating Machine Unlearning for Multimodal LLMs](https://arxiv.org/abs/2610.19613) | arXiv | 2026-10 | - |
| [Exploring and Bridging Knowledge Holes in Unlearned Multimodal Large Language Models](https://arxiv.org/abs/2608.01849) | arXiv | 2026-08 | - |
| [POPS: Recovering Unlearned Multi-Modality Knowledge in MLLMs with Prompt-Optimized Parameter Shaking](https://arxiv.org/abs/2607.06649) | arXiv | 2026-07 | - |
| [On the Robustness of Machine Unlearning for Vision-Language Models](https://arxiv.org/abs/2605.26992) | arXiv | 2026-05 | [![Star](https://img.shields.io/github/stars/XMUDeepLIT/VLM-UnL-Attack.svg?style=social&label=Star)](https://github.com/XMUDeepLIT/VLM-UnL-Attack) |
| [Before Forgetting, Learn to Remember: Revisiting Foundational Learning Failures in LVLM Unlearning Benchmarks](https://arxiv.org/abs/2605.03759) | ACL 2026 Findings | 2026-05 | - |
| [Metric Unreliability in Multimodal Machine Unlearning: A Systematic Analysis and Principled Unified Score](https://arxiv.org/abs/2605.02206) | arXiv | 2026-05 | [![Star](https://img.shields.io/github/stars/abdullahak07/UnifiedUnl.svg?style=social&label=Star)](https://github.com/abdullahak07/UnifiedUnl) |
| [Suppression Is Not Forgetting: Residual Recoverability in Visual Concept Unlearning for VLMs](https://arxiv.org/abs/2604.03114) | arXiv | 2026-04 | - |
| [SUA: Stealthy Multimodal Large Language Model Unlearning Attack](https://arxiv.org/abs/2506.17265) | EMNLP 2025 | 2025-06 | - |
| **[PUBG]** [Rethinking Post-Unlearning Behavior of Large Vision-Language Models](https://arxiv.org/abs/2506.02541) | arXiv | 2025-06 | - |

<p align="right"><a href="#awesome-mllm-unlearning">⬆ back to top</a></p>

## CLIP & Contrastive Vision-Language Models

| Title | Venue | Date | Code |
| :---- | :---: | :--: | :--: |
| [Open Vocabulary Domain Unlearning](https://arxiv.org/abs/2609.31356) | NeurIPS 2026 | 2026-09 | - |
| [Not All Patches Are Equally Forgettable: Spatially Localized Domain Unlearning in Vision-Language Models](https://arxiv.org/abs/2609.17790) | BMVC 2026 | 2026-09 | - |
| [ICED: Concept-level Machine Unlearning via Interpretable Concept Decomposition](https://arxiv.org/abs/2605.14309) | arXiv | 2026-05 | - |
| [EASE: Federated Multimodal Unlearning via Entanglement-Aware Anchor Closure](https://arxiv.org/abs/2605.00733) | arXiv | 2026-05 | - |
| [Bias Redistribution in Visual Machine Unlearning: Does Forgetting One Group Harm Another?](https://arxiv.org/abs/2604.08111) | arXiv | 2026-04 | - |
| [SALMUBench: A Benchmark for Sensitive Association-Level Multimodal Unlearning](https://arxiv.org/abs/2603.26316) | CVPR 2026 | 2026-03 | [![Star](https://img.shields.io/github/stars/cvc-mmu/salmubench.svg?style=social&label=Star)](https://github.com/cvc-mmu/salmubench) |
| [Erasing CLIP Memories: Non-Destructive, Data-Free Zero-Shot class Unlearning in CLIP Models](https://arxiv.org/abs/2512.14137) | arXiv | 2025-12 | - |
| [Selective, Controlled and Domain-Agnostic Unlearning in Pretrained CLIP: A Training- and Data-Free Approach](https://arxiv.org/abs/2512.14113) | arXiv | 2025-12 | - |
| **[ADU]** [Approximate Domain Unlearning for Vision-Language Models](https://arxiv.org/abs/2510.08132) | NeurIPS 2025 (Spotlight) | 2025-10 | - |
| [Unlearning the Noisy Correspondence Makes CLIP More Robust](https://arxiv.org/abs/2507.03434) | ICCV 2025 | 2025-07 | - |
| [Targeted Forgetting of Image Subgroups in CLIP Models](https://arxiv.org/abs/2506.03117) | arXiv | 2025-06 | - |
| [Machine Unlearning in Hyperbolic vs. Euclidean Multimodal Contrastive Learning: Adapting Alignment Calibration to MERU](https://arxiv.org/abs/2503.15166) | arXiv | 2025-03 | [![Star](https://img.shields.io/github/stars/alex-pv01/HAC.svg?style=social&label=Star)](https://github.com/alex-pv01/HAC) |
| [CLIPErase: Efficient Unlearning of Visual-Textual Associations in CLIP](https://arxiv.org/abs/2410.23330) | ACL 2025 | 2024-10 | [![Star](https://img.shields.io/github/stars/Tianyu-yang-anna/ClipErase-ACL.svg?style=social&label=Star)](https://github.com/Tianyu-yang-anna/ClipErase-ACL) |
| **[SLUG]** [Targeted Unlearning with Single Layer Unlearning Gradient](https://arxiv.org/abs/2407.11867) | ICML 2025 | 2024-07 | [![Star](https://img.shields.io/github/stars/CSIPlab/SLUG.svg?style=social&label=Star)](https://github.com/CSIPlab/SLUG) |
| [Zero-Shot Class Unlearning in CLIP with Synthetic Samples](https://arxiv.org/abs/2407.07485) | WACV 2025 | 2024-07 | - |
| [MUC: Machine Unlearning for Contrastive Learning with Black-box Evaluation](https://arxiv.org/abs/2406.03603) | TMLR | 2024-06 | [![Star](https://img.shields.io/github/stars/EhanW/Alignment-Calibration.svg?style=social&label=Star)](https://github.com/EhanW/Alignment-Calibration) |
| [Unlearning Backdoor Threats: Enhancing Backdoor Defense in Multimodal Contrastive Learning via Local Token Unlearning](https://arxiv.org/abs/2403.16257) | arXiv | 2024-03 | - |
| [MultiDelete for Multimodal Machine Unlearning](https://arxiv.org/abs/2311.12047) | ECCV 2024 | 2023-11 | [![Star](https://img.shields.io/github/stars/CLU-UML/MultiDelete.svg?style=social&label=Star)](https://github.com/CLU-UML/MultiDelete) |

<p align="right"><a href="#awesome-mllm-unlearning">⬆ back to top</a></p>

## Beyond Vision: Audio, Video & Embodied Models

| Title | Venue | Date | Code |
| :---- | :---: | :--: | :--: |
| [Sparse Feature Policy Unlearning Mitigates State Hallucination in Vision-Language-Action Models](https://arxiv.org/abs/2610.09496) | arXiv | 2026-10 | - |
| [FedCoT-VQA: A Federated Learning and Unlearning Framework for Chain-of-Thought Planners in VideoQA](https://arxiv.org/abs/2609.26814) | arXiv | 2026-09 | - |
| [Machine Unlearning for Speech Question Answering in Large Audio-Language Models](https://arxiv.org/abs/2609.13195) | arXiv | 2026-08 | - |
| [VLA-Forget: Vision-Language-Action Unlearning for Embodied Foundation Models](https://arxiv.org/abs/2604.03956) | ACL 2026 Workshop | 2026-04 | [![Star](https://img.shields.io/github/stars/raviranjan-ai/VLA-Forget.svg?style=social&label=Star)](https://github.com/raviranjan-ai/VLA-Forget) |

<p align="right"><a href="#awesome-mllm-unlearning">⬆ back to top</a></p>

## Toolkits & Frameworks

| Title | Venue | Date | Code |
| :---- | :---: | :--: | :--: |
| [Open-MMUnlearning: Unifying Methods and Evaluation for MLLM Unlearning](https://arxiv.org/abs/2610.10358) | arXiv | 2026-10 | [![Star](https://img.shields.io/github/stars/JunkaiChen1/Open-MMunlearning.svg?style=social&label=Star)](https://github.com/JunkaiChen1/Open-MMunlearning) |

<p align="right"><a href="#awesome-mllm-unlearning">⬆ back to top</a></p>

## Related Awesome Lists

- [chrisliu298/awesome-llm-unlearning](https://github.com/chrisliu298/awesome-llm-unlearning): papers on LLM unlearning, including some multimodal work.
- [tamlhp/awesome-machine-unlearning](https://github.com/tamlhp/awesome-machine-unlearning): a broader survey-backed list on machine unlearning.
- [BradyFU/Awesome-Multimodal-Large-Language-Models](https://github.com/BradyFU/Awesome-Multimodal-Large-Language-Models): the latest advances on MLLMs in general.
- [locuslab/open-unlearning](https://github.com/locuslab/open-unlearning): a unified framework for LLM unlearning methods and benchmarks.

## Contributing

Know a paper that belongs here? Please open a pull request or an issue. Entry format and inclusion criteria are in [CONTRIBUTING.md](CONTRIBUTING.md).

## Citation

If you find this list useful, please consider starring the repo and citing it:

```bibtex
@misc{huang2026awesomemllmunlearning,
  title        = {Awesome MLLM Unlearning: A Curated List of Machine Unlearning for Multimodal Large Language Models},
  author       = {Huang, Chih-Chuan},
  year         = {2026},
  howpublished = {\url{https://github.com/HuangMason320/awesome-mllm-unlearning}}
}
```

GitHub's **Cite this repository** button (from [CITATION.cff](CITATION.cff)) gives the same reference in APA and BibTeX.

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=HuangMason320/awesome-mllm-unlearning&type=Date)](https://star-history.com/#HuangMason320/awesome-mllm-unlearning&Date)
