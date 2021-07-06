# Compiled page
https://kthpanor.github.io/echem/docs/intro.html

# Some commands

```
$ pip install -U jupyter-book
$ git clone https://github.com/kthpanor/echem.git
$ cd echem
$ vi docs/dft.md
$ jupyter-book build .
$ open _build/html/index.html
```

**Note**: We need version 0.11 (or higher) to compile our book which is not yet available with `conda install` so therefore do `pip install` as suggested above.

# Publish the html-version

```
$ pip install ghp-import
$ ghp-import -n -p -f _build/html
```

# References
The file `references.bib` in the top directory is a regular BIBTEX file. Add your references in this file. A citation in the text is added with

```
{cite}`Wang2016, Schlegel2011`
```

Multiple lists of references are possible but not yet propoerly implmented.


# Distribution of labour

1. Tutorials and Workflows: TF will get started on this section by setting up a few tutorials on spectroscopy (UV/vis, X-ray);

2. Electronic Structure Theory:
    -  Hartree—Fock theory: PN will move Ch. 4 from overleaf here;
    -  Density functional theory: ZR will move Ch. 5 from overleaf here; will include also a jupyter notebook example for Slater exchange;
    -  Wave-function theory: MD is main responsible and will set up this section (Ch. 6 overleaf) and add “Second quantization”;


3. Potential Energy Surfaces: IB is responsible for this section; will contact ML and MA to ask if they wish/can contribute to the respective subsections;
    -  Molecular structure optimization: IB (Ch. 13 overleaf)
    -  Transition-state theory: AD (Ch. 14 overleaf)
    -  Conical intersections: AD (Ch. 15 overleaf)

4. Molecular dynamics: ML & PN (Ch. 7 overleaf)

5. Properties:
    - Response theory: PN (beta-version done)
    - Algebraic diagrammatic construction: IB (Ch. 10 overleaf)
    - Exciton coupling model: XL (Ch. 11 overleaf)

6. Environment: OV will take main responsibility for this section and will move Ch. 12 from overleaf here, as well as add material on loprop.