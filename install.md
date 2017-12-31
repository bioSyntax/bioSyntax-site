---
layout: page
title: Installing bioSyntax
image:
  feature: rna-banner.jpg
comments: true
modified: 2017-12-22
---
# bioSyntax Installation

<a href="{{ site.owner.release }}"><span class="btn btn-danger">Download bioSyntax</span></a>

bioSyntax comes with a handy installation script. Simply download the latest release and run:

```
	bash bioSyntax_SETUP.sh <editor-of-choice>

	# <editors> = vim || less || gedit || sublime
```
{: .language-bash}


**Note**: The installation script should be run from root and requires super-user commands at the moment. If you don't have permissions or don't like this; simply follow the Manual Installation instructions below, but some files will need to be placed in paths accessed via root as well.

# Manual Installation

1. [Sublime](#sublime)
2. [gedit](#gedit)
3. [vim](#vim)
4. [less](#less)

## Sublime
**(Linux / Mac / Win)**

0. Install [Sublime Text 3](http://www.sublimetext.com/).

1. Unzip the downloaded bioSyntax release.

	```
	unzip bioSyntax-<release>.zip -d ./bioSyntax/
	```
	{: .language-bash}

2. In the `bioSyntax/sublime` folder rename the `Color%20Scheme%20-%20bioSyntax.sublime-package` file to `Color Scheme - bioSyntax.sublime-package`.

	```
	mv Color%20Scheme%20-%20bioSyntax.sublime-package \
	   Color\ Scheme\ -\ bioSyntax.sublime-package
	```
	{: .language-bash}

3. Copy the bioSyntax theme to your **Sublime** *Application* folder:
- **Linux**: `/opt/sublime_text/Packages/`
- **Mac**: `/Applications/Sublime\ Text.app/Contents/MacOS/Packages/`

	```
	sudo cp Color\ Scheme\ -\ bioSyntax.sublime-package <insert-path>
	```
	{: .language-bash}

4. Copy the `$bioSyntax/sublime/*.sublime-syntax` files into the Sublime *Packages* folder:
- **Linux**: `~/.config/sublime-text-3/Packages/User/`
- **Windows**: `~/AppData/Roaming/Sublime\ Text\ 3/Packages/User/`
- **Mac**: `/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/`

	```
	cp $bioSyntax/*.sublime-syntax -d <insert-path>
	```
	{: .language-bash}


5. Restart **Sublime** and select the bioSyntax (bioMonokai) theme.
	`Preferences > Color Scheme > bioMonokai`

6. Formats should auto-detect; you can select a specific syntax at the drop-menu at the bottom-right corner of the window (e.g. Plain Text)

7. You now have pretty formats!

We're working on adding bioSyntax intallation via Sublime's Package Control. (NOT IMPLEMENTED YET)
- Install [Package Control for Sublime](https://packagecontrol.io/installation).
- Once installed, in Sublime, go to `Preferences > Package Control > Package Control: Install Package` and search for `BioSyntax`, and click on it. Package Control will install the syntax files for you.
If not, follow the manual installation instructions below:


## gedit
**(Linux / Win)**

0. Install [Gedit](https://wiki.gnome.org/Apps/Gedit).
1. Unzip the downloaded bioSyntax release.
2. In bioSyntax folder copy gedit style, `$bioSyntax/gedit/bioSyntax.xml`, file to the appropriate gtksourceview styles folder.
- **Linux**: `/usr/share/gtksourceview-3.0/styles/`
- **Windows**: `/c/Program\ Files/gedit/share/gtksourceview-3.0/styles/`

	```
	sudo cp $bioSyntax/gedit/bioSyntax.xml <insert-path>
	```
	{: .language-bash}

3. Copy the gedit `*.lang` files to the appropriate gtksourceview language-spec folder.
- **Linux**: `/usr/share/gtksourceview-3.0/language-specs/`
- **Windows**: `/c/Program\ Files/gedit/share/gtksourceview-3.0/language-specs/`

	```
	sudo cp $bioSyntax/gedit/*.lang <insert-path>
	```
	{: .language-bash}

4. Restart `gedit` and select the bioSyntax theme
	`Edit > Preferences > Font & Color > bioSyntax'`

5.  You now have pretty formats!

## vim
**(Linux / Mac / Win)**

### via Pathogen

If you have [Pathogen](https://github.com/tpope/vim-pathogen) installed:

	```
	cd ~/.vim/bundle && \
	git clone https://github.com/tpope/vim-sensible.git
	```
	{: .langauge-bash}

### Manual instructions

1. Unzip the downloaded bioSyntax release.
2. Find your **vim profile folder**, and make a `syntax`, `ftdetect`, and `colors` directories in it, if they don't exist.
	- **Linux/Mac**: `~/.vim/`
	- **Windows**: `$HOME/vimfiles/`

	```
	# Linux/Mac
	mkdir -p ~/.vim ~/.vim/syntax ~/.vim/ftdetect ~/.vim/colors
	```
	{: .language-bash}

3. Turn on syntax highlighting by default in your vim configuration file. (`~/.vimrc` or `$HOME/_vimrc`)

	```
	# Linux/Mac
	touch ~/.vimrc
	if ! grep -q "syntax enable" ~/.vimrc; then echo "syntax enable\\n" >> ~/.vimrc; fi
	```
	{: .language-bash}

4. Copy the vim syntax, auto-detection, and colour files from `bioSyntax/vim`  into the respective vim folders:

	```
	cp $bioSyntax/vim/*.vim ~/.vim/syntax/
	cp $bioSyntax/vim/ftdetect/*.vim ~/.vim/ftdetect/
	cp $bioSyntax/vim/colors/bioSyntax.vim ~/.vim/colors/
	```
	{: .language-bash}

5. Restart vim and you now have pretty formats!


## less
**(Linux, Mac)**

0. Ensure that your applications/packages are up-to-date:
- **Linux**: `sudo apt-get update`
- **Mac**: (Installing **source-highlight** is easiest via homebrew. The following updates brew if it is installed; installs it otherwise.)

	```
	which -s brew
	if [[ $? != 0 ]] ; then
    	ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
	else
    	brew update
	fi
	```
	{: .language-bash}

1. Install [**source-highlight**](https://www.gnu.org/software/src-highlite/) to your system:
- **Linux**: `sudo apt-get install source-highlight`
- **Mac**: (install/update via brew)

	```
	if [[ ! -z `brew ls --versions "source-highlight"` ]]; then
		brew upgrade source-highlight
	else
		brew install source-highlight
	fi
	```
	{: .language-bash}

2. Unzip the downloaded bioSyntax release, `$bioSyntax`.

3. In the `$bioSyntax/less/` folder, copy the `biosyntax.outlang` and `biosyntax-vcf.outlang` files to the **source-highlight** folder:
- **Linux**: `/usr/share/source-highlight/`
- **Mac**: `/usr/local/opt/source-highlight/share/source-highlight/`

	```
	sudo cp $bioSyntax/less/biosyntax.outlang <insert-path>
	sudo cp $bioSyntax/less/biosyntax-vcf.outlang <insert-path>
	```
	{: .language-bash}

4. Copy the bioSyntax language definition `*.lang` and style definition `*.style` files to the paths as above:

	```
	sudo cp $bioSyntax/less/*.style <insert-path>
	sudo cp $bioSyntax/less/*.lang <insert-path>
	```
	{: .language-bash}

5. Find where **source-highlight** installed its `src-hilite-lesspipe.sh` script, and replace it with `$bioSyntax/less/src-hilite-lesspipe_BIO.sh`. Make the script executable.

	```
	# Ubuntu
	sudo cp $bioSyntax/less/src-hilite-lesspipe_BIO.sh \
	        /usr/share/source-highlight/src-hilite-lesspipe.sh

	sudo chmod 755 /usr/share/source-highlight/src-hilite-lesspipe.sh
	```
	{: .language-bash}

6. In the `$bioSyntax/less/` folder, append the appropriate `*_append.txt` file to your shell configuration file (rc file).
- **Linux**: Uses `$bioSyntax/less/rc_append.txt`

	```
	echo $SHELL
	# Outputs:
	'          $SHELL            $RCFILE '
	#         /bin/zsh    -->   ~/.zshrc
	#         /bin/sh     -->   ~/.shrc
	#         /bin/bash   -->   ~/.bashrc
	#         ...
	```
	{: .language-bash}

	```
	cat $bioSyntax/less/rc_append.txt >> $RCFILE
	```
	{: .language-bash}

- **Mac**: Uses `$bioSyntax/less/bp_append.txt`

	```
	if [ `echo $SHELL` == "/bin/bash" ]; then
		if ! grep -q "bioSyntax" ~/.bashrc; then
			cat $bioSyntax/less/bp_append.txt >> ~/.bashrc;
		fi
	fi

	# ...
	```
	{: .language-bash}

8. Restart your computer for your rc files to update, open a file with **less** and you now have pretty formats!


#### [Uninstalling bioSyntax](uninstall)
