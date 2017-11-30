---
layout: page
title: Installing bioSyntax
image:
  feature: abstract-5.jpg
comments: true
modified: 2017-12-01
---
# bioSyntax Installation

We're working on an installer to make this easier, but if you can't wait here's how to get bioSyntax now.

<a href="https://github.com/ababaian/bioSyntax/archive/master.zip"><span class="btn btn-warning">Download bioSyntax</span></a>


1. [sublime](#sublime)
2. [gedit](#gedit)
3. [vim](#vim)
4. [less](#less)


## sublime
(Linux / Mac / Win)

0. Install [Sublime Text](http://www.sublimetext.com/)
1. Download the [bioMonokai Color Scheme](https://github.com/ababaian/bioSyntax/blob/master/dev/theme/sublime/Color%20Scheme%20-%20bioSyntax.sublime-package).
2. Copy it to your Sublime Text application packages folder:
- **Linux**: `../sublime_text_3/Packages/`
- **Windows**: `C:/Program Files/Sublime Text 3/Packages/`
- **Mac**: `/Applications/Sublime Text.app/Contents/MacOS/Packages/`
3. Download the [bioSyntax sublime package](https://github.com/ababaian/bioSyntax/blob/master/syntax/bioSyntax_sublime_RELEASE.zip).
4. Unzip the `*.sublime-syntax` files into the Sublime Text Packages folder:
- **Linux**: `~/.config/sublime-text-3/Packages/User/`
- **Windows**: `%APPDATA%/Roaming/Sublime Text 3/Packages/`
- **Mac**: `/Users/your_username/Library/Application Support/Sublime Text 3/Packages/`
5. Open Sublime Text and go select the bioSyntax (bioMonokai) theme
`Preferences > Color Scheme > bioMonokai`
6. Formats should auto-detect; you can select a specific syntax at the drop-menu at the bottom-right corner of the window (e.g. Plain Text)
7. You now have pretty formats!

## gedit
(Linux / Win)
1. Download the respective `*.lang` files you're interested in

2. Download the `bioKate.xml` style scheme
 
3. Change permissions to all readonly
	`chmod 0644 *.lang`

4. Copy the `bioKate.xml` style scheme to gtksoureview style folder
	`sudo cp bioKate.xml /usr/share/gtksourceview-3.0/styles/bioKate.xml`

5. Copy the `*.lang` file(s) to gtksourceview language spec folder
	`sudo cp fasta.lang /usr/share/gtksourceview-3.0/language-specs/fasta.lang`

6. Restart `gedit` and select the bioSyntax theme
	`Edit > Preferences > Font & Color > bioKate'`
7.  You now have pretty formats!

## vim
(Linux / Mac / Win)

1. Download the the [bioSyntax release](https://github.com/ababaian/bioSyntax/archive/master.zip)

2. Make syntax highlighting folders within your home directory vim folder (`~/.vim`) if they don't exist

	```
	cd ~/.vim
	mkdir -p syntax # ~/.vim/syntax
	mkdir -p ftdetect # ~/.vim/ftdetect
	```
	{: .language-bash}

3. Copy the bioSyntax files into your vim syntax folders

	```
	cp $bioSyntax_PATH/syntax/vim/syntax/*.vim ~/.vim/syntax/
	cp $bioSyntax_PATH/syntax/vim/ftdetect/*.vim ~/.vim/ftdetect/
	```
	{: .language-bash}

4. Enable syntax highlighting within your `~/.vimrc` file by including `syntax enable`:

	```
	echo "syntax enable" >> ~/.vimrc
	```
	{: .language-bash}

5.  You now have pretty formats!


## less
(Linux)

### Install `source-highlight` (Ubuntu)

1. Install `source-highlight` to your system:

	```
	sudo apt-get update
	sudo apt-get install source-highlight
	```
	{: .language-bash}

### Installing `bioSyntax` for less (Ubuntu)

1. Download the the [bioSyntax release](https://github.com/ababaian/bioSyntax/archive/master.zip)

2. Update the `src-hilite-lesspipe.sh` script in the source-highlight directory.

	```
	# source-highlight directory on your system
	SRCDIR='/usr/share/source-highlight'

	cd  $bioSyntax_PATH/syntax/less/

	sudo cp src-hilite-lesspipe_BIO.sh $SRCDIR/src-hilite-lesspipe.sh
	```
	{: .language-bash}

	**Note**: On different systems the `/usr/share/source-highlight/src-hilite-lesspipe.sh` may be installed to a different directory. (i.e CentOS: `export LESSOPEN="| /usr/bin/src-hilite-lesspipe.sh %s"`)

3. Copy over the `*.lang`, `*.outlang` and `*.syntax` files to the source-highlight directory.

	```
	cd  $bioSyntax_PATH/syntax/less/

	# Copy over language files
	sudo cp *.lang $SRCDIR/

	# Copy over style files
	sudo cp *.style $SRCDIR/

	# Copy over output-language files
	sudo cp *.outlang $SRCDIR/
	```
	{: .language-bash}

4. Append these lines (`$bioSyntax_PATH/syntax/less/rc_append.txt`) lines to your `~/.bashrc` and/or `~/.zshrc` 


	```
	cd  $bioSyntax_PATH/syntax/less/
	cat rc_append.txt >> ~/.bashrc
	```
	{: .language-bash}
	or
	```
	## Append this to your ~/.zshrc & ~/.bashrc
	##
	## Syntax Highlighting for less
	export LESSOPEN="| /usr/share/source-highlight/src-hilite-lesspipe.sh %s"
	export LESS=" -R "

	alias less='less -NSi -# 10'
	# -N: add line numbers
	# -S: don't wrap lines (force to single line)
	# -# 10: Horizontal scroll distance

	alias more='less'

	# Explicit call of  <file format>-less for piping data
	# i.e:  samtools view -h aligned_hits.bam | sam-less
	# Core syntaxes (default)
	alias fa-less='source-highlight -f esc --lang-def=fasta.lang --outlang-def=bioSyntax.outlang --style-file=fasta.style | less'
	alias fq-less='source-highlight -f esc --lang-def=fastq.lang --outlang-def=bioSyntax.outlang --style-file=fasta.style | less'
	alias clustal-less='source-highlight -f esc --lang-def=clustal.lang --outlang-def=bioSyntax.outlang --style-file=fasta.style | less'
	alias bed-less='source-highlight -f esc --lang-def=bed.lang --outlang-def=bioSyntax.outlang --style-file=sam.style | less'
	alias sam-less='source-highlight -f esc --lang-def=sam.lang --outlang-def=bioSyntax.outlang --style-file=sam.style | less'
	alias gtf-less='source-highlight -f esc --lang-def=gtf.lang --outlang-def=bioSyntax-vcf.outlang --style-file=vcf.style | less'
	alias vcf-less='source-highlight -f esc --lang-def=vcf.lang --outlang-def=bioSyntax-vcf.outlang --style-file=vcf.style | less'

	# Auxillary syntaxes (uncomment to activate)
	#alias fai-less='source-highlight -f esc --lang-def=faidx.lang --outlang-def=bioSyntax.outlang --style-file=sam.style | less'
	#alias flagstat-less='source-highlight -f esc --lang-def=flagstat.lang --outlang-def=bioSyntax.outlang --style-file=sam.style | less'
	```
	{: .language-bash}

5. Restart your computer for the `rc` files to update.

6. You now have pretty formats!
