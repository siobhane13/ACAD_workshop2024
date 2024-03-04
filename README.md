# ACAD_workshop2024

First login to the cloud server using ssh

```ssh user@acadworkshop.uoa.cloud```

### Make github repo and clone it to your home directory in the cloud
Use git clone to clone repository to your local machine

```git clone https://github.com/your-username/repository.git```

### Make changes and push from local terminal
Navigate to your repo in the local terminal 
Use a text editor (vim, nano) to add/remove text

```nano repositoryname```

Then add these changes, commit writing a message and push it to your copy of the repo

```
git status
git add
git commit -m "comment on what was added"
git push
```

To list commits

```
git log
git log --oneline --decorate --graph
```

Can then roll back to previous version, maybe if mistake made or need to run a previous version

```git checkout IDofversion```

### Setting up conda environments and other dependencies
Create (acad-euks_1) environment files. Use text editior to copy and paste content in box below and save file as acad-euks_1.yaml.

```
name: acad-euks_1
channels:
  - conda-forge
  - bioconda
  - defaults
dependencies:
  - python>=3.8,<=3.9
  - Cython>=0.29.24
  - pip
  - pip:
      - pyrle>=0.0.31
      - pyranges>=0.0.112
      - kneed>=0.8.1
      - matplotlib>=3.6.0
  - samtools
  - bowtie2
  - r-base
  - r-ggplot2
  - r-dplyr
  - r-tidyr
  - r-readr
  - fastp
  - vsearch
  - sga
  - seqtk
  - fasta-splitter
  - datamash
  - seqkit
```

Then create the environment

```conda env create -f acad-euks_1.yaml```

and then activate the environment

```conda activate acad-euks_1.yaml```

Lastly, install bam-filter in the acad-euks_1 using pip

```pip install bam-filter```

### Data Analysis
Activate conda environment

```conda activate acad-euks_1```

Quality control of trimmed and merged sequences. Important to remove duplicates, to save cpu and run time. Can use 'vsearch' which is a fast tool that screens for 100% identical sequences. ```vsearch --help``` allows familiarisation with its options

```time vsearch --fastx_uniques ERR10493277_small-FINAL.fq.gz --fastqout ERR10493277_small-FINAL.vs.fq --minseqlength 30 --strand both```








