# Key Concepts

## Raw Data (Files)

Raw data can be in the form of fastq files, matrix data, or tabular data (csv, tsv, etc). Such files can be outputs from scientific instruments or processed data files from such instruments or other bioinformatic sources. These files may be derivatives of image files (ex. processed matrix data from spatial images, cell paintings, etc), proteomics platforms (ex. high throughput mass spectrometry, antibody protein arrays, etc.), or gene expression platforms (ex.microarray).

## Datasets

Mithrl datasets form the foundation of the Mithrl Scientific Decision Engine. A Mithrl dataset is in the MFF format (Mithrl Friendly Format) and is the result of cleaning raw data files via nomenclature standardization, normalization, and harmonization. Once the dataset is created it is then ready for any agentic processing to allow acalable, and flexible tertiary analysis and hypothesis generation. This data clean up process also allows for ready true cross-dataset and cross-omics analysis.

## Analysis

An analysis is the series of natural-language queries (questions) a user asks of one or more datasets. For example, a user might take the results of a one-time single-cell experiment then ask for a volcano plot followed by a list of the top DEGs, followed by a list of the enriched pathways, followed by predicted targets. That entire thread would be an analysis.

## Projects

Projects are an aggregation of Mithrl datasets that are related to a specific research goal. Projects may include multiple analysis threads, multiple datasets and across multiple modalities.

{% include "../.gitbook/includes/support-footer.md" %}
