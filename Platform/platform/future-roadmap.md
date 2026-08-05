---
hidden: true
---

# Future Roadmap

Mithrl's mission is to accelerate every stage of therapeutic development, from early discovery to late-stage clinical translation. While the platform today focuses on RNA-seq and mechanistic analysis, we're expanding rapidly to support more data types, integrate multi-omics workflows, and enable decision-making across the full drug development lifecycle.

At Mithrl, we move fast. Our small, focused team ships features in days, not quarters. We work hand-in-hand with scientists, bioinformaticians, and R\&D leads across our customer base to co-develop what matters most, always with the goal of accelerating discovery and decision-making.

This roadmap reflects where we're headed. Some of these features are already underway with partner labs. Others are coming next. If you're excited about anything you see here, let us know. Chances are, we're already working on it.

***

## 🧬 Genomic & Epigenomic Expansion

### Whole Genome & Whole Exome Sequencing (WGS & WES)

**What it will do**

Support for WGS and WES pipelines will enable mutation calling, copy number analysis, and variant annotation. These features will link directly to downstream gene expression interpretation.

**Use Cases**

* Detect driver mutations and actionable variants in cancer
* Correlate mutational burden with expression and pathway shifts
* Integrate variant-level data into therapeutic hypothesis generation

**Planned Outputs**

* Annotated variant call files (VCFs)
* Mutation-expression overlay plots
* Gene-centric variant summaries

***

### DNA Methylation (Bulk and Single-Cell)

**What it will do**

We'll support methylation data from both bulk and single-cell platforms (e.g. scBS-seq, snmC-seq), allowing researchers to integrate epigenetic context into expression and regulatory analysis.

**Use Cases**

* Identify silenced tumor suppressors or activated enhancers
* Profile cell-type-specific methylation shifts after treatment
* Connect regulatory regions to expression output

**Planned Outputs**

* Differentially methylated regions (DMRs)
* Correlation plots with expression data
* Epigenetic pathway activation maps

***

## 🧪 Multi-Omics Integration

### Proteomics + Metabolomics Support

**What it will do**

You'll be able to upload proteomics and metabolomics data alongside transcriptomics to enable system-wide analysis. This will include bulk mass spectrometry (LC-MS, CyTOF) and targeted panels.

**Use Cases**

* Cross-validate expression-level hits at the protein level
* Link metabolic shifts to gene expression and pathway activity
* Profile drug mechanism with layered molecular evidence

**Planned Outputs**

* Correlation heatmaps across omics
* Integrated volcano plots
* Protein/gene/metabolite co-enrichment maps

***

### Multi-Omics Cohort Analysis

**What it will do**

Combining transcriptomics, epigenomics, proteomics, and metabolomics from the same samples or patients to drive unified clustering, signature development, and translational hypothesis testing.

**Use Cases**

* Discover patient subgroups using multi-omic signals
* Improve biomarker robustness by integrating layers
* Reduce false positives by triangulating across modalities

**Planned Outputs**

* Multi-omic clustering plots
* Cross-omic trajectory and UMAP
* Unified enrichment across all omics types

***

## 👩‍🔬 AI Co-Scientists for Full Drug Development

Beyond omics, Mithrl is building a suite of AI Co-Scientists that specialize in downstream phases of the therapeutic pipeline. These modules will extend the platform from insight generation to decision support across IND-enabling studies and clinical trial execution.

***

### Lead Optimization

**What it will do**

Ingest SAR data, in vitro results, and expression shifts from compound screening to help rank and prioritize candidate molecules.

**Use Cases**

* Identify compounds with favorable on-target/off-target profiles
* Link molecular features to biological impact
* Suggest analogs with improved safety margins

***

### High-Throughput Screening (HTS)

**What it will do**

Analyze thousands of compound screens across gene expression, viability, and phenotypic data.

**Use Cases**

* Discover dose-response thresholds at a transcriptomic level
* Classify compound categories by mechanism
* Filter hits by safety, potency, or multi-omic response

***

### IND-Enabling Studies

**What it will do**

Automate key analyses and summaries for IND preparation, including dose-response justification, toxicogenomics, and cross-species translation checks.

**Use Cases**

* Detect and flag toxic signatures preclinically
* Generate summary tables and visuals for regulators
* Score transcriptomic similarity between model systems and human samples

***

### Clinical Trial Analysis

**What it will do**

Support biomarker-driven analysis of Phase 1 and Phase 2 trials using transcriptomic, proteomic, and methylation data.

**Use Cases**

* Stratify patients by biomarker expression
* Compare arms using mechanistic signatures
* Generate AI-assisted clinical reports for regulatory bodies

***

## 💡 Partnering on the Roadmap

We develop these features in collaboration with scientists and therapeutic programs on the front lines.

If you're planning to bring in:

* WGS or WES pipelines
* Bulk or single-cell epigenetics
* Proteomics or metabolomics
* Cohort-scale multi-omics experiments
* IND or clinical-stage decision-making

...we'd love to support you.

Contact us at [support@mithrl.com](mailto:support@mithrl.com) or talk to your Customer Success Manager directly.

Let's build the future of scientific discovery together.

{% include "../.gitbook/includes/support-footer.md" %}
