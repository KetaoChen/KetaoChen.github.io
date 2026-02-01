---
layout: post
title: "Notes: Karpathy's Intro to Large Language Models"
date: 2026-02-01
categories: [llm-basics]
tags: [karpathy, llm, notes]
---

Notes from Andrej Karpathy's [Intro to Large Language Models](https://www.youtube.com/watch?v=zjkBMFhNj_g) (Nov 2023, 1hr).

## Key Takeaways

### LLM = Two Files
- **Parameters file** — neural network weights (Llama 2 70B = 140GB)
- **Run file** — ~500 lines of C to run inference
- Complexity is in training, not inference

### Training = Lossy Compression of the Internet
- 10TB internet text → 140GB parameters ≈ 100x compression
- Next word prediction forces the network to learn world knowledge
- Knowledge storage is "weird" — knows Tom Cruise's mother, but not the reverse (reversal curse)

### Two-Stage Training
1. **Pre-training** — massive internet data, produces base model (document generator)
2. **Fine-tuning** — human-labeled Q&A pairs (~100K), produces assistant model
3. **RLHF (optional)** — human comparisons for further refinement

### Scaling Laws
- Performance = f(parameters N, data D) — predictable, monotonically increasing, no saturation
- This drives the GPU arms race: bigger model + more data = guaranteed better results

### LLM as Operating System
The most powerful analogy in the talk:

| Traditional OS | LLM OS |
|---------------|--------|
| Disk/Network | Browser/file retrieval |
| RAM | Context window |
| CPU process | LLM kernel process |
| Multithreading | Tool use |
| User/kernel space | Prompt hierarchy |
| Windows/Mac vs Linux | GPT/Claude vs Llama |

### Tool Use
Modern LLMs call tools: browser search, Python execution, image generation. This is exactly what protocols like MCP are standardizing.

### Security Challenges
- **Jailbreaks** — role-play bypasses, base64 encoding, adversarial suffixes
- **Prompt injection** — hidden instructions in images/webpages/documents
- **Data poisoning** — trigger phrases embedded in training data

## What's Changed Since 2023

- **System 2 thinking** — now reality (Claude thinking mode, o1/o3 reasoning)
- **Scaling** — training runs now in billions of dollars
- **Open source** — Llama 3, Mistral, DeepSeek have narrowed the gap significantly
