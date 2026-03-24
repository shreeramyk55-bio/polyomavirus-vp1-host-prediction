# VP1 Physicochemical Features Predict Polyomavirus Host Specificity Across Vertebrates

**Author:** Shreeram Y K  
**ORCID:** https://orcid.org/0009-0006-1579-7202  
**Contact:** shreeramyk55@gmail.com

## Overview
Computational study predicting polyomavirus host specificity from VP1 capsid protein features. 116 VP1 sequences from NCBI, 26 physicochemical features, 3 ML models (SVM best at 77.6%).

## Key Results
- Best model: SVM with 77.6% cross-validated accuracy
- Top predictor: Proline content (pct_P)
- 23 of 26 features statistically significant (p < 0.05)
- Docking energies: -3.6 to -5.6 kcal/mol

## Files
| File | Description |
|------|-------------|
| vp1_metadata.csv | 116 sequences with NCBI accessions and hosts |
| vp1_sequences.fasta | VP1 protein sequences in FASTA format |
| sequence_features.csv | 26 physicochemical features per sequence |
| statistical_tests.csv | Kruskal-Wallis test results |
| docking_results.csv | AutoDock Vina binding energies |
| Fig1-Fig10 PNGs | All publication figures at 300 DPI |

## Tools Used
Python 3.13, BioPython 1.83, scikit-learn 1.4, XGBoost 2.0, MEGA 12, PyMOL 2.5, AutoDock Vina 1.1.2

## Crystal Structures Used
PDB IDs: 3BWR, 4MJ0, 4MJN, 1CN3, 1SIE, 1SID, 1VPS, 4FMG, 4POF, 4POT, 4X0V, 3S7V

## License
MIT License - Copyright (c) 2026 Shreeram Y K
