---
layout: ../../layouts/CaseStudy.astro
title: Evaluating retrieval in efficient language models
category: Independent MS capstone · UCLA
summary: A literature survey and controlled experimental study of how public language-model checkpoints retrieve exact information under increasing context length and distractor pressure.
role: Sole implementation and report author
period: 2026
team: Faculty-advised individual project
tools: [Python, GPU experiments, Synthetic datasets, Exact-match evaluation, Likelihood scoring, Mamba, BASED]
evidence:
  - label: Source code and experiment setup
    url: https://github.com/jehfoori/Efficient-LLMs-Capstone
  - label: Full capstone report
    url: https://github.com/jehfoori/Efficient-LLMs-Capstone/blob/main/report/main.pdf
note: Results below are from the capstone report. They describe the tested checkpoints and evaluation settings, not universal rankings of model architectures.
---

## From a research question to an experiment

My advising professor proposed the topic. I read the relevant papers, planned the experiments, designed and implemented the evaluation code, arranged and funded GPU compute, and wrote the final report.

The study examined a tradeoff in efficient language models: reducing the cost of processing context may affect how precisely a model can recover a particular fact among similar records. I used synthetic key-value retrieval tasks to make that behavior measurable.

## A controlled evaluation pipeline

I generated deterministic datasets containing a target key-value record and optional distractor records. Models received the same task format, and I scored whether the first generated number matched the requested value. I also categorized failures: selecting a distractor, producing a value absent from the document, or generating no number.

The first experiment compared six HazyResearch checkpoints across eight context lengths, with and without twenty distractors: 2,880 model generations. A second experiment compared three official Mamba-family checkpoints at 2,048, 4,096, and 8,192 tokens, with 0, 5, or 10 distractors: 810 generations. Each setting used 30 examples.

## Investigating an unexpected result

A BASED checkpoint showed an unusual accuracy collapse at an intermediate context length, followed by recovery at longer lengths. I investigated whether the generation implementation was affecting the result.

| Diagnostic at 1,792 tokens | Correct answers |
| --- | --- |
| Cached generation, BASED 360M in fp32 | 2 / 20 |
| Recompute decoding, same setting | 20 / 20 |

The final BASED runs used recompute decoding. That decision also changed what I could responsibly compare: I reported retrieval accuracy and failure types, without treating those runs as a fair speed or memory comparison against cached decoding in other models.

## Separating retrieval from answer formatting

I added a diagnostic that ranked candidate answers by their continuation likelihood under the same completion prompt. This helped distinguish failures to generate the expected answer format from failures to identify the correct record.

Across the tested settings, distractors exposed weaknesses that a simple single-record task often hid. Mamba-2 was the strongest of the three official Mamba-family checkpoints in the second experiment, but the report treats that as a bounded observation about this evaluation.

## What the work demonstrates

The project involved translating a research topic into executable experiments, maintaining comparable inputs and scoring, and investigating anomalies before interpreting results. The repository includes the evaluation implementation, tests, experiment scripts, figures, and report.
