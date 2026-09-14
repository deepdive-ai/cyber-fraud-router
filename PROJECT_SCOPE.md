# Relationship to the Week 5 project

This is a custom adaptation of the [Week 5 project handout](https://docs.google.com/document/d/1VwWWJtH0atdUGQJpHFXKLL3WeIALGpve-kdEVujHbqU/edit). It applies the idea of fine-tuning a model for routing to synthetic cyber-fraud complaints.

| Handout topic | Implementation in this project |
|---|---|
| Support-ticket dataset | 600 synthetic cyber-fraud complaints; around 100 cases manually reviewed before fine-tuning. |
| Qwen3 1.7B Base model | Llama 3.1 8B Instruct. |
| LLaMA Factory / LLaMA Board training | Nebius Token Factory LoRA training. |
| 80/20 train/validation split | Separate 420 training, 90 validation, and 90 test cases. |
| Review training loss | Successful three-epoch job; selected checkpoint validation loss 2.3487701, recorded in the evaluation report and checkpoint metadata. |
| Merge adapter and smoke-test | Loaded the adapter separately with PEFT; no merge was performed. Saved recruiter example produced C as expected. The tutorial's five-example smoke test is not claimed. |
| Evaluate and compare | Base and fine-tuned predictions, per-class metrics, confusion matrices and error analysis. Baseline response-format problems are documented. |
| Faster and cheaper routing | Not established by a controlled latency or cost benchmark. |
| Custom-project submission | Public GitHub repository with assets and screenshots. The handout also requests a Loom video; a video link has not been supplied for inclusion in this repository. |

The results demonstrate this custom workflow, not completion of every platform-specific step in the original tutorial.
