---
layout: page
title: Installing bioSyntax
image:
  feature: rna-banner.jpg
comments: true
modified: 2018-04-11
---
# bioSyntax Installation

<a href="{{ site.owner.release }}"><span class="btn btn-danger">Download bioSyntax</span></a>

bioSyntax comes with a handy installation script. Simply download the latest release and run:

```
bash bioSyntax_INSTALL.sh <editor-of-choice>

# <editors> = vim || less || gedit || sublime
```
{: .language-bash}


**Note**: Some of the installation script requires super-user commands at the moment. If you don't have permissions or don't like this; simply follow the Manual Installation instructions below, but some files will need to be placed in paths accessed via root as well.

## Forking bioSyntax for development

For installing bioSyntax, download the [latest zip release]({{ site.owner.release }}).

To clone/fork the complete bioSyntax repository including development files and submodules, use:

```
git clone --recurse-submodules https://github.com/bioSyntax/bioSyntax.git

# Or if you already cloned it
git submodule update --init
```
{: .language-bash}


# Manual Installation

1. [Sublime](#sublime)
2. [gedit](#gedit)
3. [vim](#vim)
4. [less](#less)

## Sublime
**(Linux / Mac / Win)**

### via Package Control (Easiest, no admin/sudo privileges required):

- Install [Package Control for Sublime](https://packagecontrol.io/installation).
- In Sublime, `Preferences > Package Control > Package Control: Install Package` and search for `bioSyntax`.

### Manual Install (sudo/admin privileges may be required):

0. Install [Sublime Text 3](http://www.sublimetext.com/).

1. Unzip the downloaded bioSyntax release.

	```
	unzip bioSyntax-<release>.zip -d ./bioSyntax/
	```
	{: .language-bash}

2. Copy the `$bioSyntax/sublime/*.sublime-syntax` files into the Sublime *Packages* folder:
- **Linux**: `~/.config/sublime-text-3/Packages/bioSyntax/`
- **Windows**: `~/AppData/Roaming/Sublime\ Text\ 3/Packages/bioSyntax/`
- **Mac**: `~/Library/Application\ Support/Sublime\ Text\ 3/Packages/bioSyntax/`

	```
	cp $bioSyntax/sublime/*.sublime-syntax -d <insert-path>
	```
	{: .language-bash}

3. Copy over the `$bioSyntax/sublime/bioSyntax.tmTheme` theme file

	```
	cp $bioSyntax/sublime/bioSyntax.tmTheme -d <insert-path>
	```
	{: .language-bash}

4. Formats should auto-detect; you can select a specific syntax at the drop-menu at the bottom-right corner of the window (e.g. Plain Text)

5. Restart **Sublime** and you now have pretty formats!


## gedit (sudo/admin privileges may be required):
**(Linux / Win)**

0. Install [Gedit](https://wiki.gnome.org/Apps/Gedit).
1. Unzip the downloaded bioSyntax release.
2. In bioSyntax folder copy gedit style, `$bioSyntax/gedit/bioSyntax.xml`, file to the appropriate gtksourceview styles folder.
- **Linux**: `$HOME/.local/share/gtksourceview-3.0/styles`
- **Windows**: `/c/Program\ Files/gedit/share/gtksourceview-3.0/styles/`

	```
	cp $bioSyntax/gedit/bioSyntax.xml <insert-path>
	```
	{: .language-bash}

3. Copy the gedit `*.lang` files to the appropriate gtksourceview language-spec folder.
- **Linux**: `$HOME/.local/share/gtksourceview-3.0/language-specs`
- **Windows**: `/c/Program\ Files/gedit/share/gtksourceview-3.0/language-specs/`

	```
	cp $bioSyntax/gedit/*.lang <insert-path>
	```
	{: .language-bash}

4. Restart `gedit` and select the bioSyntax theme

	`Edit > Preferences > Font & Color > bioSyntax`

5.  You now have pretty formats!

## vim
**(Linux / Mac / Win)**

### via Pathogen (Easiest installation, may require sudo/admin privileges):

If you have [Pathogen](https://github.com/tpope/vim-pathogen) and [Git](https://git-scm.com/downloads) installed:

```
cd ~/.vim/bundle &&
git clone https://github.com/bioSyntax/bioSyntax-vim.git
```
{: .langauge-bash}

### Manual install

1. Unzip the downloaded bioSyntax release.
2. Find your **vim profile folder**, and make a `syntax`, `ftdetect`, and `colors` directories in it, if they don't exist.
	- **Linux/Mac**: `~/.vim/`
	- **Windows**: `$HOME/vimfiles/`

	```
	# Linux/Mac
	mkdir -p ~/.vim ~/.vim/syntax ~/.vim/ftdetect ~/.vim/colors
	
	# Windows
	mkdir -p $HOME/vimfiles $HOME/vimfiles/syntax $HOME/vimfiles/ftdetect $HOME/vimfiles/colors
	```
	{: .language-bash}

3. Turn on syntax highlighting by default in your vim configuration file. (`~/.vimrc` or `$HOME/_vimrc`)

	```
	# Linux/Mac
	touch ~/.vimrc
	if ! grep -q "syntax enable" ~/.vimrc; then echo "syntax enable\\n" >> ~/.vimrc; fi
	
	# Windows
	touch $HOME/_vimrc
	if ! grep -q ":syntax enable" $HOME/_vimrc; then echo ":syntax enable\\n" >> $HOME/_vimrc; fi
	```
	{: .language-bash}

4. Copy the vim syntax, auto-detection, and colour files from `bioSyntax/vim`  into the respective vim folders:

	```
	# Linux/Mac
	cp $bioSyntax/vim/syntax/*.vim ~/.vim/syntax/
	cp $bioSyntax/vim/ftdetect/*.vim ~/.vim/ftdetect/
	cp $bioSyntax/vim/colors/bioSyntax.vim ~/.vim/colors/
	
	# Windows
	cp $bioSyntax/vim/syntax/*.vim $HOME/.vim/syntax/
	cp $bioSyntax/vim/ftdetect/*.vim $HOME/.vim/ftdetect/
	cp $bioSyntax/vim/colors/bioSyntax.vim $HOME/.vim/colors/
	```
	{: .language-bash}

5. Restart vim and you now have pretty formats!


## less (Hardest installation, sudo privileges may be required)
**(Linux, Mac)**
NOTE: Syntax-highlighting can be turned off using `:syntax off` or removing the `:syntax enable` line from the `.vimrc/_vimrc` file.

0. Ensure that your applications/packages are up-to-date:
- **Linux**: `sudo apt-get update`
- **Mac**: (Installing **source-highlight** is easiest via homebrew. The following updates brew if it is installed; installs it otherwise.)

	```
	# Mac
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
	# Mac
	if [[ ! -z `brew ls --versions "source-highlight"` ]]; then
		brew upgrade source-highlight
	else
		brew install source-highlight
	fi
	```
	{: .language-bash}

2. Unzip the downloaded bioSyntax release, `$bioSyntax`.

3. In the `$bioSyntax/less/` folder, copy the `biosyntax.outlang` and `biosyntax-vcf.outlang` files to the **source-highlight** folder:
- **Linux**: `$HOME/.local/share/source-highlight`
- **Mac**: `/usr/local/opt/source-highlight/share/source-highlight/`

	```
	cp $bioSyntax/less/bioSyntax.outlang <insert-path>
	cp $bioSyntax/less/bioSyntax-vcf.outlang <insert-path>
	```
	{: .language-bash}

4. Copy the bioSyntax language and style definition files (`*.lang` and `*.style`) to same paths as above:

	```
	cp $bioSyntax/less/*.style <insert-path>
	cp $bioSyntax/less/*.lang <insert-path>
	```
	{: .language-bash}

5. Find and replace **source-highlight**'s `src-hilite-lesspipe.sh` script with `$bioSyntax/less/src-hilite-lesspipe_bio.sh`. Make the script executable.

	```
	# Ubuntu
	cp $bioSyntax/less/src-hilite-lesspipe-bio-LINUX.sh \
	$HOME/.local/share/source-highlight/src-hilite-lesspipe-bio.sh

	chmod 755 $HOME/.local/share/source-highlight/src-hilite-lesspipe-bio.sh
	
	# Mac
	cp $bioSyntax/less/src-hilite-lesspipe-bio-MAC.sh \
	/usr/local/bin/src-hilite-lesspipe.sh
	
	chmod 755 /usr/local/bin/src-hilite-lesspipe.sh
	```
	{: .language-bash}

6. In the `$bioSyntax/less/` folder, append the appropriate `*_append.txt` file to your shell configuration file (rc file).
- **Linux**: Use `$bioSyntax/less/rc_append.txt`

	```
	# Check your shell
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
	cat $bioSyntax/less/rc_append.txt >> ~/.zshrc
	```
	{: .language-bash}

- **Mac**: Uses `$bioSyntax/less/bp_append.txt`

	```
	if [ `echo $SHELL` == "/bin/bash" ]; then
		if ! grep -q "bioSyntax" ~/.bashrc; then
			cat $bioSyntax/less/bp_append.txt >> ~/.bashrc;
		fi
	fi
	```
	{: .language-bash}

8. Restart your computer for your rc files to update, open a file with **less** and you now have pretty formats!

#### [Uninstalling bioSyntax :'(](uninstall)
