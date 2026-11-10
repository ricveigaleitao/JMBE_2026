# Teaching Microbiomes and One Health: computational practical sessions

[![DOI](https://zenodo.org/badge/1452498296.svg)](https://doi.org/10.5281/zenodo.24116287)

Teaching materials for the two computational practical sessions described in:

> Costa, Joana & Leitão, Ricardo. Teaching Microbiomes and One Health in the Age of AI: A Field-Tested Curriculum Sequence for Complex Causality, Data Interpretation, and Evidence-to-Action Learning. *Journal of Microbiology & Biology Education* (submitted).

In these sessions, undergraduate students work hands-on with real 16S rRNA metabarcoding data in R/RStudio. The aim is not to train bioinformaticians, but to show how sequence-based evidence is generated, processed, interpreted, and limited, and how choices at earlier stages (experimental design, sampling, marker choice, bioinformatic processing) shape the final results and conclusions.

- **Practical session 1** goes from raw sequencing reads to a table of microbial taxa (DADA2 workflow).
- **Practical session 2** analyses and interprets a microbiome dataset: alpha and beta diversity, shared taxa, taxonomic composition, and predicted functions.

This repository accompanies Appendix S2 of the article.

## Repository contents

```
├── README.md
├── LICENSE
├── install_R_packages.Rmd            # installs all packages for both sessions
├── practical_session1/
│   ├── practical_session1_workflow.Rmd    # guided R Markdown script
│   ├── practical_session1_workflow.html   # rendered script: code + outputs
│   ├── data/                              # input data (see "Data")
│   ├── outputs/                           # example outputs from the authors' run
│   └── instructions/                      # student guide (.pdf and editable .docx)
└── practical_session2/
    ├── practical_session2_workflow.Rmd
    ├── practical_session2_workflow.html
    ├── data/
    ├── outputs/
    └── instructions/
```

## Quick start

1. **Download** the repository: from Zenodo (https://doi.org/10.5281/zenodo.24116287) or GitHub (green **Code** button → **Download ZIP**). Unzip it.
2. **Open** `JMBE_2026.Rproj` in RStudio.
3. **Install packages** once: open `install_R_packages.Rmd` and run all chunks. The last chunk reports any package that failed to install.
4. **Session 1 only: download the SILVA reference file** (about 139 MB; too large for this repository). Download `silva_nr99_v138.2_toGenus_trainset.fa.gz` from <https://zenodo.org/records/14169026> and save it in `practical_session1/data/`.
5. **Open a workflow** (`practical_session1_workflow.Rmd` or `practical_session2_workflow.Rmd`) and run the chunks in order, or click **Knit** to run the whole script and produce the HTML report.

All file paths in the scripts are relative to each session folder, so the materials work on any computer without editing paths.

**No working R installation?** Open the `.html` file of each session in a web browser. It shows every step of the script with its output, so students can follow the analysis on their own computer while the instructor runs the code on a projected screen.

## Data

All data are small subsets of an unpublished research project by one of the authors, shared for teaching purposes.

**Practical session 1** (`practical_session1/data/`)
- `A1_1_clean.fastq`, `A1_2_clean.fastq`, `A2_1_clean.fastq`, `A2_2_clean.fastq`: paired-end reads (forward `_1` and reverse `_2`) for two soil samples, after adapter and primer removal. Used to inspect sequencing output and as input for DADA2.
- `Metadata_test.csv`: sample metadata.
- `silva_nr99_v138.2_toGenus_trainset.fa.gz`: SILVA reference file (download separately; see Quick start).

**Practical session 2** (`practical_session2/data/`)
- `ps_cultivar.rds`: a phyloseq object with 12 soil samples, collected in summer from three plots in each of four farms in a Mediterranean region, with an ASV table, taxonomy, and sample metadata. Main variables: `Culture` (Olive, Almond) and `System1`, the farm management system: `O_olive` (organic olive), `T_olive` (traditional olive), `I_almond` (intensive almond), and `HI_almond` (high-intensive almond).
- `functional_table.tsv`: predicted functional groups (FAPROTAX) for the same 12 samples.

## Example outputs

The `outputs/` folders contain the results of the authors' run of each workflow:

- **Session 1:** filtered reads, and `ps.rds` and `taxa.rds`, the phyloseq object and taxonomy table produced at the end of the workflow. These can be used as a starting point if DADA2 cannot be run in class.
- **Session 2:** `alfa-diversity/`, `beta-diversity/`, `venn_diagram/`, `taxonomy_plots/` and `faprotax/`, with figures (PNG), tables (CSV), and PERMANOVA results (TXT).

Running the scripts overwrites these files, so students can compare their own results with the reference outputs. Small visual differences (e.g. jittered points) are expected between runs.

## Software requirements

Developed and tested with R 4.6.2 and RStudio 2026.10.1+239 on Windows. Exact package versions are listed in `package_versions.csv`, and the full session information (R version, operating system, and loaded packages) is printed at the end of each rendered HTML workflow.

| Session | Bioconductor | CRAN |
|---|---|---|
| 1 | ShortRead, dada2, Biostrings, phyloseq | ggplot2, rmarkdown, knitr |
| 2 | phyloseq, DESeq2, microbiome | ggplot2, RColorBrewer, vegan, ggvenn, dplyr, ggpubr, scales, ragg, gplots |

On Windows, `filterAndTrim()` must run with `multithread = FALSE` (already set in the script).

## Adapting the materials

Instructors are encouraged to adapt the scripts, datasets, and student guides to their own courses. The `.docx` versions of the student guides can be edited directly. The workflows can be used with other amplicon datasets by replacing the files in `data/` and adjusting the metadata variables and DADA2 parameters (e.g. `truncLen`, expected sequence length).

## How to cite

If you use these materials, please cite the article and this repository:

> Costa, Joana & Leitão, Ricardo. (2026). *Teaching Microbiomes and One Health: R Markdown workflows and data for two computational practical sessions* [Computer software and data set]. Zenodo. https://doi.org/10.5281/zenodo.24116287

## License

The code (R Markdown scripts) is released under the MIT License (see `LICENSE`). The data, student guides, and example outputs are released under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

The SILVA reference database is not distributed here; it is subject to its own license (see the SILVA website).

## Contact

Joana Costa : jcosta@uc.pt
Ricardo Leitão: https://github.com/ricveigaleitao/JMBE_2026
