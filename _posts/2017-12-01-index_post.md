---
layout: post
---

## Syntax Highlighting for Computational Biology.

Intuitive coloring for `.sam`, `.vcf`, `.fasta`, `.gtf`, `.pdb`, & more formats.

<div style="text-align:center">
<script src="https://asciinema.org/a/153567.js" id="asciicast-153567" async></script>
</div>

<!--[<img src="http://biosyntax.org/images/sam-less-2.gif">](images/screens/sam-less.png)
-->

### Usage

bioSyntax integrates seamlessly with **vim**, **less**, **gedit**, & **sublime** to automatically recognize [your favorite biological file formats](man#supported-file-formats). Large data files can also be directly piped into **less** with `sam-less`, `vcf-less`, ..., `xyz-less` commands.

![Example less command](images/sam-less_command.gif)

To gain the most insight from your data, read our brief [bioSyntax Manual](man).

### [INSTALL](install)

## Updates

#### 2017-12-19 - bioSyntax v0.1-beta1 Release

- Initial release for pre-print manuscript
- Syntax highlighting for FASTA, FASTQ, BED, GTF, PDB, SAM & VCF
- Ported to gedit, sublime, vim and less