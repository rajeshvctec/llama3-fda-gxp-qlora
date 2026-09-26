# Llama-3-8B FDA/GxP Compliance — QLoRA Fine-tune

Fine-tuned Llama-3-8B on 91 synthetic FDA/GxP compliance Q&A pairs using QLoRA (via Unsloth), evaluated with LLM-as-judge on a held-out test set.

# Results
| | Score (1-5, GPT-4o-mini judge) |
|---|---|
| Base model | 2.93 |
| Fine-tuned | 3.64 |

Base model answers were frequently generic, repetitive, or empty on FDA-specific questions. Fine-tuned answers were concise, on-topic, and used correct regulatory terminology consistently.

# Method
- Base: `unsloth/llama-3-8b-bnb-4bit`
- QLoRA: r=16, alpha=16, target modules = attention + MLP projections
- 60 training steps, batch size 2, grad accumulation 4
- Data: synthetic Q&A generated from 21 CFR Part 11 / GxP source text (GPT-4o-mini), 77 train / 14 test split

# Model
Adapter weights: https://huggingface.co/rajeshvctec/llama3-8b-fda-gxp-qlora

# Notebook
See `[notebook filename].ipynb` in this repo for full training code.
