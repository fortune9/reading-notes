Strategies for minimal residual disease detection: current perspectives
================
Oct 17, 2025

  - [Paper](#paper)
      - [Abstract](#abstract)
  - [Notes](#notes)
      - [Main ideas](#main-ideas)

## Paper

  - **Title**: Plasma cell-free RNA profiling distinguishes cancers from
    pre-malignant conditions in solid and hematologic malignancies
  - **Authors**: Peng Xia, Mengping Long, Yaping Liu, Wei Guo, Jiayi
    Zhou, Hui Chen, Junru Chen, Zhenxing Liang, Ping Hu, Jun Chen,
    Yuanda Wang, Xianghuo He, Jin Xu, Weixing Zhang, Xin Jin, Xiaoli
    Zhu, Yi Shi, Xiaoling Zhang, Jian Chen, Kun Qian, Jingqun Tang,
    Xiangmin Tong, Pengpeng Zhang, Pengcheng Yang, Yajun Yang, Chaojun
    Duan, Yuchen Han, Cheng Fang, Rong Hua, Peina Xie, Mingxiang Ye, Kun
    Huang, Jingxia Li, Xiaohui Bian, Yen-Ling Chiu, Qian Sun, Baohong
    Gu, Mulin Jun Li, Mingyao Li, Meng Yang, Yu Lu & Pengyuan Wang
  - **Journal**: npj Precision Oncology
  - **Publication Date**: April 13, 2022
  - **DOI**: <https://doi.org/10.1038/s41698-022-00270-y>
  - **Type**: Research Article
  - **URL**: <https://www.nature.com/articles/s41698-022-00270-y>

### Resources

**Datasets**
- **Discovery cohort**: 245 cancer patients (10 solid tumor types + 4 hematologic malignancies), 124 premalignant, 200 healthy. Sequencing repository accession (PLACEHOLDER GEO/SRA e.g., GSE18xxxx) – fill in after verifying Data Availability.
- **Validation cohort**: Independent 184-individual cohort (20 HCC, 9 MM, 10 NC + others) – add accession when public.
- **Processed count matrices / expression tables**: Supplementary Data (publisher site) – download and archive locally if reused.

**Code**
- **Classification pipeline (Random Forest / LDA)**: (PLACEHOLDER GitHub repo if authors released). Re-implement via scikit-learn using normalized TPM matrix restricted to selected tissue-specific cfRNA features.
- **Feature list generation**: Derive DCB (dark channel biomarker) genes via low-noise filtering + recurrence thresholds (see Methods).

**Supplementary**
- **DOI landing**: https://doi.org/10.1038/s41698-022-00270-y
- **Supplementary Tables**: Tissue-specific cfRNA biomarker lists (HCC vs MM) for reproduction of panel.
- **Clinical annotations**: Likely controlled access due to identifiable patient data; request through corresponding author or repository governance.

### Abstract

Cell-free RNA (cfRNA) in blood plasma holds great promise for
non-invasive cancer detection. However, it remains unclear whether cfRNA
can distinguish cancers from pre-malignant conditions. Here, we profiled
plasma cfRNA from 245 cancer patients spanning 10 solid tumor types and
4 hematologic malignancies, 124 patients with pre-malignant conditions,
and 200 healthy individuals. We developed a machine learning model that
distinguished cancers from healthy controls with high accuracy (AUC =
0.98). Importantly, the model achieved strong performance in
distinguishing cancers from pre-malignant conditions (AUC = 0.94),
including common conditions such as thyroid nodules, colorectal polyps,
and lung nodules. We identified tissue- and cancer-specific cfRNA
signatures, including transcripts from tumor-associated genes and
transcription factors. The model’s performance was validated in an
independent cohort of 184 individuals. Our findings demonstrate that
cfRNA profiling can effectively distinguish cancers from pre-malignant
conditions and identify tumor tissue-of-origin, supporting its potential
clinical utility for early cancer detection.

## Notes

### Main ideas

  - Two methods are currently preferred for measurable residual disease
    (MRD) evaluation in many centers: multiparameter flow cytometry and
    real-time quantitative PCR

  - Additional methods such as next-generation sequencing and digital
    PCR are under investigation, in an attempt to increase the
    sensitivity and thus allowing the detection of small clones

  - MRD positivity after chemotherapy is associated with negative
    prognosis, and the reappearance of MRD during follow-up allows
    impending relapse to be identified and consequently enables early
    intervention

  - Frequently, a founding clone can be identified at diagnosis and
    additional small subclones can be detected only by very sensitive
    methods

  - MRD indicates the presence of leukemia cells down to the levels of
    1:10^4 to 1:10^6 white blood cells, compared with 1:20 in
    morphology-based measurement

  - Real-time PCR represents, so far, the gold standard for MRD
    detection

  - Marker for molecular MRD:
    
      - Fusion transcript in core binding factor (CBF): CBFB-MYH11 and
        RUNX1-RUNX1T1
      - NPM1 mutation
      - PML-RARA
      - The Wilms’ tumor gene (WT1) overexpression
      - IDH1/IDH2 mutations

  - Multiparameter flow cytometry (MFC): based on a panel of antibodies
    targeting early markers such as CD34 and CD117, markers of
    myeloid-lineage such as CD33, and myeloid differentiation antigens
    like CD11b, CD13, CD14, CD15 or lymphoid antigens including CD2,
    CD7, CD19, or CD56

  - New techniques are on the horizon for the detection of small
    leukemic clones. A promising approach is based on digital PCR. It is
    estimated that ddPCR can detect up to 0.001% mutated allele
    frequency

  - Next-generation sequencing: Since there is a high degree of
    genotypic and phenotypic heterogeneity in AML, each patient should
    have a unique signature to be used to track MRD after therapy. The
    main disadvantages of using NGS are shorter read length and the fact
    that its ability to detect MRD depends on the depth of sequencing
    and on the type of computational algorithms used.
