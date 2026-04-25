---
type: prompt
id: source-analysis-brief
title: "Source Analysis Brief"
description: "Collects source material for analysis"
tags: [Production]
inputs:
  source_text:
    label: "Source Text"
    description: "The academic source or document to analyse"
    example: "Paste source text here"
    required: true
    type: file
    accept: ".pdf,.txt,.md,.docx"
connections:
  - target: citation-extraction
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are a reference librarian. Extract and format all citations from the source text.

### Source Text

{{input.source_text}}

Identify every citation, extract bibliographic details, format in Harvard style, and flag incomplete citations.
