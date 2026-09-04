## Analysis notebook summary

The main analysis is in [`notebooks/analysis.qmd`](notebooks/analysis.qmd). It analyzes single-cell RNA-sequencing data from nine Cell Ranger samples (`GSM8403163`–`GSM8403171`) representing trisomy 21 (T21) and control embryonic samples.  Its central questions are which cell types and subclusters show senescence-associated profiles, how those profiles differ between T21 and controls, and which biological pathways distinguish the genotypes. When enabled, it writes marker and enrichment tables (Excel) and figures (PNG) to the repository root, including cluster marker files, senescence/cluster plots, and cluster 2 T21-versus-control GO/KEGG results.

The workflow is:

1. Read the sample sheet and import each sample as a Seurat object.
2. Merge the samples, calculate mitochondrial read percentages, inspect quality-control metrics, and retain cells with 500–10,000 detected features and less than 25% mitochondrial reads.
3. Normalize with SCTransform, run PCA and UMAP, and integrate samples with reciprocal PCA (RPCA). Neighbor graphs and clusters are generated at several resolutions; the analysis uses the lower-resolution clustering as the broad grouping and the higher-resolution clustering to investigate subpopulations.
4. Identify marker genes for clusters and genotype (T21 versus control), add HGNC gene descriptions, and export marker tables for downstream interpretation.
5. Score cells for senescence using AUCell and a combined senescence gene set from the Mayo Clinic marker list. Senescence scores are visualized across genotypes and clusters.
6. Assign putative cell types using AUCell scores against fetal-lung gene sets from the Descartes reference. These annotations are used to ask which cell types are represented in, and contribute to, senescent populations.
7. Focus on broad cluster 2, which is split into RPCA subclusters (especially 5, 11, 13, 21, and 22). The notebook compares T21 and control marker genes within subclusters 5, 11, and 21, examines senescence-score differences with Kruskal–Wallis tests, and produces dot plots of shared and subcluster-specific markers.
8. Perform pathway analysis on ranked and significant marker lists using Gene Ontology, KEGG, Reactome, BioCarta, PID, WikiPathways, and fetal-lung cell-type gene sets. Both over-representation analysis and GSEA are used, with results visualized as dot plots and heat plots.
