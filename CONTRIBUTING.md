# Contributing

Thanks for helping keep this list complete and accurate! Pull requests and issues are both welcome.

## What belongs here

A paper fits this list if its main contribution is about **unlearning, forgetting, or knowledge removal** in one of:

- generative multimodal LLMs / large vision-language models (e.g., LLaVA, Qwen-VL, InternVL),
- contrastive vision-language models (e.g., CLIP),
- other multimodal foundation models (audio-language, video-language, vision-language-action).

Out of scope: text-only LLM unlearning, text-to-image diffusion concept erasure, and catastrophic forgetting in continual learning (unless the goal is intentional removal of knowledge).

## How to add a paper

1. Pick the section that fits best:
   - **Surveys**: survey and position papers.
   - **Benchmarks & Datasets**: papers whose main contribution is an evaluation benchmark or dataset.
   - **Unlearning Methods for MLLMs**: new unlearning algorithms for generative MLLMs/LVLMs.
   - **Safety, Hallucination & Spurious Correlations**: unlearning used to remove harmful behavior, hallucinations, or spurious features.
   - **Evaluation, Robustness & Attacks**: analysis of unlearning quality, recovery or relearning attacks, metric studies.
   - **CLIP & Contrastive Vision-Language Models**: unlearning for CLIP-style encoders.
   - **Beyond Vision: Audio, Video & Embodied Models**: audio-language, video-language, and VLA models.
   - **Toolkits & Frameworks**: libraries and unified codebases.
2. Add one table row, keeping the section **newest first** (by first arXiv version):

   ```markdown
   | **[ShortName]** [Full Paper Title](https://arxiv.org/abs/XXXX.XXXXX) | Venue YYYY | YYYY-MM | [![Star](https://img.shields.io/github/stars/OWNER/REPO.svg?style=social&label=Star)](https://github.com/OWNER/REPO) |
   ```

   - **ShortName**: the method or benchmark name, if the paper has one. Omit it if the title already starts with that name.
   - **Title**: use the exact arXiv title, linked to the arXiv abstract page (or the official proceedings page if there is no arXiv version).
   - **Venue**: the published venue (e.g., `NeurIPS 2025`, `ACL 2025 Findings`), or `arXiv` for preprints.
   - **Date**: year and month of the first arXiv version.
   - **Code**: the official repository's star badge, or `-` if no official code is available.
3. Update the paper count in the README's *About* section and in the table of contents.

Please put one paper per row and one topic per pull request. If you are unsure where a paper fits, just open an issue with the arXiv link and we will place it.
