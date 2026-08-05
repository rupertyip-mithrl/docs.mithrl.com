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

## Mithrl Knowledge Graph

### Architecture & entity Overview <a href="#architecture-and-entity-overview" id="architecture-and-entity-overview"></a>

### Overview <a href="#overview" id="overview"></a>

Mithrl's knowledge platform combines a structured gene–phenotype–variant knowledge graph with curated reference tables, ontology databases, and a literature store with semantic embeddings. Together, these layers power the interpretation, hypothesis generation, and biological reasoning capabilities within Mithrl's platform. Alongside the graph, a set of curated reference tables covers pathways, transcriptional regulation, gene sets, cell-type markers, expression context, and drug/safety overlays. All layers are queryable through a unified internal API surface.

### Entity Types (Nodes) <a href="#entity-types-nodes" id="entity-types-nodes"></a>

The knowledge graph currently contains three entity types:

Entity TypeExamplesNotes

Gene

TP53, BRCA1, EGFR

Species-scoped: human, mouse, pig, zebrafish, crab-eating macaque

Phenotype / Biomodule

Disease states, biological contexts

Encompasses disease phenotypes, tissue/cell-type contexts, biological processes, and user-defined biological modules

Gene Variant

SNPs, structural variants

First-class entities with variant-specific relationship types

Species coverage: human, mouse, pig, zebrafish, and crab-eating macaque. Cross-species ortholog projection is supported for queries that require remapping (e.g. pig genes to human orthologs).

### Relationship Types (Edges) <a href="#relationship-types-edges" id="relationship-types-edges"></a>

Edges are typed to distinguish associative from directional/mechanistic claims. Every edge can carry citations (PubMed IDs), a free-text reasoning field, and a confidence/evidence status flag.

Relationship TypeDirectionalityDescription

Associated

Undirected

General association; largest category (\~793k edges). Covers gene–phenotype, gene–gene, and literature-mined links.

Positive Impact

Directed

Increase in source entity is associated with increase in target; used for mechanistic/causal claims (\~7k edges).

Negative Impact

Directed

Increase in source associated with decrease in target; directional inhibitory or downregulatory signal (\~6k edges).

Gene Variant

Directed

Variant annotates or belongs to a gene locus (\~44k edges).

Variant Phenotype Effect

Directed

Effect of a variant on a phenotype or disease context (\~50k edges).

Coverage note: the graph is predominantly associative — \~793k of \~900k edges are undirected associations, while directed mechanistic edges (Positive Impact / Negative Impact) currently total \~13k. This reflects the inherent availability of curated causal evidence in the literature, not a design limitation. Causal edge curation is an active and ongoing priority.

Evidence filtering: edges are classified as having sufficient or insufficient evidence based on citation and curation provenance. Approximately 95% of edges carry at least one supporting citation and are returned by default in queries. Edges flagged as insufficient evidence are retained in the graph for completeness but excluded from default analytical results unless explicitly requested.

### Knowledge Sources <a href="#knowledge-sources" id="knowledge-sources"></a>

The graph is populated from a combination of public databases, curated literature, and internally generated hypotheses from Mithrl's analysis pipelines. All literature sources are PubMed-ID anchored — no unverified web content is ingested.

SourceRole in Knowledge Graph

NCBI Gene

Gene identity, symbols, summaries, and species-scoped tables; basis for internal gene identifiers

KEGG

Gene–pathway membership and pathway metadata

Gene Ontology (GO)

Gene–GO term annotations across Biological Process, Molecular Function, and Cellular Component

UniProt

Protein-level descriptive context and gene summaries

TRRUST

Curated transcription factor–target regulatory edges (human and mouse)

MSigDB

Gene set membership and semantic similarity over curated sets

Human Protein Atlas

Tissue and cell-type expression features; gene–tissue/cell-type association

Open Targets

Target-level drug context, safety signals, and druggability; queried dynamically in addition to static edges

PubMed / Primary Literature

Full-text ingestion with curated PubMed ID provenance; powers semantic retrieval and supports edge evidence citation

In addition to static database ingestion, Mithrl's analysis pipelines can generate new gene–phenotype hypotheses that are added to the graph as internally-derived edges, clearly marked with their source provenance. This allows the graph to grow dynamically as analyses are run on the platform. Note on Open Targets: drug, safety, and druggability data from Open Targets is queried dynamically at runtime rather than fully materialized as static KG edges. This means those results reflect the current state of the Open Targets dataset at query time, and may differ slightly between query dates as Open Targets releases updates. All other sources are versioned and static within a given Mithrl release.

### Scale & Descriptive Statistics <a href="#scale-and-descriptive-statistics" id="scale-and-descriptive-statistics"></a>

CategoryCount (approx.)Notes

Phenotypes / Biomodules

\~24,000

Disease states, tissue contexts, biological modules

Gene Variants

\~43,000

SNPs and structural variants

Total Relationships

\~900,000

All edge types combined

Strong Evidence Relationships

\~857,000

Edges with at least one citation or curated source (\~95% of total). Edges lacking evidence are retained but excluded from default query results.

Directed / mechanistic edges

\~13,000

Positive Impact + Negative Impact combined. Causal coverage is narrower than associative; active curation is ongoing.

### Custom / Institutional Knowledge Graph Extension <a href="#custom-institutional-knowledge-graph-extension" id="custom-institutional-knowledge-graph-extension"></a>

Mithrl supports augmenting the shared knowledge graph with customer-specific content. This is particularly relevant for organizations with proprietary compound data, bespoke biological contexts, or non-public experimental results that should inform interpretation.

The integration pathway works as follows:

* Structured data (triples): customer-provided entity–relationship–entity triples can be directly ingested into a tenant-isolated graph partition.
* Unstructured data (documents, notebooks): Mithrl's literature curation pipeline can process PDFs, lab notebooks, and structured text to extract entities and relationships, which are then QC-reviewed before graph ingestion.
* Fine-tuning: edge cases that require human-in-the-loop review are documented and used to iteratively fine-tune Mithrl's curation models, reducing the manual review burden over time.

Customer-specific graph partitions are strictly isolated — they do not contribute to the shared public graph and are only accessible within the customer's environment.

### What the Knowledge Graph Enables <a href="#what-the-knowledge-graph-enables" id="what-the-knowledge-graph-enables"></a>

The graph and reference layers together power the following capabilities within Mithrl's platform:

* Hypothesis generation: gene–phenotype relationship queries grounded in curated evidence, with citations and confidence levels
* Pathway and regulatory analysis: TF–target regulatory matrices (TRRUST-backed), pathway adjacency, and gene-set enrichment
* Cell-type annotation: marker-based cell-type identification using curated marker sets and natural-language marker queries
* Drug and safety context: druggability, known drug associations, and safety signals via Open Targets integration
* Semantic retrieval: literature search grounded in PubMed-anchored chunks, not open-web content
* Cross-species analysis: ortholog-aware queries that remap experimental species to human where relevant
* Institutional augmentation: customer knowledge graph extension for proprietary compound or experimental context
