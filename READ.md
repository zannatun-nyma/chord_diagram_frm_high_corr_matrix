# Metabolite Interaction Network Visualization

This repository contains the Python implementation for generating a high-resolution, publication-ready chord diagram. The visualization illustrates internal connectivity among highly correlated serum metabolites, specifically designed for metabolomics research.



## 🔬 Scientific Context
The network graph displays associations between serum metabolites characterized by high-strength partial rank correlations ($|r| \geq 0.70$).

- **Nodes:** Represent individual metabolites. Size and color intensity are proportional to the "degree" or connectivity score (ranging from 1 [single association] to 4 [high-degree central hubs]).
- **Edges:** Represent pairwise associations. Line thickness and color gradient correspond to the magnitude of the partial correlation coefficient.
- **Statistical Basis:** Partial rank correlation coefficients were derived using Spearman analysis adjusted for age, sex, and center.

## 🛠 Installation & Setup

### 1. Using Conda (Recommended)
This method recreates the environment with all necessary C-extensions for Biopython and Matplotlib.

```bash
# Create the environment from the .yml file
conda env create -f environment.yml

# Activate the environment
conda activate chord_diagram_env
```

### 2. Using pip
Alternatively, if you are not using Conda, you can install the dependencies via pip using the provided requirements file:
```bash
pip install -r requirements.txt
```

## 📂 Project Structure
```text
project_root/
│
├── data/
│   └── weighted_high_corr_adjacency_matrix.csv  # Input correlation matrix
│
├── img/
│   ├── final_chord.png                          # High-resolution output
│   └── final_chord.svg                          # Scalable vector output
│
├── chord_diagram.py                             # Main processing script
├── environment.yml                              # Conda environment config
├── requirements.txt                             # Pip requirements file
├── 1. creat_high_corr_matrix.ipynb                            # Exploration notebook
└── 5. high_corr_pycirclize.ipynb                            # Final visualization notebook
```

## 🚀 Running the Code
To generate the chord diagram, run the following command in your terminal:

```bash
python chord_diagram.py
```

## 🎨 Visualization Features
- **Custom Node Gradient:** Uses a truncated `magma_r` colormap (darkened to remove bright neon yellow) to represent node degrees.
- **Radial (Ray-like) Labels:** Metabolite names are oriented perpendicularly to the circle to accommodate long chemical nomenclature without overlapping.
- **Dual Legends:** Includes a vertical colorbar for link strength (Seismic) and a rectangular discrete legend for node degrees.

