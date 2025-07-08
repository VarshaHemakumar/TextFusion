#  TextFusion: Abstractive Summarization of Legislation Using BART

**TextFusion** is a lightweight yet powerful abstractive summarizer built using the pre-trained `facebook/bart-base` model. This project fine-tunes BART on the **Billsum** dataset to generate human-like summaries for U.S. congressional and state legislative texts.

---

##  Project Highlights

-  Fine-tunes `facebook/bart-base` on legal government bills  
-  Custom tokenization, cleaning, and preprocessing  
-  Evaluates with ROUGE, BLEU, and BERTScore  
-  Visual analysis of training loss and evaluation metrics  
-  Uses custom training loop with dynamic evaluation via `generate()`

---

##  Dataset

- **Source**: [Billsum](https://huggingface.co/datasets/FiscalNote/billsum)  
- **Type**: Long-form U.S. bills and their summaries  
- **Preprocessing**:  
  - Tokenized using `BartTokenizer`  
  - Input max length: 1024 tokens  
  - Target summary max length: 256 tokens  
  - Text lowercasing, punctuation stripping  

---

##  Model Architecture

| Component        | Description                         |
|------------------|-------------------------------------|
| Pretrained Model | `facebook/bart-base`                |
| Fine-Tuning Task | Sequence-to-sequence summarization  |
| Objective        | Maximize summary generation quality |
| Loss Function    | CrossEntropyLoss with label smoothing |
| Optimizer        | AdamW                               |
| Evaluation       | `generate()` with beam search       |

---

##  Visual Results

This section presents training behavior and evaluation results for both the base and optimized BART summarization models fine-tuned on the Billsum dataset.

---

###  Base Model: Training vs Validation Loss
<img width="590" alt="Base Loss Curve" src="https://github.com/user-attachments/assets/4aa3ad8e-9bbd-4c9a-b66e-2d17b29380fb" />

---

###  Base Model: Evaluation Metrics
<img width="339" alt="Base Results" src="https://github.com/user-attachments/assets/a74d1f45-e29c-4391-96c8-2623946bd612" />

---

###  Best Model: Training vs Validation Loss (Post Tuning)
<img width="514" alt="Best Loss Curve" src="https://github.com/user-attachments/assets/928bd386-590d-4bfb-9a65-5094cd765ef1" />

---

###  Best Model: ROUGE-1 Score Over Epochs
<img width="529" alt="ROUGE-1 Over Epochs" src="https://github.com/user-attachments/assets/7513105a-2f51-4ece-a2ec-72532c00647a" />

---

###  Best Model: Final Evaluation Metrics
<img width="360" alt="Best Model Results" src="https://github.com/user-attachments/assets/bf530294-b317-4d20-8b37-4aa9edef90a0" />


---

##  Evaluation Metrics

| Metric      | Value (Approx.) |
|-------------|------------------|
| ROUGE-1     | > 40             |
| ROUGE-2     | > 18             |
| ROUGE-L     | > 28             |
| BLEU        | > 12             |
| BERTScore   | > 75             |

> These scores align with benchmark targets for the Billsum dataset.

---



##  Reflections

- BART’s encoder-decoder setup is well-suited for long-form summarization  
- The `generate()` method allows rich decoding strategies like beam search  
- ROUGE and BLEU offer surface-level checks, but BERTScore captures semantic quality  
- Managing sequence length and batch size is critical for training stability  

---
