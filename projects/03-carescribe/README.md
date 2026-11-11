# Project 3: CareScribe (Weeks 9–11)

**Brief:** Doctors spend hours writing patient summaries. Fine-tune an open LLM to draft discharge-style summaries in clinical style.

**Data:** public, already de-identified transcriptions such as MTSamples. Run your own de-identification pass on top anyway. **Never use real patient data.**

## Deliverables
- [ ] Generation-parameter notebook: temperature, top-p, penalties, structured JSON output (W9)
- [ ] `data/curate.py`: cleaning, de-identification (regex or Presidio), train/val/test split, and a data card (W10)
- [ ] QLoRA fine-tune of a 1–3B instruct model (Colab/Kaggle), with the config and training logs committed (W10)
- [ ] `eval/rubric.md`, a clinician rubric, scored base vs. fine-tuned on 30+ held-out notes (W11)
- [ ] Adapter on the Hugging Face Hub, plus `RESULTS.md` (W11)

## Done when
The fine-tuned model beats the base model on the rubric, not just on loss, and `RESULTS.md` shows 3 good and 3 bad examples honestly.
