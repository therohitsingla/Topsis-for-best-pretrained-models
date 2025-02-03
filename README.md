# TOPSIS for Conversational Model Selection 🚀

## Overview

This tool uses TOPSIS (Technique for Order Preference by Similarity to Ideal Solution) to rank text generation models (like DialoGPT, OPT, BLOOM) based on customizable criteria such as response quality, speed, and size. Perfect for finding the optimal balance between accuracy and efficiency!

## Features

* Multi-Criteria Ranking: Evaluate models using metrics like ROUGE scores (quality), inference time (speed), and model size (efficiency).

* Customizable Weights: Adjust importance for each metric (e.g., prioritize speed over size).

* Visual Results: Get ranked tables and bar charts for easy comparison.

* Plug-and-Play: Works with any dataset of model metrics. No complex setup!

## Installation

```bash
pip install numpy pandas matplotlib
```

## Usage

Add your model data (example below) and run the script to get rankings.

```python
from topsis import evaluate_models

# Example data: ROUGE-1, Inference Time (s), Model Size (GB)
model_data = [
    {"model": "DialoGPT-medium", "ROUGE-1": 0.45, "Inference Time": 0.67, "Size": 4.2},
    {"model": "OPT-1.3b", "ROUGE-1": 0.50, "Inference Time": 1.03, "Size": 7.5},
    {"model": "BLOOM-560m", "ROUGE-1": 0.48, "Inference Time": 0.78, "Size": 3.1}
]

# Evaluate models (weights: [ROUGE-1, Inference Time, Size], impacts: [+, -, -])
results = evaluate_models(model_data, weights=[0.5, 0.25, 0.25])
print(results)
```

## Evaluation Metrics

| Metric | Goal | Example Value |
|--------|------|---------------|
| ROUGE-1 F1 | Higher ✅ | 0.45 |
| Inference Time | Lower ⏬ | 0.67s |
| Model Size | Lower ⏬ | 4.2GB |

## Sample Output

Ranked Models Table (results.csv):

| Rank | Model | TOPSIS Score |
|------|-------|--------------|
| 1 | DialoGPT-medium | 0.85 |
| 2 | BLOOM-560m | 0.73 |
| 3 | OPT-1.3b | 0.60 |

## Customization

* Adjust Weights: Change `weights=[0.5, 0.25, 0.25]` to prioritize metrics differently.

* Add New Metrics: Include BLEU scores, memory usage, etc., by updating the data and impacts.
