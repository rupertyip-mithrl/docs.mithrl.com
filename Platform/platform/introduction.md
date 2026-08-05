---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Introduction

Mithrl is your AI scientific collaborator.

We've built the first commercially available Scientific Decision Engine (SDE) designed specifically for R\&D and discovery teams. From raw sequencing files to hypotheses, Mithrl compresses the time it takes to analyze, interpret, and act on biological data, from months to minutes.

This documentation outlines what the platform supports today, what is currently in limited release, and what's in active development. If you're running NGS and multi-omics experiments, looking for novel targets, or validating mechanisms of action, this guide is for you.

***

## What is Mithrl?

Mithrl is an AI-powered platform that automates NGS and multi-omics analysis, data visualization, data exploration, and hypothesis generation. It's used by therapeutic research teams to extract biological meaning from large datasets without the need for custom coding or manual data wrangling.

{% hint style="success" %}
**Mithrl supports:**

* **Bulk RNA-seq, scRNA-seq, DRUG-seq, ATAC-seq, and ChIP-seq data analysis** (10X, Smart-seq, and others)
* **Proteomics data from high throughput mass spectrometry (HTS) and Illumina Protein Prep (Somalogics)**
* **Natural language-driven workflows** — ask a scientific question and get real answers
* **Differential expression, enrichment, clustering**, and **network-based analyses**
* **Automated insight reports** with plots, gene-level tables, and mechanistic interpretation
* **Target discovery, mechanism-of-action modeling**, and **hypothesis generation**
{% endhint %}

Designed for scientists, Mithrl handles everything from normalization, statistical analysis, visualization, literature-backed interpretation & hypothesis generation all behind the scenes.

***

## Clarifying Questions

Mithrl is built to behave like a thoughtful lab partner, not a black box. When your question is ambiguous or missing key details, it won't make assumptions or fill in gaps with made-up answers. Instead, it will ask for clarification so it can give you a precise and scientifically valid response.

For example, if you ask:

```
Show me differentially expressed genes
```

Mithrl might respond with:

```
Which groups should I compare? I didn't detect clear treatment and control labels in your question.
```

Or if you ask:

```
Find genes that are statistically significant
```

It might prompt:

```
Could you confirm the p-value threshold you want to use for significance? Default is 0.05.
```

***

## Follow-Up Questions

Mithrl doesn't just answer one question at a time. It understands context across your entire session and enables a conversational workflow that reflects how scientists naturally think through a problem.

When you ask a follow-up, Mithrl uses the results from the previous step. Whether it's a differential expression list, a filtered dataset, or an enrichment analysis, that result becomes the foundation for the next step. There's no need to restate the entire prompt or re-select your dataset. This allows you to iterate, refine, and dig deeper just like you would at the bench or in a discussion with a teammate.

For example:

```
What genes are upregulated in treated vs control?
```

```
Which of those are involved in apoptosis?
```

```
Show me KEGG pathways enriched in those genes.
```

```
Of those pathways, which ones overlap with known toxicity pathways?
```

***

## How This Documentation is Organized

This site is structured to be navigable by both bench scientists and informatics leads:

* [**Key Concepts**](key-concepts.md) - these are the core objects within the Mithrl platform
* [**Supported Features**](supported-features.md) — Tools available across all standard accounts.
* [**Mithrl Knowledge Graph**](mithrl-knowledge-graph.md) — A curated collection of public and private databases representing the domain knowledge of biology
* [**Trust Center**](https://trust.mithrl.com/resources?s=wgh724r3nig9pglpqnbqp\&name=hipaa-workstation-security-policy) — Mithrl's Trust Center showcases the company's SOC2 compliance certifications, and privacy policies.

If you're new to Mithrl, we recommend starting with **Supported Features** for a sense of what's immediately usable in your workspace.

***

## What Mithrl Replaces

Scientists use Mithrl to eliminate manual bioinformatics bottlenecks:

| Without Mithrl                                    | With Mithrl                                               |
| ------------------------------------------------- | --------------------------------------------------------- |
| Waiting weeks for differential expression results | Results in minutes                                        |
| Manually annotating DE genes in Excel             | Automated pathway enrichment + plots                      |
| Outsourced reports with no reproducibility        | Reproducible reports with all inputs documented           |
| Hard-to-interpret clustering heatmaps             | Dimensionality-reduced plots with annotated clusters      |
| Fragmented tools across multiple systems          | Unified, conversational interface with exportable reports |

***

## Support

{% hint style="info" %}
If you need help with the platform, you have multiple ways to reach us:
{% endhint %}

* **Email**: [support@mithrl.com](mailto:support@mithrl.com)
* **Slack or Teams**: Reach out in your **dedicated customer success channel**
* **Feature questions or analysis blockers**: Ping your **Customer Success Manager** directly or email [support@mithrl.com](mailto:support@mithrl.com)

We're happy to assist with data uploads, onboarding training, or scientific interpretation of results.

***

Let's get started.

{% include "../.gitbook/includes/support-footer.md" %}
