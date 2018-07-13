---
layout: page
title: Uninstall bioSyntax
image:
  feature: rna-banner.jpg
comments: true
modified: 2017-12-22
---

# Uninstall bioSyntax

bioSyntax also comes with an uninstaller script in the release. To use it, run 

```
	#  :'(
	bash bioSyntax_UNINSTALL.sh <editor-of-choice>
```
{: .language-bash}

**Note**: The uninstaller script should also be run from root and requires super-user commands at the moment. If you don't have permissions or don't like this; simply follow the Manual Uninstallation instructions below, but some files will need to be placed in paths accessed via root as well.


If you run into any problems open an [issue on github](https://github.com/bioSyntax/bioSyntax/issues) and we can help.

## sublime
**(Linux / Mac / Win)**

Remove the bioSyntax Color Scheme, `Color Scheme - bioSyntax.sublime-package` from your Sublime Text application packages folder:
- **Linux**: `/opt/sublime_text/Packages/`
- **Windows**: `~/AppData/Roaming/Sublime\ Text\ 3/Packages/User/bioSyntax/`
- **Mac**: `/Applications/Sublime\ Text.app/Contents/MacOS/Packages/`. 

	```
		sudo rm <insert-path>/Color\ Scheme\ -\ bioSyntax.sublime-package
	```
	{: .language-bash}

2. Remove any `*.sublime-syntax` files you no longer want from the Sublime Text Packages folder
- **Linux**: `~/.config/sublime-text-3/Packages/User/`
- **Windows**: `~/AppData/Roaming/Sublime\ Text\ 3/Packages/User/`
- **Mac**: `/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/`

	```
		rm <insert-path>/<filetype>.sublime-syntax
	```
	{: .language-bash}

## gedit
**(Linux / Win)**

1. Remove the bioSyntax style file, `bioSyntax.xml` from the appropriate gtksourceview style folder (depending on your version of Gedit):
- **Linux**: `/usr/share/gtksourceview-3.0/styles/`
- **Windows**: `/c/Program\ Files/gedit/share/gtksourceview-3.0/styles/`

	```
		sudo rm <insert-path>/bioSyntax.xml
	```
	{: .language-bash}

2. Remove any `*.lang` file(s) you no longer want from the appropriate gtksourceview language specs folder (also depends on version of Gedit):
- **Linux**: `/usr/share/gtksourceview-3.0/language-specs/`
- **Windows**: `/c/Program\ Files/gedit/share/gtksourceview-3.0/language-specs/`

	```
		sudo rm <insert-path>/<filetype>.lang
	```
	{: .language-bash}

## vim
**(Linux / Mac / Win)**

1. Remove the bioSyntax color file, `bioSyntax.vim` from your Vim colors folder:

	```
		rm ~/.vim/colors/bioSyntax.vim
	```
	{: .language-bash}

2. Remove any syntax file(s) you no longer want from your Vim syntax folder:

	```
		rm ~/.vim/syntax/<filetype>.vim
	```
	{: .language-bash}

3. Remove corresponding autodetec files from your Vim ftdetect folder:

	```
		rm ~/.vim/ftdetect/<filetype>.vim
	```
	{: .language-bash}

## less
**(Linux / Mac)**

1. Remove the `biosyntax.outlang` and `biosyntax-vcf.outlang` files from your source-highlight folder:
- **Ubuntu**: `/usr/share/source-highlight/`
- **CentOS**: `/usr/bin/`
- **Mac**: `/usr/local/opt/source-highlight/share/source-highlight/`

	```
		sudo rm <insert-path>/biosyntax.outlang
		sudo rm <insert-path>/biosyntax-vcf.outlang
	```
	{: .language-bash}

2. Remove the `*.style` and corresponding `*.lang` file(s) that you no longer want from the paths as above:

	```
		sudo rm <insert-path>/<filetype>.lang
		sudo rm <insert-path>/<filetype>.style
	```
	{: .language-bash}

3. If you wish to uninstall source-highlight for less as well, run the following:

- **Linux**:

	```
		sudo apt-get remove source-highlight
	```
	{: .language-bash}

- **Mac**:

	```
		brew uinstall source-highlight
	```
	{: .language-bash}


