# Suggested 3-minute Loom demo

**0:00–0:25 — Problem.** “Cyber-fraud complaints arrive as unstructured text. My prototype routes an allegation into five scam categories or human review. It does not verify that a crime occurred.”

**0:25–0:50 — Data.** Show label_mapping.json and a training example. “I created 600 balanced synthetic complaints, reviewed pilot and selected cases, and split them into 420 training, 90 validation, and 90 held-out test complaints. Reasons are review metadata; the model learns to return one category letter.”

**0:50–1:15 — Fine-tuning.** Show the successful Nebius job and checkpoints screenshot. “I fine-tuned Llama 3.1 8B Instruct with LoRA for three epochs. I downloaded epoch 3, loaded the base model in 4-bit on a Colab T4, and attached all 448 adapter tensors.”

**1:15–1:45 — Live example.** Run the already working complaint cell about a fake recruiter. Show C. “C means job/task scam. The interface can translate that letter to a review queue.”

**1:45–2:25 — Evaluation.** Show the summary and EVALUATION_REPORT.md. “On the 90 synthetic test complaints, the fine-tuned model got 82 correct: 91.1% accuracy and 0.906 macro-F1. It returned a single letter every time. The baseline wrote prose, which our initial parser rejected. A separate post-hoc audit recovered 64 correct baseline classifications out of 90, with two conflicting answers counted incorrect. I separate this audit from the automated format scores.”

**2:25–3:00 — Limitations.** Show the error table. “Six of the eight mistakes were cases that should have gone to human review. Human-review recall was only 60%. Next I would improve those boundary cases using training and validation data, then evaluate on a fresh, independently reviewed test set and real-world complaints. This is a classroom prototype, not production fraud adjudication.”
