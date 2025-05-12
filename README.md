# SAS Code Generation with Fine-Tuned LLM

This project explores the use of large language models (LLMs) to generate valid, executable SAS code based on natural language healthcare specifications. Built as part of a graduate NLP course at UMBC, the goal was to shorten the turnaround time for coding requests in healthcare analytics — transforming what typically takes days or weeks into seconds.

While the final model is limited by a small training set, this repo serves as an early prototype for natural language–to–SAS pipelines in structured healthcare workflows.

---

## 🔍 Problem Statement

Healthcare analysts frequently receive vague or high-level requests from policy or clinical stakeholders ("Show all members eligible for Medicaid in 2018 with more than one hospitalization"). These need to be manually translated into complex SAS code — a time-intensive process.

This project fine-tunes an open LLM on real analyst-authored prompt–code pairs to see how far we can automate the process.

---

## 🛠️ Model & Tools

* **Model:** `unsloth/Llama-3.2-1B-bnb-4bit`
* **Trainer:** `SFTTrainer` from 🤗 `transformers` + `unsloth`
* **Fine-Tuning Method:** LoRA (parameter-efficient fine-tuning via PEFT)
* **Data Format:** JSON with `Context` (prompt) → `Response` (SAS code)
* **Evaluation:** Prompt-to-code fidelity + manual review
* **Logging:** Weights & Biases (wandb)

---

## 🧠 Dataset

* Fully human-written prompts and SAS code completions (\~150 examples)
* All examples reflect realistic healthcare data manipulation, eligibility filtering, and macro usage.
* NOTE: Dataset is not included in this repo due to source permissions.

---

## 📊 Results

While the model produced partially correct completions, accuracy was limited by dataset size and complexity of SAS macro structures. The experiment highlights the need for:

* More robust data variety (e.g., synthetic augmentation)
* Targeted prompt engineering
* Larger-scale training or instruction tuning

---

## 📁 Repo Structure

```
sas-finetune-llm/
├── notebooks/
│   └── Final_Model.ipynb        # Colab notebook for training & evaluation
├── data/
│   └── sample_prompt.json       # Optional example (not included here)
├── thumbnail.png                # For GitHub/LinkedIn preview (optional)
└── README.md
```

---

## 📌 Next Steps

* Add synthetic training data to improve coverage
* Evaluate CodeLlama or Codestral on same task
* Build RAG pipeline around prompt templates + real-time code validation

---

## 📇 Credits

Capstone project for DATA690: Large Language Models
University of Maryland, Baltimore County (UMBC) – MPS in Data Science
Author: Craig Drohan
