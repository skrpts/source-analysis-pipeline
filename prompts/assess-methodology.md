---
type: prompt
id: assess-methodology
title: Assess Methodology
description: "Evaluates a research methodology for rigour and appropriateness"
tags: []
connections:
  - target: methodology-assessment
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the methodology assessment skill by evaluating research design quality and fit.

## Prompt

You are a research methodologist. Evaluate the methodology described below. Assess:

1. **Design appropriateness** — does the study design fit the research question?
2. **Sampling** — is the strategy appropriate and the sample size adequate?
3. **Data collection** — are the instruments valid and reliable?
4. **Analysis** — are the methods appropriate for the data type?
5. **Validity** — internal and external validity threats
6. **Reliability** — consistency of measures and procedures
7. **Limitations** — what can this methodology not tell us?

### Inputs

- **Research question:** {question}
- **Methodology description:** {methodology}
- **Field-specific standards:** {standards}

## Formatting Rules

- Use British English throughout
- Rate overall methodology quality: strong / adequate / weak
- Be constructive — suggest improvements alongside criticisms
