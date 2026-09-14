# Cyber-Fraud Complaint Router

Llama-3.1-8B-Instruct fine-tuned with LoRA on Nebius; evaluated on Google Colab T4 with 4-bit NF4 inference.

**91.11% accuracy, 0.906 macro-F1, 100% single-letter compliance on 90 held-out synthetic complaints.** Read EVALUATION_REPORT.md for the baseline parser limitation, exploratory response audit, and human-review failures.

## Included
- Dataset splits and conversational JSONL training inputs
- Original Nebius adapter and tokenizer files
- Raw predictions, confusion matrices, and both original experiment summaries
- Evaluation report and suggested demo narration

## Add before submission
- Export your executed Colab notebook using File → Download → Download .ipynb and add it here. The earlier Qwen draft does not reproduce this Llama run.
- Add your Loom video URL below.
- Include a screenshot of the successful training job or notebook evaluation.

Demo video: ADD YOUR LOOM URL
Executed notebook: ADD YOUR DOWNLOADED NOTEBOOK

## Running
Use the executed notebook for the actual installation, authentication, base model loading, adapter key conversion, inference, and evaluation steps. Access to meta-llama/Llama-3.1-8B-Instruct is required through your own Hugging Face account. Do not include access tokens. The downloaded Nebius adapter keys require the base_model.model. prefix when loading through PEFT; the executed notebook contains that conversion and a missing-key check.

## Limitations
Synthetic English data and small test set. Predictions describe allegations and route for review; they do not establish criminal conduct. No calibrated confidence estimates. This prototype requires human oversight.

Built with Llama. Base model use and redistribution are subject to the Llama 3.1 Community License: https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct/blob/main/LICENSE
