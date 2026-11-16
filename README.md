# Next-Word Prediction on *A Study in Scarlet*

Comparing four next-word predictors on the same held-out text from Arthur Conan Doyle's *A Study in Scarlet*:

1. **Trigram + backoff** (statistical baseline, trained on the book)
2. **BERT** `bert-base-uncased` (masked LM, zero-shot)
3. **GPT-2** `gpt2` (causal LM, zero-shot)
4. **GPT-2 fine-tuned** on the book

## Method
- Text extracted from the PDF, cleaned (page numbers, headings, drop-caps removed; punctuation and case kept), split into sentences.
- 80/10/10 train/val/test split by chunks of 10 consecutive sentences (no neighbouring-sentence leakage).
- Test set: every word with at least 3 words of context, restricted to words that are a single token in both GPT-2 and BERT, so all models are scored on identical examples.
- Metrics: top-1 / top-5 next-word accuracy; perplexity for GPT-2 before vs. after fine-tuning.
- Fine-tuning: 4 epochs, lr 5e-5, 128-token blocks, best epoch chosen by validation perplexity.

## Results
> Fill these in from the notebook output (`results_accuracy.csv`, `results_accuracy.png`).

| Model | Top-1 | Top-5 |
|---|---|---|
| Trigram + backoff | 13.4% | 33.4% |
| BERT (zero-shot) | 10.5% | 24.1% |
| GPT-2 (zero-shot) | 28.6% | 53.5% |
| GPT-2 (fine-tuned) | 32.4% | 58.5% |

GPT-2 test perplexity: zero-shot 47.78 -> fine-tuned 30.70

## Findings
_(2-4 sentences: which model won, how much fine-tuning helped, what kinds of errors remain — use the error-analysis cell.)_

## Limitations
- Small corpus (~43k words, one author, one novel) — fine-tuning gains are partly style memorisation.
- BERT is not a left-to-right model; `[MASK]`-at-end is a workaround, not its intended use.
- Top-k is over whole-word tokens only; rare multi-token words are excluded from evaluation.

## Run it
Open `NLP_Project_Next_Word_Prediction_v2.ipynb` in Google Colab (GPU runtime), upload `study_in_scarlet.pdf` when asked, run all cells.
