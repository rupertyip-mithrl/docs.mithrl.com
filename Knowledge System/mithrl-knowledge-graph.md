---
hidden: true
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

# Mithrl Knowledge Graph

## Architecture & entity Overview

## Overview

Mithrl's knowledge platform combines a structured gene–phenotype–variant knowledge graph with curated reference tables, ontology databases, and a literature store with semantic embeddings. Together, these layers power the interpretation, hypothesis generation, and biological reasoning capabilities within Mithrl's platform. Alongside the graph, a set of curated reference tables covers pathways, transcriptional regulation, gene sets, cell-type markers, expression context, and drug/safety overlays. All layers are queryable through a unified internal API surface.

## Entity Types (Nodes)

The knowledge graph currently contains three entity types:

<table><thead><tr><th width="220.41015625" valign="top">Entity Type</th><th width="247.1875" valign="top">Examples</th><th valign="top">Notes</th></tr></thead><tbody><tr><td valign="top">Gene</td><td valign="top">TP53, BRCA1, EGFR</td><td valign="top">Species-scoped: human, mouse, pig, zebrafish, crab-eating macaque</td></tr><tr><td valign="top">Phenotype / Biomodule</td><td valign="top">Disease states, biological contexts</td><td valign="top">Encompasses disease phenotypes, tissue/cell-type contexts, biological processes, and user-defined biological modules</td></tr><tr><td valign="top">Gene Variant</td><td valign="top">SNPs, structural variants</td><td valign="top">First-class entities with variant-specific relationship types</td></tr></tbody></table>

Species coverage: human, mouse, pig, zebrafish, and crab-eating macaque. Cross-species ortholog projection is supported for queries that require remapping (e.g. pig genes to human orthologs).

## Relationship Types (Edges)

Edges are typed to distinguish associative from directional/mechanistic claims. Every edge can carry citations (PubMed IDs), a free-text reasoning field, and a confidence/evidence status flag.

<table><thead><tr><th width="216.9609375" valign="top">Relationship Type</th><th width="140.16796875" valign="top">Directionality</th><th valign="top">Description</th></tr></thead><tbody><tr><td valign="top">Associated</td><td valign="top">Undirected</td><td valign="top">General association; largest category (~793k edges). Covers gene–phenotype, gene–gene, and literature-mined links.</td></tr><tr><td valign="top">Positive Impact</td><td valign="top">Directed</td><td valign="top">Increase in source entity is associated with increase in target; used for mechanistic/causal claims (~7k edges).</td></tr><tr><td valign="top">Negative Impact</td><td valign="top">Directed</td><td valign="top">Increase in source associated with decrease in target; directional inhibitory or downregulatory signal (~6k edges).</td></tr><tr><td valign="top">Gene Variant</td><td valign="top">Directed</td><td valign="top">Variant annotates or belongs to a gene locus (~44k edges).</td></tr><tr><td valign="top">Variant Phenotype Effect</td><td valign="top">Directed</td><td valign="top">Effect of a variant on a phenotype or disease context (~50k edges).</td></tr></tbody></table>

Coverage note: the graph is predominantly associative — \~793k of \~900k edges are undirected associations, while directed mechanistic edges (Positive Impact / Negative Impact) currently total \~13k. This reflects the inherent availability of curated causal evidence in the literature, not a design limitation. Causal edge curation is an active and ongoing priority.

Evidence filtering: edges are classified as having sufficient or insufficient evidence based on citation and curation provenance. Approximately 95% of edges carry at least one supporting citation and are returned by default in queries. Edges flagged as insufficient evidence are retained in the graph for completeness but excluded from default analytical results unless explicitly requested.

## Knowledge Sources

The graph is populated from a combination of public databases, curated literature, and internally generated hypotheses from Mithrl's analysis pipelines. All literature sources are PubMed-ID anchored — no unverified web content is ingested.

<table><thead><tr><th width="249.390625" valign="top">Source</th><th valign="top">Role in Knowledge Graph</th></tr></thead><tbody><tr><td valign="top">NCBI Gene</td><td valign="top">Gene identity, symbols, summaries, and species-scoped tables; basis for internal gene identifiers</td></tr><tr><td valign="top">KEGG</td><td valign="top">Gene–pathway membership and pathway metadata</td></tr><tr><td valign="top">Gene Ontology (GO)</td><td valign="top">Gene–GO term annotations across Biological Process, Molecular Function, and Cellular Component</td></tr><tr><td valign="top">UniProt</td><td valign="top">Protein-level descriptive context and gene summaries</td></tr><tr><td valign="top">TRRUST</td><td valign="top">Curated transcription factor–target regulatory edges (human and mouse)</td></tr><tr><td valign="top">MSigDB</td><td valign="top">Gene set membership and semantic similarity over curated sets</td></tr><tr><td valign="top">Human Protein Atlas</td><td valign="top">Tissue and cell-type expression features; gene–tissue/cell-type association</td></tr><tr><td valign="top">Open Targets</td><td valign="top">Target-level drug context, safety signals, and druggability; queried dynamically in addition to static edges</td></tr><tr><td valign="top">PubMed / Primary Literature</td><td valign="top">Full-text ingestion with curated PubMed ID provenance; powers semantic retrieval and supports edge evidence citation</td></tr></tbody></table>

In addition to static database ingestion, Mithrl's analysis pipelines can generate new gene–phenotype hypotheses that are added to the graph as internally-derived edges, clearly marked with their source provenance. This allows the graph to grow dynamically as analyses are run on the platform. Note on Open Targets: drug, safety, and druggability data from Open Targets is queried dynamically at runtime rather than fully materialized as static KG edges. This means those results reflect the current state of the Open Targets dataset at query time, and may differ slightly between query dates as Open Targets releases updates. All other sources are versioned and static within a given Mithrl release.

## Scale & Descriptive Statistics

<table><thead><tr><th width="251.3203125" valign="top">Category</th><th width="175.47265625" valign="top">Count (approx.)</th><th valign="top">Notes</th></tr></thead><tbody><tr><td valign="top">Phenotypes / Biomodules</td><td valign="top">~24,000</td><td valign="top">Disease states, tissue contexts, biological modules</td></tr><tr><td valign="top">Gene Variants</td><td valign="top">~43,000</td><td valign="top">SNPs and structural variants</td></tr><tr><td valign="top">Total Relationships</td><td valign="top">~900,000</td><td valign="top">All edge types combined</td></tr><tr><td valign="top">Strong Evidence Relationships</td><td valign="top">~857,000</td><td valign="top">Edges with at least one citation or curated source (~95% of total). Edges lacking evidence are retained but excluded from default query results.</td></tr><tr><td valign="top">Directed / mechanistic edges</td><td valign="top">~13,000</td><td valign="top">Positive Impact + Negative Impact combined. Causal coverage is narrower than associative; active curation is ongoing.</td></tr></tbody></table>

## Custom / Institutional Knowledge Graph Extension

Mithrl supports augmenting the shared knowledge graph with customer-specific content. This is particularly relevant for organizations with proprietary compound data, bespoke biological contexts, or non-public experimental results that should inform interpretation.

The integration pathway works as follows:

* Structured data (triples): customer-provided entity–relationship–entity triples can be directly ingested into a tenant-isolated graph partition.
* Unstructured data (documents, notebooks): Mithrl's literature curation pipeline can process PDFs, lab notebooks, and structured text to extract entities and relationships, which are then QC-reviewed before graph ingestion.
* Fine-tuning: edge cases that require human-in-the-loop review are documented and used to iteratively fine-tune Mithrl's curation models, reducing the manual review burden over time.

Customer-specific graph partitions are strictly isolated — they do not contribute to the shared public graph and are only accessible within the customer's environment.

## What the Knowledge Graph Enables

The graph and reference layers together power the following capabilities within Mithrl's platform:

* Hypothesis generation: gene–phenotype relationship queries grounded in curated evidence, with citations and confidence levels
* Pathway and regulatory analysis: TF–target regulatory matrices (TRRUST-backed), pathway adjacency, and gene-set enrichment
* Cell-type annotation: marker-based cell-type identification using curated marker sets and natural-language marker queries
* Drug and safety context: druggability, known drug associations, and safety signals via Open Targets integration
* Semantic retrieval: literature search grounded in PubMed-anchored chunks, not open-web content
* Cross-species analysis: ortholog-aware queries that remap experimental species to human where relevant
* Institutional augmentation: customer knowledge graph extension for proprietary compound or experimental context

{% include "../.gitbook/includes/support-footer.md" %}
