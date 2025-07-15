# MERIT Microbes Repository

## Overview
This repository contains R scripts and data for analyzing microbial communities and enzymatic activities from the MERIT (Marine Ecosystem Response to warming In Tidal wetlands) whole-ecosystem warming experiment. The study was conducted in a Wadden Sea salt marsh (Hamburger Hallig, Schleswig-Holstein, Germany).

**Publication**: Hydrology Masks Warming Effects on Microbial Communities in Salt Marsh Soils

**Authors**: Julian Mittmann-Goetsch¹, Peter Mueller²'³, Kai Jensen¹, Susanne Liebner⁴'⁵, Simon Thomsen¹, Roy Rich³, Alexander Bartholomäus⁴, Dirk Granse¹, Johann Jaitner¹, Viktoria Unger¹  

**Affiliations**:  
¹ Institute of Plant Science and Microbiology, University of Hamburg, Hamburg, Germany  
² Institute of Landscape Ecology, Universität Münster, Münster, Germany  
³ Institute for Environmental Sciences, Rheinland-Pfälzische Technische Universität, Kaiserslautern Landau, Germany  
⁴ GFZ German Research Center for Geosciences, Geomicrobiology, Potsdam, Germany  
⁵ Institute for Biochemistry and Biology, Universität Potsdam, Potsdam, Germany  
⁶ Smithsonian Environmental Research Center, Edgewater, MD, USA

## Repository Structure

```
merit_microbes_repo/
├── data/                          # Raw and processed datasets
│   ├── metadata.csv              # Sample metadata
│   ├── climate/                  # Climate data files
│   ├── eea/                      # Extracellular enzyme activity data
│   ├── elevation/                # Elevation measurements
│   ├── faprotax/                 # Functional annotation data
│   ├── iris/                     # IRIS measurements
│   ├── om/                       # Organic matter content data
│   ├── qpcr/                     # qPCR abundance data
│   ├── rna/                      # RNA sequencing data
│   └── warming/                  # Temperature warming data
├── scripts/                      # Analysis scripts
│   ├── script_data_preprocessing_eea.Rmd     # EEA raw data processing
│   ├── script_data_preprocessing_warming.Rmd # Warming data processing
│   ├── script_correlation_matrix.Rmd         # Cross-variable correlations
│   ├── script_climate.Rmd                    # Climate data analysis
│   ├── script_community.Rmd                  # Microbial community analysis
│   ├── script_eea.Rmd                        # Enzyme activity analysis
│   ├── script_faprotax.Rmd                   # Functional annotation analysis
│   ├── script_iris.Rmd                       # IRIS analysis
│   ├── script_om.Rmd                         # Organic matter analysis
│   └── script_qpcr_2023.Rmd                  # Bacterial abundance analysis
└── tables/                       # Output tables and statistics
```

## Experimental Design

### Treatments
- **Ambient**: Control plots (no warming)
- **+1.5°C**: Moderate warming treatment
- **+3.0°C**: High warming treatment

### Zones
- **Pioneer zone**: Early successional marsh areas
- **Low marsh**: Regularly flooded areas
- **High marsh**: Occasionally flooded areas

### Soil Layers
- **Topsoil (0-30 cm)**: Surface soil layers (0-5, 5-10, 20-30 cm depths)
- **Subsoil (40-100 cm)**: Deeper soil layers (40-50, 80-100 cm depths)

## Data Processing Workflow

1. **Data Preprocessing**: Raw data processing and quality control
2. **Individual Analyses**: Separate analysis scripts for each data type
3. **Integration**: Cross-variable correlation and synthesis

## Script Descriptions

### Preprocessing Scripts
- `script_data_preprocessing_eea.Rmd`: Processes raw EEA plate reader data
- `script_data_preprocessing_warming.Rmd`: Cleans and summarizes temperature data

### Analysis Scripts
- `script_community.Rmd`: Microbial community composition and diversity analysis
- `script_eea.Rmd`: Extracellular enzyme activity analysis (C and N acquisition)
- `script_faprotax.Rmd`: Functional gene annotation and pathway analysis
- `script_iris.Rmd`: Iron reduction activity measurements
- `script_om.Rmd`: Organic matter content analysis
- `script_qpcr_2023.Rmd`: Bacterial abundance (16S rRNA gene copies)
- `script_climate.Rmd`: Climate and environmental data analysis

### Integration Scripts
- `script_correlation_matrix.Rmd`: Cross-variable correlations and multivariate analysis

## Data Naming Convention

Dataframes follow a hierarchical naming convention:
- `df_[dataset]_0_raw`: Raw, unprocessed data
- `df_[dataset]_1_filtered`: Quality-filtered data
- `df_[dataset]_2_summarized`: Aggregated/summarized data
- `df_[dataset]_3_merged`: Data merged with other datasets
- `df_[dataset]_final`: Final processed data for analysis

## Key Variables

### Response Variables
- **Alpha diversity**: Shannon diversity index
- **Beta diversity**: Bray-Curtis dissimilarity
- **EEA**: Enzyme activities (GLU, CHI, LEU) normalized to organic matter
- **qPCR**: 16S rRNA gene copy numbers
- **Functional diversity**: FAPROTAX functional groups

### Environmental Variables
- **Temperature**: Soil temperature at multiple depths
- **Elevation**: Plot elevation relative to mean sea level
- **Organic matter**: Soil organic matter content (%)
- **Iron reduction**: IRIS probe measurements

## Statistical Methods

- **Mixed-effects models**: Account for spatial dependence (plot-level random effects)
- **Robust regression**: Handle non-normal residuals (robustlmm package)
- **PERMANOVA**: Test multivariate community differences
- **Post-hoc tests**: Pairwise comparisons with emmeans

## Requirements

### R Version
R ≥ 4.0.0

### Required Packages
See individual script headers for specific package requirements. Key packages include:
- `phyloseq`, `vegan`: Community ecology analysis
- `lme4`, `robustlmm`: Mixed-effects modeling
- `emmeans`: Post-hoc comparisons
- `ggplot2`, `ggpubr`: Data visualization
- `dplyr`, `tidyverse`: Data manipulation

## Usage

1. Clone the repository
2. Ensure all required packages are installed
3. Run preprocessing scripts first:
   - `script_data_preprocessing_eea.Rmd`
   - `script_data_preprocessing_warming.Rmd`
4. Run individual analysis scripts as needed
5. Run integration script for cross-variable analysis:
   - `script_correlation_matrix.Rmd`

## Citation

If you use this code or data, please cite:
[Citation will be added upon publication]

## Contact

Julian Mittmann-Goetsch  
Institute of Plant Science and Microbiology, Universität Hamburg

---
