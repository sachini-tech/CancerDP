# CancerDP: Prioritization of Anticancer Drugs Using Genomic Features of Cancer Cells

Welcome to the official repository for CancerDP, a webserver for predicting the priority and potency of anticancer drugs against a cancer cell line using its genomic features. This resource is designed to support researchers working in cancer biology, pharmacogenomics, and personalized medicine.

Web Server:  https://webs.iiitd.edu.in/raghava/cancerdp/

ZENODO : https://doi.org/10.5281/zenodo.20072079

## Citation

Gupta, S., Chaudhary, K., Kumar, R., Gautam, A., Nanda, J. S., Dhanda, S. K., Brahmachari, S. K., & Raghava, G. P. S. (2016).
Prioritization of anticancer drugs against a cancer using genomic features of cancer cells: A step towards personalized medicine.
Scientific Reports, 6, 23857. https://doi.org/10.1038/srep23857


## About the Webserver

CancerDP is the first publicly available webserver for anticancer drug prioritization based on genomic features of cancer cell lines. It addresses the long-standing gap where several large-scale pharmacogenomics studies existed but no tool was available publicly in the form of a web service or software. CancerDP enables researchers to predict growth inhibition of 24 anticancer drugs against a cancer cell line using its mutation, variation, gene expression, and copy number variation (CNV) profiles.

The models are built using the Cancer Cell Line Encyclopedia (CCLE) dataset covering:

* Hybrid capture sequencing of 1,667 genes in 448 cell lines
* RMA-normalized mRNA expression data of 17,627 genes in 488 cell lines
* CNV data for 21,217 genes across 418 cell lines
* IC50 drug sensitivity data for 24 anticancer drugs across 504 cell lines


## Key Features

Drug Coverage

* 24 anticancer drugs analyzed (16 kinase inhibitors, 3 cytotoxic drugs, 5 other targeted therapies)
* Drugs include launched, Phase I–III, and preclinical candidates
* Covers targets including EGFR, HER2, MEK, ALK, c-MET, RAF, HDAC, MDM2, HSP90, Topoisomerase I, and Beta-tubulin

Prediction Models

* SVM (Support Vector Machine) regression models developed for each of the 24 drugs
* Five model types based on different genomic features: mutation, variation, expression, CNV, and hybrid
* Best average Pearson Correlation Coefficient (PCC) of **0.78** achieved by hybrid models
* Outperforms previous CCLE models (max average correlation 0.43)
* Top individual drug correlations reach 0.90 (e.g., LBW242, PLX4720)

Genomic Feature Types Supported

* Mutation (binary: mutated = 1, wild-type = 0; MAF/ANNOVAR/VCF input)
* Variation (binary: variant present = 1, absent = 0)
* Gene expression (RMA-normalized log2 values from Affymetrix U133 Plus 2.0 arrays)
* Copy Number Variation (log2 ratio of cancer vs. normal gene copy numbers)
* Hybrid (combination of mutation + expression + CNV)

Feature Selection Methods

* CfsSubsetEval algorithm (WEKA) — reduces features to an average of 43–80 genes per drug
* F-stepping technique — further reduces to an average of 20–34 genes per drug
* Correlation-based selection (expression vs. IC50) — top 50 correlated genes


## Overview

CancerDP provides the following tools:

* **Prioritization Module** — Predicts drug effectiveness from raw NGS data (VCF/ANNOVAR input) or manually entered genomic profiles
* **Drug Calculator** — Probabilistic module to find the contribution of each individual gene towards drug resistance or sensitivity; works with mutation, variation, expression, and CNV data
* **Signature Module** — Identifies important genes for each drug; displays average IC50 in mutated vs. wild-type cell lines (mutation/variation) or average expression in resistant vs. sensitive cell lines (expression/CNV)
* **Expression & CNV Module** — Displays genes with their average expression/CNV in resistant and sensitive cell lines for any selected drug


### Key Biological Findings

* Panobinostat is the most promiscuous anticancer drug — effective against >99% of cell lines tested
* Only 5 of 24 drugs (17AAG, Irinotecan, Paclitaxel, Panobinostat, Topotecan) are sensitive against >50% of cell lines
* Tissue-specific drug response observed: Irinotecan is effective against 100% of Autonomic Ganglia and soft-tissue cell lines; Topotecan is effective against 87% of hematopoietic and lymphoid cell lines
* TP53, KRAS, and MAP3K1 mutations significantly affect sensitivity across 10 drugs
* SMARCA4 epigenetic factor mutations linked to resistance in multiple drug types
* Gene expression-based models (average PCC = 0.73) outperform all other single-feature models


### Model Performance Summary

| Feature Type | Average PCC |
|---|---|
| Mutation | 0.43 |
| Variation | 0.52 |
| CNV | 0.55 |
| Expression | 0.73 |
| Hybrid | **0.78** |
| CCLE (prior study) | 0.42 |


### Limitations

* Drug toxicity profiles are not incorporated into the prioritization models
* Models are trained on cell line data and may not fully reflect in vivo patient tumor behavior
* No single clear-cut biomarker discriminates all drug-resistant from drug-sensitive cell lines
* Mutation-based models show the weakest performance compared to expression-based models


## Applications

* Personalized anticancer drug selection based on a patient tumor's genomic profile
* Identification of genomic biomarkers of drug resistance and sensitivity
* Prioritizing drugs for specific cancer tissue types
* Machine learning benchmarking for pharmacogenomics research
* Understanding tissue-specific and drug-specific genomic vulnerability patterns


## Contact & Authors

Prof. Gajendra P. S. Raghava
raghava@iiitd.ac.in
http://webs.iiitd.edu.in/raghava/

Developed at:
Bioinformatics Centre, CSIR-Institute of Microbial Technology, Sector 39A, Chandigarh, India
CSIR-Institute of Genomics and Integrative Biology, Mathura Road, New Delhi — 110007, India


## License

This webserver is distributed under the
Creative Commons Attribution License (CC BY 4.0)

