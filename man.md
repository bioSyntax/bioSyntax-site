---
layout: page
title: bioSyntax Manual
image:
  feature: abstract-3.jpg
comments: false
markdown: kramdown
---
Grok your data

The objective of bioSyntax is to bring you closer to your data, giving you an [intuitive & empathetic](https://en.wikipedia.org/wiki/Grok) understanding of biology. To appreciate all that bioSyntax has to offer read this short manual (~10 minutes) and go explore.

{:toc}

1. [Getting Started](#getting-started) 
2. [Reading bioSyntax](#reading-biosyntax)
3. [Supported Formats](#supported-file-formats)
4. [Developing New Formats & Themes](#collaborate)

# Getting Started

### [Installing bioSyntax -->](../install)

bioSyntax integreates seamlessly with `vim` (Linux / Mac / Win), `sublime` (Linux / Mac / Win), `gedit` (Linux / Win), & `less` (Linux / Mac).


### Reading large-data

For very large data sets, it's often slow to open them in a text editor. It's best to use the command-line program `less` which will read your file from a data-stream. We currently support `.sam`, `.vcf`, & `.fasta` files for less.

##### Read your large-data set with `less` directly

```
# If your file is uncompressed, it can be read directly
# less will recognize the file extension (.XYZ)

cd ~/myData/

less dbSNP107_common.vcf

less hg19.fa
```

##### Stream your data into `less` on the command line using pipes (`|`)

```
# If your file is compressed, you can 'pipe' the data 
# using the "|" operator from decompression, directly into
# less. You must prefix the extension as file formats are
# not recognized.

cd ~/myCompressedData/ 

samtools view -h NA12878_hg38.bam | sam-less

gzip -dc dbSNP107_rare.vcf.gz | vcf-less

gzip -dc hg38.fa.gz
```


# Reading Data

### Nucleotides

bioSyntax implements full [IUPAC Nucleotide Code](https://en.wikipedia.org/wiki/Nucleic_acid_notation#IUPAC_notation) coloring. Ambiguous bases are represented by additive color-mixing of the parent bases. For example, **T**hymine (blue) + **C**ytosine (red) are both p**Y**rimidines (magenta).

![bioSyntax Nucleotides](../images/nt_IUPAC_v0.1.png)

An intuitive feature of this color scheme is that the 'GC-content' of a sequence can be quickly approximated by how warm (high GC, red-orange) or cool (low GC, blue-green) a sequence appears.

### PHRED Scores

When available, bioSyntax will highlight [PHRED quality scores](https://en.wikipedia.org/wiki/Phred_quality_score) in a step-gradient of blacks (PHRED = 0-10) to whites (PHRED = 40+).

### CIGAR Strings

Probabaly the most cumbersome

### Amino Acid Color Schemes

You can choose from several color-schemes for amino-acid fasta files. The `Fasta Clustal` (Default) syntax is good for discriminating amino acids, or you may prefer `Fasta Zappo`, `Fasta Taylor` or `Fasta Hydrophobiticy` which group and color the amino acids slightly differently.

### GTF / WIG Scores

# Supported File Formats

File format and software compatibility matrix for bioSyntax.

|   | status            |
|---|:------------------|
| X |   Syntax Complete |
| o |   In Development  |
| - |   Unavailable     |

## Core Syntaxes

| File Format | Description                 | sublime | vim | gedit | less |
|:------------|:----------------------------|:-------:|:---:|:-----:|:----:|
| .fasta      | Generic nt/aa sequence      |    X    |  X  |   X   |   X  |
| .fastq      | Fasta + PHRED quality       |    X    |  -  |   -   |   X  |
| .clustal    | Multiple Sequence Alignment |    X    |  o  |   X   |   X  |
| .bed        | Genomic Ranges              |    X    |  o  |   X   |   X  |
| .gtf        | Genomic Annotation          |    X    |  o  |   o   |   X  |
| .pdb        | Protein Structure           |    X    |  X  |   o   |   -  |
| .vcf        | Variant Call Format         |    o    |  o  |   o   |   X  |
| .sam        | NGS Sequence Data           |    X    |  -  |   o   |   X  |

## Auxillary Syntaxes

| File Format | Description                 | sublime | vim | Gedit | less |
|-------------|-----------------------------|:-------:|:---:|:-----:|:----:|
| .fasta      | fasta alternative AA colors |         |     |       |      |
| -           | Clustal                     |    X    |  o  |   X   | -    |
| -           | Taylor                      |    X    |  o  |   X   | -    |
| -           | Zappo                       |    X    |  o  |   X   | -    |
| -           | Hydrophobicity              |    X    |  o  |   X   | -    |
| .fai        | Fasta Index (faidx)         |    X    |  X  |   X   | X    |
| .flagstat   | samtools flag summary       |    X    |  -  |   X   | X    |
| .newick     | Tree Format                 |    -    |  -  |   -   | -    |
| .pdbx       | Protein Structure (large)   |    -    |  -  |   -   | -    |
| .phylip     | Multiple Sequence Alignment |    -    |  -  |   -   | -    |
| .wig        | Wiggle data                 |    o    |  -  |   X   | -    |


# Collaborate

[ Under Construction ]

bioSyntax is a community project for biological syntax highlighting. If you work with a particular file format you'd like syntax highlighting for, develop the syntax files and we'll add them. Don't worry we can help : )

## Report a bug

## Developing bioSyntax for `.XXX` file format

## Creating a custom theme

## Other ways to help

Right now check out the [bioSyntax Repo](https://github.com/ababaian/bioSyntax) and look under 'issues' for development instructions.

If you're really keen, check out the [TODO](https://github.com/ababaian/bioSyntax/issues) for ways to help develop bioSyntax.

[ under construction ]
- How To Instructions for each program  (take from issues)
- Other ways to contribute...

