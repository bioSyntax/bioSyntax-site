---
layout: page
title: Developing bioSyntax
image:
  feature: tiredformatician.gif
  credit: goldenboy
comments: true
markdown: kramdown
---
	"HAPPINESS ONLY REAL WHEN SHARED" -C. McCandless

bioSyntax is a community project for scientific syntax highlighting. We encourage you to change and customize it to suit your needs. This page is a collection of resources to help you start that journey. Once you create something helpful, chances are others will find it helpful too, so share :)

{:toc}

1. [Development Guidelines](#biosyntax-development-guidelines)
...

# bioSyntax Development Guidelines

## Design Principles

1. KISS: Keep it simple & sweet.

2. Grok your data.
	Syntax highlighting increases legibility, that is the ease with which characters are read. Great syntax highlighting (in science) also reveals the content of the data with a glance.
	To understand what information is important, you should understand the data structure and how its being applied/used by scientists (opposed to machine parsing). The most valuble asset here is real-life experience working with a file type.

3. Make it portable.
	Scientific computing is messy and often not standardized. The syntax you develop may work for your use-cases but not be widely portable. A few steps from the beginning can help you define syntax broadly and accurately.
	- Find and carefully read the **Format Specification** for you file-type (i.e. [SAM Spec](https://samtools.github.io/hts-specs/SAMv1.pdf)). This is your primary guide for what is and is not appropriate within a file-type.
	- Find multiple example files in the central databases (NCBI SRA, EMBL-EBI, RCSB, ...).
	- Find multiple example files used by large consortiums or teams (ENCODE, 1000 Genomes Project, RefSeq, ...)
	- Find multiple example files output from common software packages (GATK, CLUSTAL, UCSC Genome Browser, Galaxy, ...)


## Developing syntax-highlighting for `<$file-format>`

If you work with a scientific file-format and would like to add syntax-highlighting to it, we'd like to help you develop it.

1. Fork the [bioSyntax repository](fork).
2. Search [bioSyntax Issues](https://github.com/bioSyntax/bioSyntax/issues) for the file-format you're interested in.
	- If it exists; Help develop it.
	- If it doesn't exist; start an issue for that format.
		a) Title:"FORMAT DEVELOPMENT: `<$file-format>`"
		b) Include a 'File Specification Definition'
		c) Find and include 3-4 example data files (<100 kb) for testing
		d) In words, write out a 'sketch' of how you would like the syntax highlighting to function
3. Read other examples of syntax-definition files to learn how it functions.
4. Develop the syntax definition file for your format.
5. Ideally, once your familiar with the file format and it's definitions you'll be able to quickly port it (**vim**, **less**, **gedit** and **sublime**).
6. Once you're happy with the results and it's working, submit it to the main bioSyntax repository by placing a "pull request". We'll review the code and add it to the next release.


## Porting bioSyntax to `<$software>`

The choice of text-editors we included is based on our own use. To port bioSyntax to another program or interface:

1. Fork the [bioSyntax repository](fork).
2. Search [bioSyntax Issues](https://github.com/bioSyntax/bioSyntax/issues) for the software port you're interested in.
	- If it exists; Help develop.
	- If it doesn't exist; start an issue for that port.
		a) Title:"PORT: `<$software>`"
		b) Find out and link resources on how syntax-highlighting files are set up for that program
		c) Write syntax definition files for the bioSyntax *core file-types*
3. Once you're happy with the results and it's working, submit it to the main bioSyntax repository by placing a "pull request". We'll review the code and add it to the next release.

## Creating a custom color-theme

If you're particular about how you want everything to look. Feel free to tweak the theme files. If you develop a theme you think is exceptionally good then we'd be happy to see it. Follow the steps for developing a file format and put in a pull request to add it to bioSyntax. 

## Other ways to Collaborate

If you like bioSyntax and would like to help out in other ways, check the [bioSyntax Issues](https://github.com/ababaian/bioSyntax/issues) to see if you can help solve an open problem.  Problems tagged <span style="color: green">`help`</span> are often a good place to start with.

Looking for a side-project to work on? Take on one of the projects from the [bioSyntax TODO](https://github.com/ababaian/bioSyntax/issues).

# Useful Resources

### Regular Expressions

- [How to use Regular Expression](https://www.ugrad.cs.ubc.ca/%7Ecs121/2011W2/Labs/Lab8/lab8.html)
- [Regex Cheatsheet](http://www.rexegg.com/regex-quickstart.html)
- [Ruby Regex Tester](http://rubular.com/)
- [Optimizing Regex](http://www.rexegg.com/regex-optimizations.html)
- [Selecting columns with Regex](https://github.com/ababaian/bioSyntax/issues/17)

### File Specification Files
- [SAM v1.5](https://samtools.github.io/hts-specs/SAMv1.pdf)
- [VCF v4.2](https://samtools.github.io/hts-specs/VCFv4.2.pdf)
- [PDB v3.30](ftp://ftp.wwpdb.org/pub/pdb/doc/format_descriptions/Format_v33_Letter.pdf)
- [UCSC Format Spec.](https://genome.ucsc.edu/FAQ/FAQformat.html)
- [GTF v2.2](http://mblab.wustl.edu/GTF22.html)

# Syntax Development for `less`

Syntax highlighting in **less** is non-standard. We use the **source-highlight** package to accomplish this. 

### Resources
- [**source-highlight** website](https://www.gnu.org/software/src-highlite/)
- [**source-highlight** syntax Documentation](https://www.gnu.org/software/src-highlite/source-highlight.html#Language-Definitions)
- [8-bit ANSI Escape Code Colors](https://en.wikipedia.org/wiki/ANSI_escape_code#8-bit)

### Development

1. Language Definition files are stored in `$SOURCE_HIGHLIGHT_PATH/<language>.lang`
2. Every `<language>.lang` file has an associated `<language>.style` file which assigns the regex variable in `.lang` to color variables in `.outlang`.
3. The main color-theme files are either; `biosyntax.outlang` or `biosyntax-vcf.outlang`. This is the only place where colors are set.
4. Automatic file-extension recognition for less is performed by the `$BIOSYNTAX/less/src-hilite-lesspipe.sh` script. You'll have to add explicit support for a new format.
	
	```
	*.fasta|*.fa|*.mfa)
	source-highlight -f esc --lang-def=fasta.lang --outlang-def=bioSyntax.outlang --style-file=fasta.style -i "$source" ;;
	```
	{: .language-bash}


5. To add pipe-capability in less; `alias` are defined in the users `.bashrc` or `.zshrc`. All bioSyntax aliases can be found in the `$BIOSYNTAX/less/rc_append.txt` file.

	```
	alias fa-less='source-highlight -f esc --lang-def=fasta.lang --outlang-def=bioSyntax.outlang --style-file=fasta.style | less'
	```
	{: .language-bash}

- To maximize compatibility; please limit color use to  Xterm 8-bit (256 colors)
- There is currently a 17-color limit in **source-highlight** as imposed in [colors.h](https://www.gnu.org/software/src-highlite/api/colors_8h_source.html).

# Development for `vim`

**vim** natively supports syntax highlighting.

### Resources
- [Syntax-higlighting in vim](http://vim.wikia.com/wiki/Creating_your_own_syntax_files)
- [Syntax Language Documentation](http://vimdoc.sourceforge.net/htmldoc/syntax.html)
- [Writing a `theme` set for vim](http://andrewradev.com/2011/08/06/making-vim-pretty-with-custom-colors/)

### Development

1. Language Definition files are stored in `<language>.vim` in your vim-syntax folder.
	- Linux/MacOS: `~/.vim/syntax/` folder
	- Windows: `$HOME/vimfiles/syntax/<language>.vim`

2. Ensure Syntax Highlighting is enabled: add `syntax enable` to your `~/.vimrc` file.
3. To make **vim** recognize a file-extension, a `<language>.vim` (the same name as your syntax file) should be placed in `~/.vim/ftdetect/` folder (win:`$HOME/vimfiles/ftdetect`). This file contains a single line to set the filetype on buffer read.
	
	```
	au BufRead,BufNewFile *.stc set filetype=<language>
	```
	{: .language-bash}

4. bioSyntax uses a custom theme file which is stored in `~/.vim/colors/bioSyntax.vim`. All Language Definition files must refer or link to colour-variables defined in this theme file.
	
	```
	# 'ntA' is defined in ~/.vim/colors/bioSyntax.vim
	syntax match ntA "[Aa]"

	# To assign 'ntT' colours to a new variable 'ntI',
	# Define the match then
	syntax match ntI "[Ii]"

	# Link the new variable to the pre-defined color variable
	highlight link ntI ntT

	```
	{: .language-bash}


# Development for `gedit`

**gedit** supports syntax highlighting through the **gtksourceview** library. 

### Resources
- [gtksoureview page](https://wiki.gnome.org/Projects/GtkSourceView)
- [Language Definition v2.0 Tutorial](https://developer.gnome.org/gtksourceview/stable/lang-tutorial.html)
- [Language Definition v2.0 Reference](https://developer.gnome.org/gtksourceview/stable/lang-reference.html)
- [Style Scheme Definition Reference](https://developer.gnome.org/gtksourceview/stable/style-reference.html)

### Development

1. Any Language Definition file for gedit `<language>.lang` should be placed in the gtksourceview language folder
	- Linux: `/usr/share/gtksourceview-3.0/language-specs/<language>.lang`
2. The bioSyntax theme file `bioSyntax.xml` is in the gtksoureview style folder 
	- Linux: `/usr/share/gtksourceview-3.0/styles/bioSyntax.xml`
3. In the header for `bioSyntax.xml`, it will import the parent style `kate.xml`. This can be modified.

# Development for `sublime`

**sublime** has native support for syntax highlighting.

### Resources
- [Syntax Defintion Documentaion](http://www.sublimetext.com/docs/3/syntax.html)
- [Writing Syntax Definitions](http://docs.sublimetext.info/en/latest/extensibility/syntaxdefs.html)
- [Sublime Color scheme](https://forum.sublimetext.com/t/json-syntax-highlighting-does-not-work/7023/6)

### Development

1. To start an example file for a new format: in Sublime > Tools > Developer > New Syntax. The extension of this file should be `<language>.sublime-syntax`.
2. The `<language>.sublime-syntax` file cannot contain any Tabs; everything is space-indented.
3. The `<language>.sublime-syntax` file should be placed in:
- Linux: `~/.config/sublime-text-3/Packages/User`
- Windows: `%APPDATA%/Roaming/Sublime Text 3/Packages/`
- Mac: `~/Library/Application Support/Sublime Text 3/Packages/User/`
4. The language definiton file refers to color definitions as scopes, which are defined in a theme file, `Color Scheme - bioSyntax.sublime-package` in
- Linux: `/opt/sublime_text/Packages/`
- Windows: `C:/Program Files/Sublime Text 3/Packages/`
- Mac: `/Applications/Sublime Text.app/Contents/MacOS/Packages/`

********************************************************

<div style="text-align:center">
	<a href="drawHelix.sh"> <img src="./images/drawHelix.sh.gif" alt="drawHelix.sh"></a>
</div>