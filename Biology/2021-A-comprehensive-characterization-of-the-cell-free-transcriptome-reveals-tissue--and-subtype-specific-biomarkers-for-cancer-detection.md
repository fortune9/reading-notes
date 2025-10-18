A comprehensive characterization of the cell-free transcriptome reveals
tissue- and subtype-specific biomarkers for cancer detection
================
Mar 26, 2023

-   [Paper](#paper)
-   [Notes](#notes)
    -   [Sample summary](#sample-summary)
    -   [Main findings](#main-findings)

## Paper

-   title: A comprehensive characterization of the cell-free
    transcriptome reveals tissue- and subtype-specific biomarkers for
    cancer detection
-   link: <https://doi.org/10.1038/s41467-021-22444-1>

### Resources

**Datasets**
- **Primary cfRNA sequencing cohort**: CCGA (Circulating Cell-free Genome Atlas) trial (NCT02889978) – controlled-access via GRAIL / data access committee.
- **Gene expression matrices & processed counts**: GEO accession (PLACEHOLDER e.g., GSE17xxxx) – insert actual once verified from Data Availability.
- **Clinical annotations**: Available under controlled access (patient consent restrictions) – request through trial portal.

**Code / Pipelines**
- **Analysis scripts**: (PLACEHOLDER) If authors deposited (GitHub link to preprocessing, tissue-of-origin classifier) add here.
- **Example tissue-of-origin model approach**: Random forest / LDA (as described) – replicate with scikit-learn using DCB gene panel.

**Supplementary**
- **Clinical trial registration**: NCT02889978
- **DOI landing**: https://doi.org/10.1038/s41467-021-22444-1
- **Supplementary information**: Linked on publisher site (tables listing DCB genes, expression filters).

## Notes

### Sample summary

stage III breast \[n = 46\], lung \[n = 30\]) and non-cancer (n = 89)
participants from the Circulating Cell-free Genome Atlas (NCT02889978)

### Main findings

-   Of 57,820 annotated genes, 39,564 (68%) are not detected in cfRNA
    from non-cancer individuals

-   Within these low-noise regions, we identify tissue- and
    cancer-specific genes, defined as “dark channel biomarker” (DCB)
    genes, that are recurrently detected in individuals with cancer.

-   12 DCB genes were identified in lung cancer samples (SLC34A2,
    GABRG1, ROS1, AGR2, GNAT3, SFTPA2, MUC5B, SFTA3, SMIM22, CXCL17,
    BPIFA1, WFDC2), and 8 DCB genes were identified in breast cancer
    samples (CSN1S1, FABP7, OPN1SW, SCGB2A2, LALBA, CASP14, KLK5, WFDC2)

-   DCB levels in plasma correlate with tumor shedding rate and RNA
    expression in matched tissue

-   cfRNA may be released into the blood through mechanisms other than
    cell death, such as exosome-mediated signaling by living cells13.
    Consequently, tumor-derived cfDNA and cfRNA may originate from
    distinct cell populations within the tumor microenvironment
