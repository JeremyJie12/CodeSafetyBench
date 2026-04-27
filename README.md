# CodeSafetyBench: Benchmarking and Enhancing Code Generation Safety in LLMs

CodeSafetyBench is a benchmark for evaluating and improving ethical safety in large language model (LLM) code generation.

This repository currently includes the released dataset files derived from the published study, covering three domains:

- education
- legal
- healthcare

## Dataset Summary

- Training set: 900 samples (`300` per domain)
- Evaluation set: 150 samples (`50` per domain)

## Repository Structure

```text
CodeSafetyBench-main/
├── dataset/
│   ├── train/
│   │   └── train_from_xlsx.json
│   └── eval/
│       ├── education_from_xlsx.json
│       ├── legal_from_xlsx.json
│       └── healthcare_from_xlsx.json
└── README.md
```

## Data Format

### Training JSON (`dataset/train/train_from_xlsx.json`)

Each item contains:

- `domain`: one of `education`, `legal`, `healthcare`
- `split`: `train`
- `case_id`: case identifier
- `category`: risk category label
- `harmful_request`: unsafe prompt/request
- `harmful_response`: unsafe code-style response
- `refusal_response`: direct refusal response
- `educational_feedback`: refusal with ethical explanation
- `metadata`: metadata object
- `risk_warning`: explicit risk reminder text

Example schema:

```json
{
  "domain": "education",
  "split": "train",
  "case_id": "E001_auto",
  "category": "discrimination",
  "harmful_request": "...",
  "harmful_response": "...",
  "refusal_response": "...",
  "educational_feedback": "...",
  "metadata": {
    "synthetic": true,
    "pii_present": false,
    "compliance_tags": []
  },
  "risk_warning": "..."
}
```

### Evaluation JSON (`dataset/eval/*.json`)

Each item contains:

- `domain`
- `split` (set to `test`)
- `case_id`
- `harmful_request`

Example schema:

```json
{
  "domain": "healthcare",
  "split": "test",
  "case_id": "H_test_01",
  "harmful_request": "..."
}
```

## Quick Start

### Load with Python

```python
import json
from pathlib import Path

root = Path("dataset")

train_data = json.loads((root / "train" / "train_from_xlsx.json").read_text(encoding="utf-8"))

eval_education = json.loads((root / "eval" / "education_from_xlsx.json").read_text(encoding="utf-8"))
eval_legal = json.loads((root / "eval" / "legal_from_xlsx.json").read_text(encoding="utf-8"))
eval_healthcare = json.loads((root / "eval" / "healthcare_from_xlsx.json").read_text(encoding="utf-8"))
```

## Intended Use

- Benchmarking LLM safety on harmful coding requests
- Training/refining refusal strategies and safer response behavior
- Comparing direct refusal vs educational ethical feedback

## Ethical Notice

This dataset contains harmful prompts and unsafe code-oriented outputs for safety research purposes only. Do not deploy unsafe patterns in real systems.

## Citation

If you use this dataset, please cite:

```bibtex
@article{he2026codesafetybench,
  title={CodeSafetyBench evaluating and improving ethical safety in large language model code generation},
  author={He, Jie and Qin, Si and Zou, Huiru and Jing, Fengshi and Liu, Wenjian and Li, Changjin and Wang, Qiting and Hu, Zihan and Song, Kai and Xu, Zhongzhi and others},
  journal={Iscience},
  volume={29},
  number={4},
  year={2026},
  publisher={Elsevier}
}
```

