# Cyber-Fraud Complaint Router — Evaluation Report

## Result
Fine-tuned Llama-3.1-8B-Instruct with LoRA classified **82/90 synthetic held-out complaints correctly (91.11%)**, macro-F1 **0.906074**. All 90 responses followed the required single-letter A–F format.

## Evaluation protocol
600 synthetic complaints, six balanced categories. Training: 420; validation: 90; test: 90. The user reviewed the pilot and selected review cases; do not describe the entire dataset as independently human-validated. Baseline and fine-tuned runs used the same system prompt, saved chat template, test inputs, deterministic generation, and 4-bit NF4 base weights on a Colab T4. Baseline used the same model with the adapter disabled.

## Baseline scoring caveat
The first experiment allowed 8 output tokens and required an exact letter. All baseline outputs failed that format; its 0% score is not a measure of pure category recognition. A second experiment allowed 64 tokens and accepted an initial category letter: base accuracy 12.22%, macro-F1 0.083333, 61 parser-invalid responses; fine-tuned accuracy 91.11%, macro-F1 0.906074, no invalid responses. Baseline single-letter compliance remained 0/90.

A post-hoc audit of saved 64-token outputs extracted explicitly declared categories even after introductory prose: **64/90 (71.11%)** baseline responses matched the dataset labels. CF335 and CF393 contain conflicting category statements and were conservatively left unresolved/count as incorrect. This audit is exploratory and was devised after seeing test outputs; it is separate from the original automated evaluation, not a preregistered benchmark. See results/base_response_audit.csv for every decision. Do not headline a 0% or 12.22% to 91.11% classification improvement without this qualification.

## Training evidence
Nebius job ftjob-1018422a3bb5485ab7bc506307c4c9b2 succeeded. Three epochs, LoRA rank 8, alpha 8, dropout 0; selected epoch 3 had validation loss 2.3487701. 448 adapter tensors loaded with no missing/unexpected adapter keys. Training loss is not accuracy. Downloaded checkpoint metadata reports six optimizer steps; improvements need broader validation.

## Fine-tuned errors
| ID | Expected | Predicted | Complaint |
|---|---|---|---|
| CF215 | investment_scam | job_task_scam | I joined a livestock return scheme online. The farm in its videos confirmed that their footage had been copied without permission. |
| CF466 | credential_phishing | shopping_scam | The supposed shopping app support worker wanted my banking OTP to check a refund; there was no actual purchase or refund request. |
| CF564 | human_review | job_task_scam | The job recruiter has not responded for a week after my interview; I did not pay anything or share login details. |
| CF568 | human_review | shopping_scam | My child made an in-app purchase on my phone and I want to request a refund. |
| CF571 | human_review | credential_phishing | An app asks me to log in after updating; I have no indication it is a fake app or page. |
| CF576 | human_review | shopping_scam | A fake insurance agent collected a premium using a forged policy and disappeared. It was not sold as an investment. |
| CF585 | human_review | shopping_scam | I was asked to pay for a prize I supposedly won, but I never entered a competition. |
| CF589 | human_review | authority_impersonation | I received a genuine-looking fine notice but have not verified it. It does not demand an unusual private transfer or threaten remote custody. |

Six of eight errors are human_review cases assigned a specific scam label. Human-review recall is 9/15 (60%). Authority, job/task, and shopping recall are each 15/15; investment and phishing recall are each 14/15. The system therefore needs particular improvement on ordinary service issues and out-of-scope complaints.

## Limitations
Small, balanced, AI-authored English synthetic test set; no real complaint validation. This is a routing prototype, not proof of fraud or a system for automatically accusing people. Confidence calibration and confidence-based routing were not evaluated. The human_review class is a trained category, not a confidence threshold. No controlled latency/cost benchmark was performed. Test results have now been inspected; further tuning would require a fresh test set for an unbiased final estimate.
