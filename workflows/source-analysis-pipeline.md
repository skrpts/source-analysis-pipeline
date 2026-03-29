---
type: workflow
id: source-analysis-pipeline
title: Source Analysis Pipeline
description: "Extract citations, assess methodology, compare arguments, and summarise sources"
tags: [Tested, Automation, Citations, Research]
connections:
  - target: citation-extraction
    type: uses
  - target: methodology-assessment
    type: uses
  - target: argument-mapping
    type: uses
  - target: source-summarisation
    type: uses
  - target: extract-citations
    type: uses
  - target: assess-methodology
    type: uses
  - target: map-argument
    type: uses
  - target: summarise-source
    type: uses
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "15-30 minutes"
  trigger: manual
---

## Overview

This workflow conducts a thorough analysis of one or more academic sources. It extracts and formats citations, assesses the methodology, maps the argumentative structure, and produces a structured summary. The outputs can feed into a literature review or inform a research proposal.

## Pipeline Stages

### Stage 1: Citation Extraction

**Input:** Source text(s), target citation style

Invoke the **citation-extraction** skill via the **extract-citations** prompt to identify all citations in the source and reformat them in the target style. Flag incomplete or suspicious citations for verification.

**Output:** Formatted reference list with quality flags.

### Stage 2: Methodology Assessment

**Input:** Source text(s), research question context

Invoke the **methodology-assessment** skill via the **assess-methodology** prompt to evaluate the research methodology. Rate the overall quality and identify specific strengths and weaknesses.

**Output:** Methodology assessment with quality rating.

### Stage 3: Argument Mapping

**Input:** Source text(s)

Invoke the **argument-mapping** skill via the **map-argument** prompt to identify and structure the argumentative components: claims, evidence, assumptions, counter-arguments, and rebuttals.

**Output:** Structured argument map with strength assessment.

### Stage 4: Source Summarisation

**Input:** Source text(s), all outputs from Stages 1-3

Invoke the **source-summarisation** skill via the **summarise-source** prompt to produce a complete summary incorporating the citation, methodology, and argument analyses.

**Output:** Complete source summary ready for use in a literature review or research proposal.

## Error Handling

- If a source lacks a clear methodology section (e.g., opinion pieces, editorials), skip Stage 2 and note the source type
- If citations are in an unfamiliar format, extract what is available and flag for manual completion
- If the argument structure is unclear (e.g., primarily descriptive text), note this in the argument map
- If multiple sources are provided, process each independently then produce a comparative summary

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.source_text}}` | Yes | The academic source text to analyse | `Paste the full text of the article, paper, or chapter here` |
| `{{input.target_citation_style}}` | Yes | Target citation style for formatted references | `APA 7th edition` |
| `{{input.research_question_context}}` | Yes | Your research question, to assess relevance against | `How does social media usage affect adolescent wellbeing?` |
| `{{input.field_specific_standards}}` | No | Field-specific methodological standards for assessment | `CONSORT for RCTs, APA reporting standards` |

## Outputs

| Name | Description |
|------|-------------|
| Formatted reference list | Formatted reference list with quality flags |
| Methodology assessment | Methodology assessment with quality rating |
| Structured argument map | Structured argument map with strength assessment |
| Complete source summary ready for use in a literature review or research proposal | Complete source summary ready for use in a literature review or research proposal |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- Most stages work with any capable model; stronger models usually improve synthesis, judgement, and writing quality.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
Source Text: "Paste the relevant brief, notes, source material, or dataset here."
Target Citation Style: "Paste the relevant brief, notes, source material, or dataset here."
Research Question Context: "Paste a short brief describing the goal, audience, and constraints."
```

