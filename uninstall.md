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



**Note**: Some of the script may require sudo/admin privileges at the moment. If you don't have permissions or don't like this; simply follow the Manual Uninstallation instructions below, but some files will need to be placed in paths accessed via root as well. For Windows, the script runs best with the [Git Bash terminal](https://git-scm.com/downloads), which may be required to be run as an administrator.

## sublime (sudo/admin privileges may be required):
**(Linux / Mac / Win)**

Remove the bioSyntax folder from the Packages folder of Sublime Text 3:
- **Linux**: `~/.config/sublime-text-3/Packages/bioSyntax/`
- **Windows**: `~/AppData/Roaming/Sublime\ Text\ 3/Packages/bioSyntax/`
- **Mac**: `~/Library/Application\ Support/Sublime\ Text\ 3/Packages/bioSyntax/`. 

	```
		rm -r <insert-path>
	```
	{: .language-bash}

## gedit (sudo/admin privileges may be required):
**(Linux / Win)**

1. Remove the bioSyntax style file, `bioSyntax.xml` from the appropriate gtksourceview style folder (depending on your version of Gedit):
- **Linux**: `"HOME/.local/share/gtksourceview-3.0/styles/`
- **Windows**: `/c/Program\ Files/gedit/share/gtksourceview-3.0/styles/`

	```
		rm <insert-path>/bioSyntax.xml
	```
	{: .language-bash}

2. Remove any `*.lang` file(s) you no longer want from the appropriate gtksourceview language specs folder (also depends on version of Gedit):
- **Linux**: `$HOME/.local/share/gtksourceview-3.0/language-specs`
- **Windows**: `/c/Program\ Files/gedit/share/gtksourceview-3.0/language-specs/`

	```
		rm <insert-path>/<filetype>.lang
	```
	{: .language-bash}

## vim
**(Linux / Mac / Win)**

### via Pathogen (sudo/admin privileges may be required):

Remove the `bioSyntax-vim` Git repo from the bundles folder in your vim folder:
- **Linux/Mac**: `~/.vim/bundles/bioSyntax-vim`
- **Windows**: `$HOME/vimfiles/bundles/bioSyntax-vim`

	```
		rm -r <insert-path>
	```
	{: .language-bash}

### Manually (sudo/admin privileges may be required):

1. Remove the bioSyntax color file, `bioSyntax.vim` from your Vim colors folder:
- **Linux/Mac**: `~/.vim/colors`
- **Windows**: `$HOME/vimfiles/colors`

	```
		rm <insert-path>/bioSyntax.vim
	```
	{: .language-bash}

2. Remove any syntax file(s) you no longer want from your Vim syntax folder:
- **Linux/Mac**: `~/.vim/syntax`
- **Windows**: `$HOME/vimfiles/syntax`

	```
		rm <insert-path>/<filetype>.vim
	```
	{: .language-bash}

3. Remove corresponding autodetect files from your Vim ftdetect folder:
- **Linux/Mac**: `~/.vim/ftdetect`
- **Windows**: `$HOME/vimfiles/ftdetect`

	```
		rm <insert-path>/<filetype>.vim
	```
	{: .language-bash}

## less (sudo/admin privileges may be required):
**(Linux / Mac)**

1. Remove the `bioSyntax.outlang` and `bioSyntax-vcf.outlang` files from your source-highlight folder:
- **Linux**: `$HOME/.local/share/source-highlight`
- **Mac**: `/usr/local/opt/source-highlight/share/source-highlight/`

	```
		rm <insert-path>/bioSyntax.outlang
		rm <insert-path>/bioSyntax-vcf.outlang
	```
	{: .language-bash}

2. Remove the `*.style` and corresponding `*.lang` file(s) that you no longer want from the paths as above:

	```
		rm <insert-path>/<filetype>.lang
		rm <insert-path>/<filetype>.style
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


