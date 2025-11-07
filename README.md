# pathopipe
**Ancient Pathogen Screening Workflow**

The pipeline is described in detail in Sikora et al., 2025, **"The spatiotemporal distribution of human pathogens in ancient Eurasia"** [https://www.nature.com/articles/s41586-025-09192-8](https://www.nature.com/articles/s41586-025-09192-8)

## Table of Contents
- [About](#about)
- [Installation](#installation)
- [Usage](#usage)
- [Input / Output](#input-output)
- [Configuration](#configuration)
- [Workflow Overview](#workflow-overview)
- [Examples](#examples)
- [Requirements](#requirements)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## About
`pathopipe` is a Snakemake workflow designed to identify and classify microbial DNA within ancient shotgun sequencing data. The workflow was developed to detect pathogens in ancient human data, but it can be applied across a wide range of microbial and eukaryotic targets, using sequencing data from various sources such as animal remains and ancient environmental samples. 

The pipeline orchestrates multiple steps—quality control, mapping, damage profiling, taxonomic classification, summary reporting—into a unified, reproducible framework.

## Installation
1. Clone the repository:

```
git clone https://github.com/martinsikora/pathopipe.git 
cd pathopipe
```

2. Install required dependencies:
    - krakenuniq (1.0.4)
    - mawk (1.3.4)
    - seqtk (1.3-r106)
    - seqkit (2.3.0)
    - bowtie2 (2.5.2)
    - samtools (1.17)
    - picard (2.27.5)
    - bedtools (2.30.0)
    - datamash (1.5)
    - metaDMG (0.2-41-gc867207)
    - snakemake (7.20.0)
    - gargammel (1.1.4)
    - R (4.2.2)
    - R package fastTopics (0.6-142)
    - R package Rbeast (0.9.7)
    - R package tidyverse (1.3.2)
    - R package inlabru (2.8.0)
    - R package Rsamtools (2.14.0)
   
4. Download reference database:
   ```
   https://doi.org/10.17894/ucph.f0f75211-7bc3-445d-90c0-b72a22ba0930
   ```

## Usage
Create a tab-separated list of sample-IDs and corresponding fastq files with column names `sampleId` and `fq` (see example file `units.tsv`). Edit your config.yml to point to your units file, reference databases, and modify other parameters if relevant.

To run the workflow:

```
snakemake --configfile config.yml --cores <N>
```
Replace <N> with the number of CPU cores you wish to allocate.
You can use the provided Snakefile or summarize.Snakefile for different stages of the analysis.

(Optional) To summarise results across all samples analysed after completion of the pathopipe pipeline, run:
```
snakemake -s summarize.Snakefile --configfile config.yml --cores <N>
```

