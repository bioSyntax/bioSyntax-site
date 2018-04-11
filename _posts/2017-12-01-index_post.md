---
layout: post
---

## Syntax Highlighting for Computational Biology.

Our goal is to make data intuitive for scientists and help you navigate and comprehend its significance. Currently supporting `.sam`, `.vcf`, `.fasta`, `.fastq`, `.gtf`, `.bed`, `.pdb`, `.cwl`, [& more formats](https://biosyntax.org/man#supported-file-formats).

<div style="text-align:center">
<script src="https://asciinema.org/a/153567.js" id="asciicast-153567" async></script>
</div>

<!--[<img src="http://biosyntax.org/images/sam-less-2.gif">](images/screens/sam-less.png)
-->

### [Tell us how bioSyntax can develop to help your workflow. (Survey ~5m)](https://goo.gl/forms/YO89fEPw71JpH3Ac2)

### [INSTALL bioSyntax](install)

### Usage

bioSyntax integrates seamlessly with **vim**, **less**, **gedit**, & **sublime** to automatically recognize [your favorite biological file formats](man#supported-file-formats). To gain the most insight from your data, read our brief [bioSyntax Manual](man).

Large data can also be directly piped into **less** with `sam-less`, `vcf-less`, ..., `xyz-less` commands.

![Example less command](images/sam-less_command.gif)

&nbsp;

### Collaborate

We're actively developing bioSyntax; we'd love to hear your comments, feedback and suggestions for further development. [Drop us a line on github](https://github.com/bioSyntax/bioSyntax/issues) or [email](mailto:info@bioSyntax.org).

If you'd like to help out, have intimate understanding of a scientific data-type, or are looking for a fun design / optimization problem check the [development page](dev).

------------------------------------------------------------------------------

## Updates

#### 2018-04-11 - bioSyntax v0.1-beta4 + Development Survey
- We're working on a [user experience survey](https://goo.gl/forms/YO89fEPw71JpH3Ac2) to focus development.
- New Syntax `vim-nexus`
- New Syntax `vim-pml` & `sublime-pml`(Pymol Script Language)
- New Syntax `cwl-sublime` and `cwl-vim` (Common Workflow Language)
- Add `bam-less` alias for `sam-less` by default
- Removed `sudo` requirements for linux-gedit & linux-less installations
- Alternative Syntax: `vim_fasta-ORF`: Syntax for finding and highlighting Open Reading Frames

#### Thanks to
- [Luis Carvalho](https://vim.sourceforge.io/scripts/script.php?script_id=964) for `vim-nexus`
- @manabuishii for `cwl-sublime` and `cwl-vim`
- @speleo3 for `vim-pml` & @bbarad for `sublime-pml`

#### Past releases
- [Pre-print manuscript](https://www.biorxiv.org/content/early/2017/12/20/235820) initial release
- [Release History](https://github.com/bioSyntax/bioSyntax/releases)