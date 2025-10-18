# 2020 - NanoVar: accurate characterization of patients’ genomic structural variants using low-depth nanopore sequencing

**Authors**: (Add full author list – from PDF)  
**Journal**: Genome Biology  
**Publication Date**: 2020 (Exact date: PLACEHOLDER)  
**DOI**: https://doi.org/10.1101/662940 (bioRxiv preprint) / Final journal DOI (Genome Biol 21:56) https://doi.org/10.1186/s13059-020-01975-8  
**Type**: Research Article / Structural Variant Calling Method  
**URL**: https://doi.org/10.1186/s13059-020-01975-8  
**Keywords**: structural variants, long-read sequencing, Oxford Nanopore, low-depth, neural network, variant calling, genome analysis

## Abstract (Condensed)
NanoVar introduces a neural-network–enhanced structural variant (SV) caller optimized for low-depth (~8×) Oxford Nanopore long-read whole-genome sequencing. It leverages split-read/discordant alignment signatures and per-event read support features passed through a trained classifier to distinguish true SVs from artifacts, enabling accurate detection while reducing sequencing cost barriers. Benchmarking shows competitive or superior sensitivity and precision versus existing tools at reduced depth, expanding feasibility of clinical and population SV characterization.

## Problem & Motivation
- High sequencing depth requirements of long-read SV callers limit clinical adoption and cost-sensitive population studies.
- Need robust SV detection at modest coverage without sacrificing precision, especially for heterogeneous patient samples.
- Existing methods often trade off sensitivity for specificity or require complex multi-tool consensus pipelines.

## Methodology Overview
1. **Input**: Basecalled ONT FASTQ → alignment to reference (e.g., minimap2). 
2. **SV Candidate Discovery**: Parsing CIGAR, split alignments, soft clips, discordant regions to propose deletions, insertions, inversions, translocations. 
3. **Feature Extraction**: For each candidate: read depth support, breakpoint consistency, alignment quality metrics, local mapping entropy, size distribution features. 
4. **Neural Network Classification**: Feed engineered feature vector into trained NN to assign probability of true SV. 
5. **Filtering & Output**: Threshold probability → VCF with annotated SVs (size, type, coordinates, support). 
6. **Benchmarking**: Compare against truth sets (e.g., GIAB) and alternative tools at 8× coverage.

## Key Findings
- Maintains high precision at low coverage (≈8×), mitigating false positives common in noisy long-read data.
- Detects broad SV spectrum (>50 bp) including insertions/deletions/inversions with favorable F1 scores.
- Performance degrades gracefully below 8×, still useful for exploratory screening.
- Neural network component improves discrimination over rule-based heuristics alone.
- Cost reduction: Lower depth requirement reduces per-sample sequencing expense.

## Performance Metrics (Illustrative)
- Coverage target: ~8× ONT. 
- Sensitivity & Precision: Competitive with higher-depth reliant tools (exact percentages: PLACEHOLDER – insert from paper tables). 
- False discovery rate reduced after NN filtering vs baseline candidate set.

## Resources
### Datasets
- **Simulation datasets & ground truths (Zenodo)**: https://doi.org/10.5281/zenodo.3569479 (all simulated SV sets + truth VCFs) [58]
- **Benchmark sample NA12878 PacBio dataset**: ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/technical/working/20131209_na12878_pacbio/si/ (Coriell NA12878 PacBio long reads) [29]
- **High-confidence SV benchmark (GIAB NA12878)**: ftp://ftp-trace.ncbi.nlm.nih.gov/giab/ftp/technical/svclassify_Manuscript/Supplementary_Information/ (truth SV set) [30]
- **Genome in a Bottle (GIAB) references**: Additional GIAB sample resources via NIST/NCBI FTP.
- **Clinical patient ONT & Illumina WGS (patients 1 & 2)**: dbGaP accession phs001847.v1.p1 → https://www.ncbi.nlm.nih.gov/projects/gap/cgi-bin/study.cgi?study_id=phs001847.v1.p1 [59]
- **Training data for NN**: Derived from simulated + empirical ONT alignments (features documented; simulation source above). 

### Code Repositories
- **Bioconda package**: https://anaconda.org/bioconda/nanovar (conda install)
- **PyPI**: https://pypi.org/project/nanovar (Python package index)
- **GitHub (source code)**: https://github.com/benoukraflab/nanovar [56]
- **Zenodo source archive**: https://doi.org/10.5281/zenodo.3569496 [57]
- **License**: GNU GPL v3
- **Scripts directory (data gen & analysis)**: In GitHub repo under `scripts/` [56]
- **Alignment prerequisite**: minimap2 (https://github.com/lh3/minimap2)
- **External dependency**: BEDTools (required pre-installation for interval operations)
- **Optional comparison tools**: Sniffles, SVIM, NanoSV (benchmark replication)

### Supplementary / Documentation
- **Preprint**: https://doi.org/10.1101/662940
- **Final Article**: https://doi.org/10.1186/s13059-020-01975-8
- **Supplementary Material**: Tables with per-tool precision/recall, feature definitions, NN architecture hyperparameters.
- **Model reproducibility**: Provide seed, architecture diagram (Supplementary Figure; include path when archived).

## Implementation Notes
- Recommended alignment flags: minimap2 `-x map-ont -a` to preserve CIGAR for SV parsing.
- Operating system: Linux x86_64; Python ≥ 3.6.
- Dependency prerequisites: BEDTools, minimap2, standard scientific Python stack.
- Installation example (conda): `conda install -c bioconda nanovar`.
- Feature extraction must normalize by local coverage to remain robust across depth fluctuations.
- Neural net likely shallow (few dense layers) to avoid overfitting given limited labeled SV events.
- Insert size and breakpoint uncertainty captured via soft-clipped segment statistics.

## Limitations & Caveats
- Low-depth ONT may miss very small (<50 bp) or complex multi-breakpoint events.
- Drop in sensitivity for tandem duplications and translocations compared to high-depth pipelines.
- Neural network model performance tied to representativeness of training examples; domain shift (different chemistries / flow cells) may require retraining.
- Homopolymer-associated indel errors could inflate insertion calls if not filtered.

## Future Directions
- Domain adaptation for new ONT chemistry (R10.x) using transfer learning.
- Integration with phasing tools to correlate SVs with haplotypes.
- Joint calling combining short- and long-read evidence for improved breakpoint resolution.
- Real-time streaming SV detection during sequencing run at partial coverage.
- Containerized workflow (Nextflow/Snakemake) for clinical lab compliance.

## Personal Notes
- Consider benchmarking NanoVar vs latest Sniffles2 at similar coverage to validate relative gains.
- For cost-sensitive projects, pilot at 6× to evaluate minimal acceptable depth threshold.
- Explore feature importance from NN (e.g., SHAP) to identify potential overfit to specific error patterns.

