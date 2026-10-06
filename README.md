# Near-bottom currents and fish communities in submarine canyons of the northern Gulf of Eilat/Aqaba

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23105556.svg)](https://doi.org/10.5281/zenodo.23105556)

R code and data for the analyses and figures of:

> Haim, A. *et al.* (in preparation). *[Manuscript title]*. *[Journal]*.

Author of the code: Almog Haim – MEDsLab, Bar-Ilan University, Israel
(almog.haim1@live.biu.ac.il)

## Contents

```
canyon-currents-fish/
├── README.md
├── LICENSE                         MIT licence (code)
├── CITATION.cff                    citation metadata (used by GitHub and Zenodo)
├── canyon-currents-fish.Rproj      RStudio project file
├── scripts/
│   ├── 01_Oceanographic_Data.Rmd        Figures 2, 3, 4 and S1
│   ├── 02_Model_Mooring_Comparison.Rmd  Figures 5, S2 and S3
│   └── 03_Bio_Environmental.Rmd         Figures 6, 7, 8, S4 and S5; GAM and RDA tables
├── data/
│   ├── README.md                   description of every data file and column
│   ├── moorings/                   current-meter and temperature-logger records (18 files)
│   ├── bruvs/                      BRUVS fish counts and deployment table (2 files)
│   └── model/                      hydrodynamic-model output (hourly, 18 stations, 2011–2012)
└── outputs/                        created when the scripts are run (figures, tables, .RData)
```

Figure 1 (study-area map) was produced in GIS and is not part of this repository.

## How to run

1. Install R (≥ 4.3) and, optionally, RStudio.
2. Install the required packages:

   ```r
   install.packages(c("tidyverse", "lubridate", "slider", "zoo", "patchwork",
                      "mgcv", "vegan", "ggrepel", "scales", "knitr", "rmarkdown", "ragg"))
   ```

3. Open `canyon-currents-fish.Rproj` (or set the working directory to the repository folder)
   and knit each script in `scripts/` (RStudio: **Knit**), or from the R console:

   ```r
   rmarkdown::render("scripts/01_Oceanographic_Data.Rmd")
   rmarkdown::render("scripts/02_Model_Mooring_Comparison.Rmd")
   rmarkdown::render("scripts/03_Bio_Environmental.Rmd")
   ```

   The scripts are independent of each other and can be run in any order. Each one reads
   the raw data from `data/`, and writes its figures (PDF, 300-dpi PNG and TIFF), its
   tables (CSV) and its R workspace (`.RData`) to `outputs/`. An HTML report with all code,
   results and the R session information (`sessionInfo()`) is written next to each script.

### Hydrodynamic-model output (Script 2)

Script 2 compares the mooring records with the output of a hydrodynamic model of the Gulf
of Eilat/Aqaba (December 2011 – November 2012). The model output at the 18 study stations
is included in `data/model` (gzip-compressed CSV, read directly by R); see
`data/model/README.md`.

## Software versions

The results in the manuscript were produced with the package versions listed at the end of
each HTML report (`sessionInfo()`). Some results, in particular the negative-binomial GAMs
of total MaxN, can differ slightly between versions of the `mgcv` package.

## Licence

- **Code** (`scripts/`): MIT licence, see `LICENSE`.
- **Data** (`data/`): Creative Commons Attribution 4.0 International (CC BY 4.0) –
  you may reuse the data provided that the source is cited.

## How to cite

Please cite the article above and this repository:

> Haim, A. 2026. Code and data for: Neighboring submarine canyons exhibit distinct physical
> and ecological signatures. Zenodo. https://doi.org/10.5281/zenodo.23105556
