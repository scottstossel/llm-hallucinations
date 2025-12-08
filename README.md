# Do Hallucination Detectors Understand Factuality?
A Robustness Study with Paraphrased Summaries

This repository contains the code, data processing steps, models, and analysis used to evaluate the robustness of hallucination-detection models under paraphrasing. Our goal is to test whether widely used detectors truly understand factual consistency or whether their strong bechmark performance is driven by superficial linguistic cues.

Paper: Do Hallucination Detectors Understand Factuality? A Robustness Study with Paraphrased Summaries
Authors: Scott Stossel, Jing Tan
UC Berkeley School of Information (MIDS)

## Motivation

Hallucination detectors often report high accuracy on standard benchmarks, but it is unclear whether these scores reflect genuine semantic understanding. Many detectors may implicitly rely on lexical patterns or dataset-specific writing styles. This project evaluates whether common architectures (BERT, RoBERTa, ELECTRA, FLAN-T5, DeBERTa) remain reliable when summaries are paraphrased—preserving factual meaning while disrupting surface form.

Our central question:
Do hallucination detectors understand factuality, or do they merely recognize familiar phrasing?

## Goals

- Build a reproducible evaluation pipeline for measuring hallucination-detection robustness.
- Construct a paraphrased out-of-distribution (OOD) test set that preserves factual truth.
- Fine-tune and evaluate multiple model families using accuracy, F1, and calibration.
- Analyze failure modes using confusion matrices and probability calibration (ECE).
- Provide scripts and notebooks to reproduce all results in the paper.

## Data & Methods

- Dataset: 
    - HaluEval (10,000 article–summary pairs labeled for factual consistency)
    - https://huggingface.co/datasets/pminervini/HaluEval
- Paraphrasing:
    - T5-based paraphrase model (paws-style)
        - https://huggingface.co/Vamsi/T5_Paraphrase_Paws
    - Verified with roberta-large-mnli and LLM-as-judge
    - Contradicting or fact-removing paraphrases removed (Appendix A2)
- Models evaluated:
    - BERT-base
    - RoBERTa-base
    - ELECTRA-base
    - FLAN-T5-base
    - DeBERTa-base
- Metrics: 
    - Accuracy, Precision, Recall, F1
    - Expected Calibration Error (ECE)
    - Confusion matrices for ID vs OOD data
- Training:
    - AdamW, LR = 5e-5, batch size = 16, 2 epochs
    - HuggingFace Transformers training pipeline

## Repository layout

- `Data_Retrieval.ipynb` - retrieve + preprocess the HaluEval dataset
- `Paraphrase_Verification.ipynb` - validate paraphrased summaries
- `experiments/` — fine-tuning, evaluation, and visualizations
- `HallucinationsInLLMs.pdf` - final paper
- `README.md` — this file.

## Quick start

1. Run Data_Retrieval.ipynb to download, clean, and split the HaluEval dataset.
2. Run Paraphrase_Verification.ipynb to generate and filter paraphrased summaries.
3. Use the notebooks in experiments/ to fine-tune models and reproduce all results.
