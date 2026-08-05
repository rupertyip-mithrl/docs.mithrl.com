---
hidden: true
---

# Beta Features

The features listed below are currently in **beta**, which means they are being actively tested and improved. They're functional and available to select customers, but they may occasionally behave unpredictably or return incomplete results depending on the dataset.

We expect and welcome your feedback.

We ship fast. If something doesn't work the way you expected, let us know. Most bugs are resolved within days, and your suggestions often directly shape how these features evolve into production tools.

If you'd like to activate any beta feature in your workspace, reach out to your Mithrl Customer Success Manager in Slack or Teams, or email us at [support@mithrl.com](mailto:support@mithrl.com).

{% hint style="info" %}
These features are still under active development. While you are welcome to explore and use them, they may occasionally behave unexpectedly or be incomplete.
{% endhint %}

## 🧬 Molecular Subtyping

**What it does**: Classifies samples into known molecular subtypes based on expression patterns. For example, breast cancer samples can be categorized as Luminal A, Luminal B, HER2+, or Basal-like using PAM50.

**Why it matters**: Subtypes guide therapeutic selection, predict prognosis, and help stratify patients for trials.

**Supports**:

* Bulk RNA-seq

**Methods**:

* Cancer-type-specific classifiers (currently supports PAM50)

**Outputs**:

* Subtype assignment per sample
* Subtype-specific gene signature scores
* Visualization of classification confidence

**Use Cases**:

* Stratify patients in drug response studies
* Predict therapeutic vulnerability based on subtype
* Exclude samples not relevant to mechanism being studied

**Suggested Prompts**:

```
Classify each sample by molecular subtype using the PAM50 signature.
```

```
Which samples are likely HER2+?
```

```
Show a bar plot of predicted subtypes across all patients.
```

***

## 📚 Discovery Engine (Literature-Augmented Insights)

**What it does**: Retrieves relevant biological literature and summaries to support hypotheses using retrieval-augmented generation (RAG) models.

**Why it matters**: You get fast answers grounded in publications without needing to manually search PubMed or sift through PDFs.

**Supports**:

* All input types (bulk, scRNA)
* Any analysis result

**Methods**:

* Scientific literature search
* NLP-based summarization and evidence linking

**Outputs**:

* Citations and article summaries
* Gene-disease-drug relationship evidence
* Contextual quotes from peer-reviewed studies

**Use Cases**:

* Validate a proposed target against the literature
* Find known mechanisms or safety concerns
* Generate hypothesis-supporting text for reports or slides

**Suggested Prompts**:

```
What's known about gene X in lung adenocarcinoma?
```

```
Has gene Y been linked to resistance in breast cancer?
```

```
Summarize the mechanism of Drug A based on published studies.
```

***

## Guidance

{% hint style="warning" %}
**Important Notes on Beta Features**

* **Instability is possible**. These tools may occasionally return unexpected outputs or fail on edge-case datasets.
* **Feedback is expected**. If something doesn't work or feels off, tell us. We review user feedback continuously.
* **We move fast**. Most bugs and improvements are shipped within 48–72 hours. You won't be waiting weeks.
{% endhint %}

To activate any of these tools:

* Message your **Customer Success Manager** in your dedicated Slack or Teams channel
* Or email us at [support@mithrl.com](mailto:support@mithrl.com)

Your feedback directly shapes what becomes part of Mithrl's core.

{% include "../.gitbook/includes/support-footer.md" %}
