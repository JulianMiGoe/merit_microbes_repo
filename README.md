# merit_microbes_repo

**Despite Overall Resilience, High Marsh Zones in Saltmarshes Show Signs of Drought-Induced Stress in Microbial Communities**

Julian Mittmann-Goetsch¹, Johann Jaitner¹, Alexander Bartholomäus², Simon Thomsen¹, Roy Rich³, Kai Jensen¹, Susanne Liebner²˒⁴, Peter Mueller⁵˒⁶, Viktoria Unger¹  
¹ Institute of Plant Science and Microbiology, Universität Hamburg, Hamburg, Germany  
² GFZ German Research Center for Geosciences, Geomicrobiology, Potsdam, Germany  
³ Smithsonian Environmental Research Center, Edgewater, MD, USA  
⁴ Institute for Biochemistry and Biology, Universität Potsdam, Potsdam, Germany  
⁵ Institute of Landscape Ecology, Universität Münster, Münster, Germany  
⁶ Institute of Environmental Sciences, Rheinland-Pfälzische Technische Universität, Kaiserslautern Landau, Germany

---

## Context

This repository contains data and analysis scripts from the MERIT experiment, which investigates the effects of warming and drought on soil microbial communities in saltmarshes. The focus is on the resilience and stress responses of microbial communities in different marsh zones (especially high marsh) under extreme events.

## Data

The [`data/`](data/) folder contains:
- **Raw data** on climate, soil parameters, enzyme activities, DNA/RNA, qPCR, organic matter, and more.
- Metadata for samples and sites (`metadata.csv`, `metadata.txt`)
- Subfolders for different data types (e.g., `bgb/`, `climate/`, `eea/`, `elevation/`, `faprotax/`, `iris/`, `qpcr/`, `rna/`, `warming/`)

## Scripts

The [`scripts/`](scripts/) folder contains RMarkdown scripts for data analysis:
- `script_bgb.Rmd`: Belowground biomass analysis
- `script_climate.Rmd`: Climate data analysis
- `script_community.Rmd`: Community analyses
- `script_eea.Rmd`: Enzyme activity analyses
- `script_faprotax.Rmd`: Functional group analyses
- `script_iris.Rmd`: IRIS tube and elevation data analysis
- `script_om.Rmd`: Organic matter data analysis
- `script_qpcr_2023.Rmd`: qPCR analyses
- `script_warming_data_2022.Rmd`: Data preparation and filtering for warming experiment

Each script is modular and includes sections for package installation, data preprocessing, analysis, and visualization.

## Usage

1. Open RStudio or VSCode and load the project (`merit_microbes_repo.Rproj`).
2. Open the desired script from the [`scripts/`](scripts/) folder and run step by step.
3. Scripts are designed to access data from the [`data/`](data/) folder.

## Notes

- All data and scripts are provided to ensure reproducibility of the analyses for the associated publication.
- For questions, please contact the first author (Julian Mittmann-Goetsch).

---
