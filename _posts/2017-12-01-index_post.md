---
layout: post
---

## Syntax Highlighting for Computational Biology.

Intuitive coloring for `.sam`, `.vcf`, `.fasta`, `.fastq`, `.gtf`, `.bed`, `.pdb`, & more formats.

<div style="text-align:center">
<script src="https://asciinema.org/a/153567.js" id="asciicast-153567" async></script>
</div>

<!--[<img src="http://biosyntax.org/images/sam-less-2.gif">](images/screens/sam-less.png)
-->

### [INSTALL bioSyntax](install)

### Usage

bioSyntax integrates seamlessly with **vim**, **less**, **gedit**, & **sublime** to automatically recognize [your favorite biological file formats](man#supported-file-formats). To gain the most insight from your data, read our brief [bioSyntax Manual](man).

Large data can also be directly piped into **less** with `sam-less`, `vcf-less`, ..., `xyz-less` commands.

![Example less command](images/sam-less_command.gif)

&nbsp;

We're actively developing bioSyntax; we'd love to hear your comments, feedback and suggestions for further development. [Drop us a line on github](https://github.com/bioSyntax/bioSyntax/issues) or [email](mailto:info@bioSyntax.org).

------------------------------------------------------------------------------

## Updates

#### 2017-12-19 - bioSyntax v0.1-beta Release

- [Pre-print manuscript](https://www.biorxiv.org/content/early/2017/12/20/235820) initial release
- Syntax highlighting for FASTA, FASTQ, BED, GTF, PDB, SAM & VCF
- Ported to gedit, sublime, vim and less