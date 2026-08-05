---
hidden: true
---

# Supported Features

Below is a list of all features available to every Mithrl user. Each one is fully supported in production environments, designed to reduce manual effort and let scientists focus on discovery.

Each section includes:

* What the feature is
* Why it matters in therapeutic research
* What data it works with
* Example prompts you can use in Mithrl

***

## 🔍 Exploratory Data Analysis (EDA)

**What it does**: Helps you understand your dataset before running deeper analyses. EDA includes quality control, basic statistics, and detecting sample-level outliers.

**Why it matters**: It's the first step to catch low-quality samples, confirm input integrity, and make sure you're asking questions of reliable data.

**Supports**:

* Bulk RNA-seq: counts or TPM
* scRNA-seq: raw count matrices

**Outputs**:

* Sample correlation heatmaps
* Violin plots of distributions
* QC stats for each sample

**Example Use Cases**:

* Detect samples with low total counts or technical artifacts
* See if treated and control groups separate early on
* Flag samples that may skew downstream results

**Suggested Prompts**:

{% hint style="info" %}
You can copy these prompts and run them directly in Mithrl.
{% endhint %}

```
Show the total counts for each sample on a bar plot to identify outlier samples.
```

```
Can you plot a correlation heatmap between using samples?
```

```
Which Cluster only appears in diseased patients?
```

***

## 🔬 Differential Expression Analysis (DEA)

**What it does**: Identifies genes that are statistically up- or downregulated between groups (e.g. treated vs control).

**Why it matters**: This is often the core of any biological discovery workflow finding genes affected by your drug, knockout, or condition.

**Supports**:

* Bulk RNA-seq: DESeq2
* scRNA-seq: Wilcoxon rank-sum (cell-type-specific)

**Outputs**:

* Volcano plots
* Fold change tables
* Significance values (p-adj)

**Example Use Cases**:

* Find genes most responsive to a drug
* Discover transcriptional signatures of disease or treatment
* Validate hits seen in vitro or in vivo
* Upset plot showcasing DEGs unique to single treatment or common to many treatments

**Suggested Prompts**:

```
What genes are differentially expressed between Drug A and control?
```

```
Show me genes upregulated in T cells after treatment.
```

```
Give me a volcano plot comparing all treated vs untreated samples.
```

***

## 🧪 Functional Enrichment Analysis (FEA)

**What it does**: Maps your differentially expressed genes to known biological pathways to understand their functional impact.

**Why it matters**: Genes don't act in isolation. Pathways tell you how groups of genes are cooperating or failing under treatment.

**Supports**:

* Bulk RNA-seq (DEA results)
* scRNA-seq (DEA results)

**Outputs**:

* Enrichment bar charts
* KEGG pathway overlays
* Gene-pathway relationship tables

**Example Use Cases**:

* Validate that your drug hits its intended pathway
* Suggest additional targets in the same pathway
* Spot potential toxicity via enriched off-target pathways

**Suggested Prompts**:

```
What KEGG pathways are enriched in my DEGs from treated vs control?
```

```
Show me functional enrichment results for upregulated genes.
```

```
Which pathways are most downregulated after Drug B treatment?
```

***

## 🎯 Target Discovery

**What it does**: Uses expression changes, literature, and network features to highlight genes that are strong therapeutic candidates.

**Why it matters**: Helps prioritize which genes to validate, develop assays for, or present in team meetings as promising targets.

**Supports**:

* Bulk RNA-seq
* scRNA-seq
* PPI networks + curated knowledge bases

**Outputs**:

* Ranked target list
* Proposed target reports and hypothesis
* Literature support summaries

**Example Use Cases**:

* Find underexplored targets with strong network roles
* Cross-validate known targets using expression and evidence
* Identify biomarkers for diagnostics or stratification

**Suggested Prompts**:

```
What genes are high-priority therapeutic targets based on my DEA results?
```

```
Show me druggable targets affected by treatment that also appear in the literature.
```

```
Prioritize targets using network connectivity and upregulation after Drug X.
```

***

## 🔗 Protein-Protein Interaction (PPI) Analysis

**What it does**: Visualizes how your differentially expressed genes interact as part of protein networks and scores key hubs.

**Why it matters**: Central genes in networks often have outsized biological roles. Targeting a hub can have system-level effects.

**Supports**:

* Bulk RNA-seq + DEA
* scRNA-seq + DEA

**Outputs**:

* Network graph visualizations
* Hub gene identification
* Gene connectivity metrics

**Example Use Cases**:

* Identify master regulators or upstream drivers
* Suggest combination therapy based on converging nodes
* Explore pathways not apparent from expression alone

**Suggested Prompts**:

```
Visualize the protein interaction network for upregulated genes.
```

```
Highlight hub genes in the PPI network.
```

```
Which genes act as central nodes among DEGs in my treated samples?
```

***

## 🧬 Clustering Analysis

**What it does**: Groups samples (or cells) based on similarity in gene expression.

**Why it matters**: Discover hidden structure in your dataset, such as subtypes, dose-dependent patterns, or unexpected outliers.

**Supports**:

* Bulk RNA-seq
* scRNA-seq

**Methods**:

* Leiden / Louvain clustering

**Outputs**:

* Cluster labels per sample or cell
* Clusters overlay on any supported dimensionality reduction coordinates (e.g. UMAP, PCA, tSNE, etc.)

**Example Use Cases**:

* Discover molecular subtypes among patients
* Cluster cells by expression to annotate cell states
* Predict who may respond to treatment

**Suggested Prompts**:

```
Cluster the samples and visualize them in 2D space.
```

```
How many distinct clusters exist in this dataset?
```

```
Assign clusters to cells and label them on a UMAP plot.
```

***

## 🧬 Cell Type Identification (scRNA-seq)

**What it does**: Automatically assigns known cell types to clusters in single-cell RNA-seq datasets using marker genes and literature.

**Why it matters**: Cell-type resolution is critical in precision biology. Knowing which cells respond to treatment helps you understand selectivity, safety, and mechanism.

**Supports**:

* scRNA-seq only (10x or similar)
* Optional: custom marker sets

**Methods**:

* Marker gene scoring
* Reference-assisted annotation
* Optional: automated literature matching

**Outputs**:

* Cluster-to-cell-type mapping
* Interactive dimensionally reduction plots with labeled cell-types
* Marker gene enrichment per cluster

**Use Cases**:

* Identify responder or non-responder cell types
* Confirm targeting specificity
* Profile immune subtypes or tumor microenvironment

**Suggested Prompts**:

```
Can you identify any immune cell types in the scRNA-seq dataset?
```

```
Assign cell type labels to each cluster using the following cell-type markers: ACM contains the genes MYH6, MYL7, GJA5, and NPPA; VCM includes the genes MYH7, MYL3, TNNC1, and HSPB7
```

```
Visualize UMAP and color by inferred cell type.
```

***

## 📉 Dimensionality Reduction

**What it does**: Projects your high-dimensional data into 2D or 3D to help you see global patterns and separation between groups.

**Why it matters**: Reduces complexity, highlights trends, and helps interpret overall structure.

**Supports**:

* Bulk RNA-seq
* scRNA-seq

**Methods**:

* PCA, UMAP, t-SNE, PACMAP

**Outputs**:

* Interactive scatter plots
* Color overlays by metadata or gene expression

**Example Use Cases**:

* Visualize how Drug A shifts treated samples
* Detect batch effects
* Spot rare cell populations

**Suggested Prompts**:

```
Run UMAP on all samples and color by treatment group.
```

```
Use PCA to visualize how samples differ by condition.
```

```
Plot a t-SNE and highlight gene X's expression.
```

***

{% hint style="info" %}
**Useful Tips**

Each feature can be used directly through natural language input. Simply describe what you want to see — Mithrl will handle the preprocessing, statistics, and visuals.
{% endhint %}

If you're unsure how to phrase something, reach out to your Customer Success Manager via Slack, Teams, or email us at [support@mithrl.com](mailto:support@mithrl.com).

{% include "../.gitbook/includes/support-footer.md" %}
