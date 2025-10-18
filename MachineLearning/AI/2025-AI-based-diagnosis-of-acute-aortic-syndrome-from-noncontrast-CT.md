# AI-based diagnosis of acute aortic syndrome from noncontrast CT

**Date**: Oct 18, 2025

## Paper

- **Title**: AI-based diagnosis of acute aortic syndrome from noncontrast CT
- **Authors**: Yujian Hu, Yilang Xiang, Yan-Jie Zhou, Yangyan He, Hongkun Zhang, and colleagues
- **Journal**: Nature Medicine
- **Publication Date**: August 20, 2025
- **DOI**: https://doi.org/10.1038/s41591-025-03916-z
- **Type**: Research Article
- **URL**: https://www.nature.com/articles/s41591-025-03916-z

### Abstract

Acute aortic syndrome (AAS) is a life-threatening cardiovascular emergency that requires rapid diagnosis and treatment. Current diagnostic approaches rely primarily on contrast-enhanced CT angiography (CTA), which may delay diagnosis and cannot be used in patients with contraindications to contrast agents. This study presents iAorta, an artificial intelligence-based real-time early warning system designed to assist radiologists and emergency department (ED) clinicians in accurately and rapidly detecting AAS using noncontrast CT scans alone. The system was developed using 3,350 consecutive patients who underwent aorta CTA scans at FAHZU (Zhejiang, China) between 2016 and 2020. iAorta was designed to automatically analyze noncontrast CT scans from patients presenting with acute chest pain and provide early warnings of AAS to radiologists when necessary. In a large-scale real-world study involving 137,525 patients, iAorta demonstrated consistently high performance across various noncontrast CT protocols, offering a crucial tool for early detection and potentially improving patient outcomes in emergency settings.

### Resources

#### Datasets
- **Training cohort**: 3,350 consecutive patients with aorta CTA scans (both arterial and noncontrast phase CT series) from FAHZU (Zhejiang, China), 2016-2020
- **Real-world validation**: 137,525 patients across various noncontrast CT protocols
- **Study data**: 14,436 data samples used for system validation
- **Data availability**: Check the paper's Data Availability section for specific access information

#### Code Repositories
- **Code availability**: Check the paper's Code Availability section at https://www.nature.com/articles/s41591-025-03916-z for potential GitHub repository or code sharing information
- **iAorta system**: AI-based real-time early warning system implementation

## Notes

### Main Ideas

- **Clinical problem**: Acute aortic syndrome (AAS) is a life-threatening emergency
  - Includes aortic dissection (AD), intramural hematoma (IMH), and penetrating atherosclerotic ulcer (PAU)
  - Requires rapid diagnosis for timely intervention
  - Current gold standard (contrast-enhanced CTA) has limitations:
    - Requires contrast agents (contraindicated in some patients)
    - May cause delays in diagnosis
    - Not always immediately available

- **iAorta system**: AI-based solution using noncontrast CT
  - Real-time early warning system for AAS detection
  - Works with noncontrast CT scans alone
  - Provides automated analysis of chest pain patients
  - Alerts radiologists and ED clinicians when AAS is suspected

- **Training approach**:
  - Deep learning model trained on both arterial and noncontrast phase CT series
  - Learns image features of AAS on noncontrast CT
  - Trained on 3,350 consecutive patient cases

- **Large-scale validation**:
  - Real-world study with 137,525 patients
  - Demonstrated high performance across various noncontrast CT protocols
  - Robust across different imaging settings and patient populations

### Methodology

- **Study design**: Retrospective development and prospective validation
- **Development cohort**: 3,350 patients from FAHZU (2016-2020)
- **Imaging modality**: Noncontrast CT (versus traditional contrast-enhanced CTA)
- **AI approach**: Deep learning-based real-time warning system
- **Validation**: Large-scale real-world study (n = 137,525)
- **Target conditions**: All AAS subtypes (AD, IMH, PAU)

### Key Findings

1. **High performance**: iAorta demonstrated consistently high diagnostic performance in detecting AAS from noncontrast CT scans

2. **Robustness**: System worked well across various noncontrast CT protocols, demonstrating generalizability

3. **Large-scale validation**: Successfully validated on 137,525 patients in real-world settings

4. **Clinical utility**: 
   - Enables AAS detection without contrast agents
   - Provides real-time warnings to clinicians
   - Can be used in patients with contrast contraindications
   - Potentially reduces time to diagnosis

5. **Comprehensive detection**: Capable of identifying different AAS subtypes (AD, IMH, PAU)

### Clinical Significance

- **Emergency medicine**: Critical tool for ED physicians managing acute chest pain
- **Patient safety**: Enables diagnosis in patients who cannot receive contrast agents (e.g., renal insufficiency, contrast allergies)
- **Time-critical**: Real-time warning system can accelerate diagnosis and treatment initiation
- **Resource optimization**: Can help prioritize patients needing urgent CTA
- **Accessibility**: Noncontrast CT is more widely available and faster than CTA

### Potential Applications

- Emergency department triage for acute chest pain patients
- Screening tool before contrast-enhanced imaging
- Alternative diagnostic approach for patients with contrast contraindications
- Real-time decision support for radiologists
- Population-level surveillance in high-risk groups

### Advantages Over Current Methods

1. **No contrast required**: Eliminates risks and contraindications associated with contrast agents
2. **Faster**: Noncontrast CT is quicker to perform than CTA
3. **More accessible**: Noncontrast CT is available in more settings
4. **Real-time analysis**: AI provides immediate alerts
5. **Consistent performance**: Less dependent on reader experience

### Future Directions

- Prospective clinical trials to assess impact on patient outcomes
- Integration into clinical workflows and PACS systems
- External validation in diverse healthcare settings globally
- Assessment of cost-effectiveness
- Potential expansion to other acute cardiovascular conditions
- Development of mobile or point-of-care versions

### Technical Considerations

- Model trained on comprehensive dataset with both contrast and noncontrast phases
- Validated across multiple CT protocols (demonstrates robustness)
- Real-time processing capability for ED settings
- Designed to work as decision support tool (not replacement for clinical judgment)
