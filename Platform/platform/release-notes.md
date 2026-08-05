# Release Notes

## Release 2026-07-08

**Improved User Experience.** We've streamlined the Mithrl user interface to reduce clutter and verbose text.

* There are now only 3 tabs: Home, Datasets, and Raw Files.
* NEW: Questions panel that list all the questions in the conversation of an analysis\
  NEW: Enlarged Results tab that show the&#x20;
  * &#x20;Plan
  * Clarification decisions made by user
  * Artifacts (plots, tables, graphs, etc)
  * Trace (of actions taken)
  * Summary on the answer to your question.

<figure><img src="../.gitbook/assets/Screenshot 2026-07-08 at 4.57.55 PM.png" alt=""><figcaption></figcaption></figure>

* NEW: Audit log tab that shows the full thinking process, ad hoc code, and steps taken to arrive at the answer to your question. The artifacts generated here are also available in the Results tab.

<figure><img src="../.gitbook/assets/Screenshot 2026-07-08 at 4.27.40 PM.png" alt=""><figcaption></figcaption></figure>

* NEW: Files tab the shows all the artifacts (Mithrl-generated tables, plots, etc) that are downloadable individually or in bulk download.

<figure><img src="../.gitbook/assets/Screenshot 2026-07-08 at 4.30.18 PM.png" alt=""><figcaption></figcaption></figure>

**Improved interactivity with graphs and plots.** You can now use sliders (when available) to view scatter plots and histograms.

<figure><img src="../.gitbook/assets/Screenshot 2026-07-08 at 5.36.52 PM.png" alt=""><figcaption></figcaption></figure>

**Upstream Regulator Networks.** Leveraging the power of the Mithrl knowledge graph, the platform can now predict the upstream regulator networks to explain observational data.

<figure><img src="../.gitbook/assets/Screenshot 2026-07-08 at 5.55.53 PM.png" alt=""><figcaption></figcaption></figure>

**Platform perfomance improvements.** The system should be faster to start, less likely to crash, and safer about saving results.



***

## Release 2026-06-22

**Plots and Graphs now available is PRISM format.** You can now export the Mithrl-generated plots and graphs in PRISM format. The exported plot files are in .PRISM format which should be compatible with the current and legacy versions of GraphPad Prism. To export a plot, click on the 3 dots in the upper right corner of the plot then select Export PRISM to export the plot in PRISM format.

<figure><img src="../.gitbook/assets/Screenshot 2026-06-23 at 2.11.47 PM.png" alt=""><figcaption></figcaption></figure>



**Minor bug fixes and performance improvements.** The team has been working hard to improve the robustness and performance of the platform.

***

## Release 2026-06-10

**What's New in This Sprint**

**ChIP-seq and ATAC-seq Analysis Have Arrived** The wait is over. Run ChIP-seq and ATAC-seq analyses directly in Mithrl, no detours required. Import your datasets from the same screen you already know, and the platform handles the rest: automated quality control, processing, all of it. Raw data to results, faster than ever.

<div align="center"><figure><img src="../.gitbook/assets/Screenshot 2026-06-10 at 11.44.09 AM.png" alt=""><figcaption></figcaption></figure></div>

**Your Datasets Now Come With Ideas** Create a new dataset and Mithrl gets to work immediately, inferring your research goal and surfacing up to three suggested questions to kickstart your analysis. Less staring at a blank screen, more discovering.

<figure><img src="../.gitbook/assets/Screenshot 2026-06-10 at 11.46.20 AM.png" alt=""><figcaption></figcaption></figure>

**Data Visualizations, Now Fully Interactive by Default** Every new visualization ships as an interactive chart. Drag to pan, scroll to zoom, go full-screen when you want the big picture. Annotations leveled up too: rectangle and lasso selection, shaded regions, and a clear-all option (with confirmation, because we've all been there). Note the Toggle New Charts Renderer setting is no longer available.

**Platform Updates:** Fresher Under the Hood Everything is now fully up to date, which means a more stable, secure, and consistent experience every day. We also made internal improvements that help us catch and squash issues before they ever reach you.

**Performance:** Built for the Heavy Lifting Faster, more reliable, and ready for your biggest workloads. Significant infrastructure improvements mean fewer slowdowns when demand spikes, so your analyses keep humming along.

**Security:** Routine security patches

***

## Release 2026-05-28

**What's New in Release 2026-05-08**

**Migration to the New Dataset Format**

If you have existing datasets created in the older Mithrl v1.0, we've started migrating user accounts to the new Mithrl v2 platform. Users have the option to use Mithrl v1 or v2. To toggle between v1 and v2, users should go to Settings>Toggle Analysis Mode.

<figure><img src="../.gitbook/assets/Screenshot 2026-06-09 at 12.23.10 PM.png" alt=""><figcaption></figcaption></figure>

We suggest you start to use only Mithrl v2 as we plan to retire Mithrl v1 soon. The advantages of Mithrl v2 include:

* collaborative planning of analysis
* faster data analysis
*

**A New Interactive Charting Experience (Opt-In Preview)**

A new charting engine makes it easier to explore, annotate, and share your data, with interactive zoom, lasso selection, custom styling, and one-click export. It is available as an opt-in preview now and will become the default in a future release. To unlock this feature go to Settings>Toggle New Charts Renderer.

<figure><img src="../.gitbook/assets/Screenshot 2026-06-09 at 12.23.59 PM.png" alt=""><figcaption></figcaption></figure>

**More Resilient Dataset Processing**

Importing datasets is now more reliable, even when input files have minor gaps or inconsistencies.

**Platform Stability and Infrastructure**

We've made behind-the-scenes improvements to how we test and deploy updates, so you can expect a more stable and reliable platform going forward.

{% include "../.gitbook/includes/support-footer.md" %}
