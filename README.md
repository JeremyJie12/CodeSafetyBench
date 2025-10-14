# CodeSafetyBench: Benchmarking and Enhancing Code Generation Safety in LLMs

> A benchmark dataset for evaluating and improving the ethical safety of large language models (LLMs) in code generation — across **healthcare**, **law**, and **education** domains.

---

## Overview

Large language models (LLMs) have revolutionized code generation, yet they also introduce serious **ethical and security risks**.  
Our research reveals that even advanced models such as GPT-4o can produce **harmful code in up to 78.67% of adversarial prompts**.

To address this critical issue, **CodeSafetyBench** provides the first **systematic benchmark** to evaluate and mitigate these risks through a structured dataset and fine-tuning framework.

---

## Key Features

- **1,050 harmful code requests** across three domains:
  -  Healthcare  
  -  Law  
  -  Education
- Each case includes **three response types**:
  1. **Harmful Response** — Unsafe code generated directly from the prompt  
  2. **Refusal Response** — Simple rejection of the harmful request  
  3. **Educational Feedback** — Ethical refusal with detailed explanation and safer alternatives  
- Supports **Supervised Fine-Tuning (SFT)** and **Direct Preference Optimization (DPO)**  
- Enables fine-grained evaluation of LLM safety under adversarial and ethical challenges  

---

## Reproducibility

We currently provide sample data and examples. The complete and detailed dataset will be released upon paper acceptance.

## Dataset Structure

The repository includes an dataset/ directory to help users understand and reproduce our dataset design and evaluation workflow.

```text
CodeSafetyBench/
│
├── dataset/
│   ├── eval/
│   │   ├── healthcare_example.json   # Healthcare domain evaluation set
│   │   ├── law_example.json   # Legal domain evaluation set
│   │   └── education_example.json   # Education domain evaluation set
│   │
│   └── train/
│       └── train_example.json # Training set for model fine-tuning
│
└── README.md

