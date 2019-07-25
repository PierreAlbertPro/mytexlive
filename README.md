# Introduction
This repository contains a Latex template for thesis manuscripts.

The [UoE branch](https://github.com/PierreAlbertPro/mytexlive/tree/UoE) contains the template for the Precision Medicine DTP. It follows the guidelines from the [Standards for the Format and Binding of a Thesis](https://github.com/PierreAlbertPro/mytexlive/blob/UoE/thesisbinding.pdf).

This repository is a bunch of various LaTeX packages. Since these are only the sources, you need to build them and put them at the right place in order to use them.

The template can be used for two types of documents:
- the manuscript of the thesis itself
- any document required during the PhD: year reports, plans, abstracts, outlines, etc.

Example templates are provided.
The only requirement is to fill in EITHER Document related information OR Thesis information:
- Thesis: 
```
\presentationyear{2020}
\grade{Doctor of Philosophy in Precision Medicine}
```
- Document:
```
\docswitch{document}
\date{\mydate[datestyle=short]{2019-06-20}}
\subtitle{Abstract}
```

# Requirements
- [python3 (version >= 3)](https://www.python.org/downloads/)
- [Latex, e.g. miktex](https://miktex.org/download)

Latex must be registered in the PATH (this should have been set automatically)


# Installation
There is 2 ways of installing the packages.


## Installation with `initexmf`
You might clone the repository anywhere you want and use the following
command.

```
initexmf --register-root=C:\path\to\your\clone
initexmf --update-fndb
```

## Installation in `texmf`
You can clone the repository directly where LaTeX will see it.

### On Linux
You can usually do the following (`~/texmf` folder is read in most default configurations of
LaTeX).

```
git clone -b UoE --single-branch https://github.com/PierreAlbertPro/mytexlive.git ~/texmf
```

If you want to choose a specific path, you can take a look into the file `web2c/texmf.cnf` from your LaTeX installation and look or change the variable `TEXMFHOME`.

Then finally, reconstruct the index.

```
texhash
```

### On Windows
Clone to the path you want to use

```
git clone -b UoE --single-branch https://github.com/PierreAlbertPro/mytexlive.git "C:\path\to\your\clone"
```

Add the path to LaTeX

```
Using MiKTeX:
Start menu -> MiKTeX -> Maintenance -> settings -> Roots -> Add...
Select the root of your folder, e.g. C:\path\to\your\clone
```

Then finally, reconstruct the index.

```
texhash
```



# Build
Build the packages.

Windows:
```
cd C:\path\to\your\clone\tex\latex
python3 update.py
```

Linux:
```
cd ~/texmf/tex/latex
python3 update.py
```

Note:
Some packages require other packages to be built.
Do [install](https://github.com/PierreAlbertPro/mytexlive/tree/UoE#installation) first then try to [build](https://github.com/PierreAlbertPro/mytexlive/tree/UoE#build).
After installation and build, you'll probably need a last update of the LaTeX packages database (`texhash` or `initexmf --update-fndb`).


# Updating
If the template has been updated, the last version can be retrieved using the following steps:
- move to the folder of the template, e.g. 
```
cd C:\path\to\your\clone
```
- retrieve the last version:
```
git pull
```
- update your local template:
```
cd tex/latex
python3 update.py
```