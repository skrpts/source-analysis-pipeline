---
type: workflow
id: source-analysis-pipeline
title: Source Analysis Pipeline
description: "Extract citations, assess methodology, compare arguments, and summarise sources"
tags: [Tested]
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
  - target: anthropic-claude
    type: runs_on
  - target: openai-gpt4
    type: runs_on
metadata:
  estimated_duration: "15-30 minutes"
  trigger: manual
---

## Overview

This workflow conducts a thorough analysis of one or more academic sources. It extracts and formats citations, assesses the methodology, maps the argumentative structure, and produces a comprehensive summary. The outputs can feed into a literature review or inform a research proposal.

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

Invoke the **source-summarisation** skill via the **summarise-source** prompt to produce a comprehensive summary incorporating the citation, methodology, and argument analyses.

**Output:** Complete source summary ready for use in a literature review or research proposal.

## Error Handling

- If a source lacks a clear methodology section (e.g., opinion pieces, editorials), skip Stage 2 and note the source type
- If citations are in an unfamiliar format, extract what is available and flag for manual completion
- If the argument structure is unclear (e.g., primarily descriptive text), note this in the argument map
- If multiple sources are provided, process each independently then produce a comparative summary
