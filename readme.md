# Truth-Preserving Resume Rewriter

A constraint-driven Generative AI system that tailors resumes to job descriptions while preserving factual accuracy and preventing unsupported claims.

## Overview

Large Language Models can generate convincing resume content, but they may also introduce skills, experiences, tools, or achievements that are not present in the original resume.

This project addresses that problem by treating the original resume as the **source of truth** and placing deterministic constraints around the LLM generation process.

The system extracts structured facts from a resume, identifies the facts most relevant to a target job description, generates a tailored resume, and validates the generated content against the original facts.

## Key Features

- Resume fact extraction using an LLM
- Immutable fact bank for preserving original information
- Resume–job-description semantic matching
- Sentence Transformer embeddings
- Cosine similarity based relevance scoring
- Constraint-driven LLM resume generation
- Hallucination / unsupported-claim detection
- Entity and token-level validation
- Reject-and-retry generation mechanism
- Change tracking for generated content

## System Workflow

```text
Resume PDF
    ↓
Text Extraction
    ↓
LLM-based Fact Extraction
    ↓
Fact Bank
    ↓
Fact Lock / Integrity Protection
    ↓
Job Description
    ↓
Semantic Matching
    ↓
Relevant Facts + Skill Gaps
    ↓
Constraint-Driven LLM Generation
    ↓
Generated Resume
    ↓
Factual Validation
    ↓
 ┌───────────────┐
 │ Valid Output? │
 └───────┬───────┘
         │
    Yes  │  No
     ↓   │   ↓
 Final   │  Blocklist +
 Output  │  Regeneration
         └───────────→
