# Personal Chat Assistant

Fine-tuned GPT-2 on everyday conversation, plus an editable "style profile" prompt that steers tone without retraining.

## Problem Statement

A generic chatbot doesn't sound like you — it replies the same flat way to everyone. Personalization systems fix this by fine-tuning on someone's own chat style. This project fine-tunes GPT-2 on everyday conversation data and adds a simple style-profile trick to steer tone at inference time.

## Dataset

[DailyDialog](https://huggingface.co/datasets/li2017dailydialog/daily_dialog) — 50,000 conversational context→response pairs, flattened from ~11,000 multi-turn dialogues. A free stand-in for personal chat history — swap in your own exported chat log for a genuinely personalized version.

## What It Builds

- A GPT-2 model fine-tuned on everyday chat message pairs
- A style-profile prompt trick that changes reply tone without retraining
- A perplexity evaluation to measure how well the model adapted
- A saved, reloadable chat model

## Results (from an actual training run)

| Metric | Value |
|---|---|
| Training pairs | 50,000 |
| Training epochs | 3 |
| Final training loss | 2.40 |
| **Perplexity on held-out chat text** | **11.57** |
| Training time | ~53 min on a free Colab T4 |

A perplexity of 11.57 is a solid, believable number — well below plain GPT-2's typical 20-35+ perplexity on out-of-domain text, showing the model genuinely adapted to casual conversational style.

**Example generated reply:**
> *"I'm just getting started. Let's just say you've got a lot of things to learn. We should just get together and have fun. Let's go"*

## Tech Stack

Python · HuggingFace Transformers (GPT-2) · Google Colab (free T4 GPU)

## How to Run

1. Open the notebook in Google Colab
2. Runtime → Change runtime type → T4 GPU
3. Run all cells top to bottom
4. Enter a free [Groq API key](https://console.groq.com/keys) when prompted (used for an optional AI helper, not required for the core training pipeline)

## Repo Structure

```
personal-chat-assistant/
├── Personal_Chat_Assistant.ipynb
└── README.md
```

## Disclaimer

Built as a learning/portfolio project. Replies occasionally repeat phrasing — a known GPT-2-small limitation at this training scale.

---
By Akshat Kesharwani
