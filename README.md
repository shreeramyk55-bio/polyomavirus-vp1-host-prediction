# VP1 Physicochemical Features Predict Polyomavirus Host Specificity Across Vertebrates

**Author:** Shreeram Yeladahalli Kalayya  
**ORCID:** [0009-0006-1579-7202](https://orcid.org/0009-0006-1579-7202)  
**Contact:** shreeramyk@gmail.com  
---

## Introduction

Polyomaviruses are DNA viruses that infect a wide range of vertebrate hosts including humans, primates, rodents, birds, bats, and fish. The major capsid protein VP1 determines which host the virus can infect by binding to sialic acid receptors on host cells. Understanding what makes VP1 proteins specific to certain hosts is important for assessing the zoonotic risk of newly discovered polyomaviruses.

Several research groups have used machine learning to predict virus-host associations, but most of this work focused on RNA viruses. No one has built a host-prediction model specifically for polyomaviruses using VP1 protein features. This project fills that gap.

## Materials and Methods

### Data Collection
- 116 non-redundant VP1 protein sequences downloaded from NCBI Protein database
- 56 polyomavirus species across 6 host categories: Human (50), Rodent (22), Bird (16), Other_Mammal (14), Bat (11), Fish (3)

### Feature Extraction
- 26 physicochemical features calculated using BioPython ProtParam
- Features include: molecular weight, isoelectric point, GRAVY, aromaticity, instability index, secondary structure fractions, charge properties, and amino acid percentages

### Phylogenetic Analysis
- ClustalW alignment in MEGA 12
- Neighbor-Joining tree with 1000 bootstrap replicates (998 successful)
- Poisson substitution model

### Structural Analysis
- 12 X-ray crystal structures from RCSB PDB
- Visualized in PyMOL with rainbow coloring at 300 DPI
- PDB IDs: 3BWR, 4MJ0, 4MJN, 1CN3, 1SIE, 1SID, 1VPS, 4FMG, 4POF, 4POT, 4X0V, 3S7V

### Molecular Docking
- AutoDock Vina v1.1.2
- Ligand: sialic acid (Neu5Ac)
- Grid: 40 x 40 x 40 Angstroms, exhaustiveness = 8

### Machine Learning
- Three classifiers: Random Forest, XGBoost, SVM
- 80/20 train-test split with stratification
- 5-fold cross-validation
- Kruskal-Wallis tests for statistical significance

## Results

### Machine Learning Performance

| Model | Test Accuracy | CV Accuracy | CV SD |
|-------|:------------:|:-----------:|:-----:|
| **SVM (RBF)** | **70.8%** | **77.6%** | **7.5%** |
| Random Forest | 70.8% | 76.8% | 6.8% |
| XGBoost | 70.8% | 71.6% | 4.9% |
| Random baseline | 16.7% | 16.7% | - |

All models perform substantially above random chance (16.7%).

### Top 5 Most Important Features

| Rank | Feature | Importance |
|:----:|---------|:----------:|
| 1 | Proline content (pct_P) | 0.075 |
| 2 | Molecular weight | 0.072 |
| 3 | Proline count | 0.063 |
| 4 | Aromaticity | 0.060 |
| 5 | Glycine content (pct_G) | 0.059 |

### Statistical Significance
- 23 of 26 features differ significantly between host categories (Kruskal-Wallis p < 0.05)
- Most significant: proline content (H=54.21, p<0.001), glycine content (H=45.58, p<0.001)

### Molecular Docking

| Virus | PDB | Host | Binding Energy |
|-------|:---:|------|:--------------:|
| WU Polyomavirus | 4POF | Human | -5.6 kcal/mol |
| B-lymphotropic PyV | 3S7V | Primate | -5.1 kcal/mol |
| Merkel Cell PyV | 4FMG | Human | -4.7 kcal/mol |
| KI Polyomavirus | 4POT | Human | -4.2 kcal/mol |
| JC Polyomavirus | 3BWR | Human | -4.0 kcal/mol |
| BK Polyomavirus | 4MJ0 | Human | -3.6 kcal/mol |

## Figures

| Figure | Description |
|--------|-------------|
| Fig 1 | Dataset overview - sequence length, host categories, species |
| Fig 2 | Feature distributions across host categories |
| Fig 3 | Feature correlation matrix (26 features) |
| Fig 4 | Phylogenetic tree with bootstrap values |
| Fig 6 | Boxplots of key features by host (p < 0.001) |
| Fig 7 | Docking binding energies |
| Fig 8 | Model performance comparison |
| Fig 9 | Feature importance ranking |
| Fig 10 | Confusion matrices for all three models |

## Conclusion

We showed that VP1 protein physicochemical properties contain enough information to predict which host a polyomavirus infects. The SVM model achieved 77.6% accuracy across six host categories, which is about 4.7 times better than random guessing. Proline and glycine content emerged as the most important features, which makes biological sense because these amino acids control the flexibility of the VP1 surface loops that bind to host cell receptors. This approach could be useful for quickly assessing the zoonotic risk of newly discovered polyomaviruses.

## Repository Files

| File | Description |
|------|-------------|
| `vp1_metadata.csv` | 116 sequences with NCBI accessions, hosts, organisms |
| `vp1_sequences.fasta` | VP1 protein sequences in FASTA format |
| `sequence_features.csv` | 26 physicochemical features for all sequences |
| `statistical_tests.csv` | Kruskal-Wallis H-test results for all features |
| `docking_results.csv` | AutoDock Vina binding energies for 12 structures |
| `Fig1-Fig10 PNGs` | All publication figures at 300 DPI |
| `README.md` | This file |

## Software Requirements

- Python 3.13
- BioPython 1.83
- scikit-learn 1.4
- XGBoost 2.0
- SciPy 1.12
- matplotlib 3.8
- MEGA 12
- PyMOL 2.5
- AutoDock Vina 1.1.2
- Open Babel 3.1

## License

MIT License - Copyright (c) 2026 Shreeram Y K

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files, to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software.
