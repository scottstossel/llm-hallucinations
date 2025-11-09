# LLM Hallucinations

This project investigates hallucinations produced by large language models (LLMs). We analyze when and why LLMs produce incorrect or unsupported statements, measure hallucination rates across tasks, and explore methods to reduce them.

## Motivation

Hallucinations are a major barrier to reliable deployment of LLMs in real-world applications. This project aims to (1) characterize common hallucination types, (2) quantify their frequency under different prompting and retrieval settings, and (3) evaluate mitigation strategies.

## Goals

- Build a reproducible evaluation suite for measuring hallucinations.
- Curate datasets and prompts that surface hallucination behavior.
- Compare mitigation techniques: retrieval augmentation, prompt engineering, constraint-based decoding, and post-hoc verification.
- Provide scripts, notebooks, and visualizations to reproduce and analyze experiments.

## Data & Methods

- Datasets: curated question sets, fact-check pairs, and domain prompts designed to elicit hallucinations. HaluEval dataset: https://huggingface.co/datasets/pminervini/HaluEval
- Metrics: hallucination rate, factual-claim precision/recall, and human annotation protocols for qualitative analysis.
- Methods: retrieval-augmented generation, grounding with external knowledge, chain-of-thought prompting, and model ensembling. Baseline model: https://huggingface.co/manueldeprada/FactCC


## Repository layout

- `notebooks/` — interactive analyses and visualizations.
- `README.md` — this file.

## Quick start

1. Baseline model and dataset can be obtained by following Hallucination_Baseline in the notebooks folder.