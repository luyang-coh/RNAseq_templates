### Order to Run Scripts ###

1) [alignment / quantification script]

2) salmon_sailfish_reformat.R

3) qc.R

4) DEG_goseq.R

### Dependencies (some optional) ###

*Alignment / Quantification*

Salmon: https://combine-lab.github.io/salmon/
Sailfish: http://www.cs.cmu.edu/~ckingsf/software/sailfish/

*Differential Expression*

edgeR: https://bioconductor.org/packages/release/bioc/html/edgeR.html

limma-voom: https://bioconductor.org/packages/release/bioc/html/limma.html

DESeq2: https://bioconductor.org/packages/release/bioc/html/DESeq2.html

qvalue: https://bioconductor.org/packages/release/bioc/html/qvalue.html

*Visualization*

gplots: https://cran.r-project.org/web/packages/gplots/index.html

heatmap.3: https://github.com/obigriffith/biostar-tutorials/blob/master/Heatmaps/heatmap.3.R

heatmap.3 example: https://www.biostars.org/p/18211/

*Gene Set Enrichment*

goseq: http://bioconductor.org/packages/release/bioc/html/goseq.html

### Parameter Values ###
| Parameter | Value|
|---|---|
|comp_name	| Name of differential expression comparison (used to name output file)
|plot_groups | Names of columns in *sample_description_file* to be plotted in QC and differential expression plots.  Use commas to plot multiple groups|
|deg_groups|Names of columns in *sample_description_file* to be plotted in QC and differential expression plots.  Use commas to include multiple variables (for multivariate model or gene list filtering)|
|treatment_group|Treatment group for primary variable; enter *continuous* for a continuous variable and a correlation will be provided instead of a fold-change value.|
|Raw_Code_PC|Path to output folder for most result|
|Result_Folder|Path to output folder for selected, final results|
|Reads_Folder_MAC|Path to Reads for Salmon/Sailfish Quantification|
|pvalue_method|Method to Calculate P-value.  Can be *edgeR*, *limma-voom*, *DESeq2*, *lm* (linear regression), or *aov* (ANOVA)|
|fdr_method|Method to Calculate FDR.  Can be *BH* (Benjamini and Hochberg),*q-value*, or *q-lfdr*|
|genome|Name of genome build|
|Threads|Number of Threads for TopHat Alignment|
|gene_annotation_file|Transcript Information File (defined from .fasta header for GENCODE genes)|
|sample_description_file|Name of Sample Description File|
|total_counts_file|Name of File to Contain Total Read Counts|
|aligned_stats_file|Name of File to Contain Aligned and Exonic Read Counts|
|cluster_distance| Distance metric for dendrogram.  Can be *Euclidean* or *Pearson_Dissimilarity*|
|gene_tpm_file|Name of File to Contain TPM Expression Values per Gene (Sum of Transcript TPM)|
|gene_counts_file|Name of File to Contain Read Counts Per Gene (Sum of Transcript Counts)|
|transcript_tpm_file|Name of File to Contain TPM Expression Values per Transcript (unlike TopHat_Workflow, these are linear with rounding occuring later)|
|transcript_counts_file|Name of File to Contain Read Counts Per Transcript|
|rpkm_expression_cutoff|Rounding Value for TPM (minimum reliable expression level)|
|minimum_fraction_expressed|Minimum fraction of samples with expression above *rpkm_expression_cutoff*. Filter for differential expression anaylsis.|
|fold_change_cutoff|Minimum fold-change difference to consider a gene differentially expressed|
|cor_cutoff|If using a continuous variable, minimum absolute correlation to consider a gene differentially expressed|
|pvalue_cutoff|Maximum p-value to consider a gene differenitally expressed|
|fdr_cutoff|Maximum FDR to consider a gene differentially expressed|
|sec_fold_change_cutoff|If comparing two gene lists, fold-change threshold for list you want to filter out|
|sec_cor_cutoff|If comparing two gene lists and using a continuous variable, minimum absolute correlation to consider a gene differentially expressed|
|sec_pvalue_cutoff|If comparing two gene lists, p-value threshold for list you want to filter out|
|sec_fdr_cutoff|If comparing two gene lists, FDR threshold for list you want to filter out|
|min_length_kb|Minimum length of gene to consider for differential expression anlysis (in kilobases)|
|run_goseq| Run goseq?  It is useful to leave this as 'no' initially, and then switch to 'yes' after optimizing differential expression parameters|
|interaction| Method for comparing an interaction of two variables.  Can be *model*, *filter-overlap*, or *no*|
|secondary_trt| If comparing two gene lists, this is treatment group for the list that you want to filter out; enter *continuous* for a continuous variable and a correlation will be provided instead of a fold-change value (also converts second variable from factor to numeric, even if interaction is set to *no*)|