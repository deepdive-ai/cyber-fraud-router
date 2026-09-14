# Cyber-Fraud Complaint Router

Llama-3.1-8B-Instruct fine-tuned with LoRA on Nebius; evaluated on Google Colab T4 with 4-bit NF4 inference.

**91.11% accuracy, 0.906 macro-F1, 100% single-letter compliance on 90 held-out synthetic complaints.** Read EVALUATION_REPORT.md for the baseline parser limitation, exploratory response audit, and human-review failures.

## Try it in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/deepdive-ai/cyber-fraud-router/blob/main/Cyber_Fraud_Demo.ipynb)

Open the demo, select a **T4 GPU**, and run the cells in order. Sign in with your own Hugging Face read token after obtaining Llama access. The notebook downloads the adapter automatically and provides a complaint-entry box. No paid inference API is used; free Colab GPU availability is not guaranteed. Initial model loading can take 10–20 minutes.

The demo uses the original evaluated loading procedure. Its new interface has been statically checked; a fresh end-to-end Colab run has not yet been verified. The executed evaluation notebook below contains the completed model run and results.

## Included
- Dataset splits and conversational JSONL training inputs
- Original Nebius adapter and tokenizer files
- Raw predictions, confusion matrices, and both original experiment summaries
- Evaluation report and suggested demo narration

## Add before submission
- Add your Loom video URL below.

Demo video: ADD YOUR LOOM URL
Executed notebook: [Cyber_Fraud_Fine_Tuning.ipynb](Cyber_Fraud_Fine_Tuning.ipynb)

## Successful notebook runs

Fine-tuned model evaluation on 90 held-out synthetic complaints: **91.11% accuracy, 0.906 macro F1, and zero invalid responses**. Base-model scores in this table are affected by output-format compliance; see [the evaluation report](EVALUATION_REPORT.md) for the exploratory response audit.

![Completed notebook evaluation](screenshots/evaluation-results.png)

The fine-tuned model correctly classifies a fake recruitment complaint as **C — job_task_scam**.

![Successful complaint classification](screenshots/successful-prediction.png)

## Running
Use the executed notebook for the actual installation, authentication, base model loading, adapter key conversion, inference, and evaluation steps. Access to meta-llama/Llama-3.1-8B-Instruct is required through your own Hugging Face account. Do not include access tokens. The downloaded Nebius adapter keys require the base_model.model. prefix when loading through PEFT; the executed notebook contains that conversion and a missing-key check.

## Limitations
Synthetic English data and small test set. Predictions describe allegations and route for review; they do not establish criminal conduct. No calibrated confidence estimates. This prototype requires human oversight.

Built with Llama. Base model use and redistribution are subject to the Llama 3.1 Community License: https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct/blob/main/LICENSE
