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
│   ├── climate/                  # Climate data files (Schleswig-Holstein regional averages)
│   │   ├── regional_averages_rr_*.txt     # Monthly precipitation data
│   │   └── regional_averages_tm_*.txt     # Monthly temperature data
│   ├── eea/                      # Extracellular enzyme activity data
│   │   ├── df_EEA_final.csv              # Processed EEA data
│   │   ├── df_EEA_processed.csv          # Intermediate processed data
│   │   └── raw/                          # Raw platereader files
│   ├── elevation/                # Elevation measurements
│   │   └── df_iris_elevation.txt         # Plot elevation data
│   ├── faprotax/                 # Functional annotation data
│   │   └── df_functional_database.tsv    # FAPROTAX functional predictions
│   ├── iris/                     # IRIS reduction index measurements
│   │   └── df_iris_2023.txt              # Redox measurements
│   ├── om/                       # Organic matter content data
│   │   ├── df_OM_MERIT_2019.txt          # 2019 organic matter data
│   │   ├── df_OM_MERIT_2021.txt          # 2021 organic matter data
│   │   └── df_OM_MERIT_2022.txt          # 2022 organic matter data
│   ├── qpcr/                     # qPCR bacterial abundance data
│   │   ├── df_copies_EUB.txt             # 16S rRNA gene copy numbers
│   │   └── df_qpcr_summary.csv           # Summary qPCR statistics
│   ├── rna/                      # RNA sequencing data
│   │   ├── table_ASV_filtered.csv        # Filtered ASV table
│   │   ├── table_ASV_filtered_rarefied_5000.csv  # Rarefied ASV table
│   │   ├── taxa_sum_Family.csv           # Family-level taxonomic counts
│   │   └── df_alpha_summary.csv          # Alpha diversity metrics
│   └── warming/                  # Temperature warming data
│       └── MERIT_2022_daily_cleaned.csv  # Daily temperature measurements
├── scripts/                      # Analysis scripts (all harmonized and updated)
│   ├── script_data_preprocessing_eea.Rmd     # EEA raw data processing
│   ├── script_warming_data_2022.Rmd          # Temperature data processing
│   ├── script_correlation_matrix.Rmd         # Cross-variable correlations
│   ├── script_climate.Rmd                    # Climate data analysis
│   ├── script_community.Rmd                  # Microbial community analysis
│   ├── script_eea.Rmd                        # Enzyme activity analysis
│   ├── script_faprotax.Rmd                   # Functional annotation analysis
│   ├── script_iris.Rmd                       # IRIS redox analysis
│   ├── script_om.Rmd                         # Organic matter analysis
│   └── script_qpcr_2023.Rmd                  # Bacterial abundance analysis
└── tables/                       # Output tables and statistical results
    ├── correlation_matrix_overall.csv        # Cross-variable correlation matrix
    └── statistics_all_variables.xlsx         # Comprehensive statistical results
```

## Experimental Design

### Treatments
- **Ambient**: Control plots (no warming)  
- **+1.5°C**: Moderate warming treatment  
- **+3.0°C**: High warming treatment  

### Environmental Zones
- **Pioneer zone (PZ)**: Lower elevation, high salinity, frequent flooding  
- **Low marsh (LM)**: Intermediate elevation and salinity  
- **High marsh (HM)**: Higher elevation, lower salinity, less frequent flooding  

### Soil Layers
- **Topsoil (0-30 cm)**: Upper soil layers (0-5 cm, 5-10 cm, 20-30 cm)  
- **Subsoil (40-100 cm)**: Deeper soil layers (40-50 cm, 80-100 cm)  

## Analyses Included

### 1. Extracellular Enzyme Activities (EEA)
- **Carbon acquisition**: β-1,4-glucosidase (GLU)  
- **Nitrogen acquisition**: Leucine aminopeptidase (LEU), β-1,4-N-acetylglucosaminidase (CHI)  
- Linear mixed-effects models with plot and core as random effects  
- Pairwise comparisons using emmeans package  

### 2. Microbial Community Structure
- **Alpha diversity**: Shannon diversity index  
- **Beta diversity**: NMDS ordination with Bray-Curtis dissimilarity  
- **Taxonomic composition**: Relative abundance at phylum level  
- **Environmental correlations**: Community dissimilarity vs. temperature and elevation gradients  
- PERMANOVA analysis for community differences  

### 3. Functional Annotation (FAPROTAX)
- Prediction of functional groups from 16S rRNA gene sequences  
- Analysis of key biogeochemical processes:
  - Nitrification, denitrification  
  - Sulfate reduction, sulfur oxidation  
  - Methanogenesis, methanotrophy  
  - Fermentation pathways  

### 4. Environmental Variables
- **Temperature**: Multi-depth soil temperature measurements (2 cm, 25 cm, 75 cm)  
- **Redox conditions**: IRIS measurements  
- **Organic matter content**: Loss-on-ignition measurements  
- **Bacterial abundance**: 16S rRNA gene copy numbers via qPCR  
- **Climate**: Regional precipitation and temperature data  
- **Elevation**: Plot-specific elevation measurements  

### 5. Correlation Analysis
- Cross-variable correlation matrix including:
  - Enzyme activities (carbon and nitrogen acquisition)  
  - Alpha diversity metrics  
  - Environmental variables  
  - Temperature measurements  
  - Chemical parameters  

## Statistical Methods

### Model Framework
- **Linear mixed-effects models (lme4)**: Account for spatial structure with plot as random effect  
- **PERMANOVA**: Test for community composition differences  
- **Pairwise comparisons**: Post-hoc tests using emmeans package  
- **Model diagnostics**: Residual normality tests and model validation  

### Experimental Controls
- **Spatial structure**: Plot-level random effects  
- **Pseudoreplication**: Core-level nested random effects where applicable  
- **Multiple comparisons**: Appropriate p-value corrections  

## Script Organization and Standards

### Unified Structure (Updated July 17, 2025)
All scripts follow a harmonized structure with:
- **Hierarchical dataframe naming**: `df_name_#_status` (e.g., `df_eea_0_raw`, `df_eea_1_processed`)  
- **English-only comments**: All German comments removed  
- **Consistent version logs**: Format `## Version X.Y: Description - DD.MM.YYYY | Initials`  
- **Package management**: Only loaded packages are used and referenced  
- **Summary sections**: Comprehensive data overviews at script end  
- **Export functions**: Key results exported for cross-script integration  

### Quality Control
- **Removed obsolete analyses**: robustlmm and log-transformed models removed  
- **Package verification**: All loaded packages are actively used  
- **Reference completeness**: All packages properly cited  
- **Code modularity**: Complex analyses split into focused scripts  

## Key Results and Outputs

### Primary Findings
1. **Environmental gradients drive community structure** more than experimental warming  
2. **Hydrology masks warming effects** on microbial communities  
3. **Depth-dependent responses** to warming treatments  
4. **Zone-specific functional profiles** related to salinity and flooding regimes  

### Generated Outputs
- **Comprehensive correlation matrix** of all measured variables  
- **Community ordination plots** showing environmental drivers  
- **Functional group heatmaps** for biogeochemical processes  
- **Temperature response plots** for enzyme activities  
- **Alpha diversity comparisons** across treatments and zones  

## Usage Instructions

### Prerequisites
- R version ≥ 4.0.0  
- Required packages listed in each script  
- Adequate memory for large phyloseq objects  

### Workflow
1. **Data preprocessing**: Run `script_data_preprocessing_eea.Rmd` and `script_warming_data_2022.Rmd`  
2. **Individual analyses**: Execute analysis scripts in any order  
3. **Integration**: Run `script_correlation_matrix.Rmd` for cross-variable analysis  
4. **Results**: Check `tables/` directory for statistical outputs  

### File Dependencies
- Most scripts are self-contained  
- Correlation matrix script depends on summary outputs from other analyses  
- All scripts use relative paths from repository root  

## Data Availability
Raw sequencing data is available through NCBI SRA under BioProject [insert accession].  
Environmental data and processed datasets are included in this repository.

## Citation
If you use this repository, please cite:
[Citation will be added upon publication]

## Contact
Julian Mittmann-Goetsch (julian.mittmann-goetsch@uni-hamburg.de)  
Institute of Plant Science and Microbiology, University of Hamburg

## License
[License information to be added]

---

*Repository last updated: July 17, 2025*  
*All scripts harmonized and validated for reproducibility*
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
