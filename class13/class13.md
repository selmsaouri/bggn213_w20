Structure Based Drug Design
================

Download and process starting structure
---------------------------------------

Here we download and clean up the HIV-Pr structure (PDB code: 1HSG) from the main PDB database. We will make a separate set of "protein-only" and "ligand-only" PDB files.

``` r
library(bio3d)
file.name <- get.pdb("1hsg")
```

We will use 'read.pdb()', 'atom.select()', and 'write.pdb()' functions to make our separate "protein-only" and "ligand-only" PDB files

``` r
hiv <- read.pdb("1hsg")
```

    ##   Note: Accessing on-line PDB file

``` r
hiv
```

    ## 
    ##  Call:  read.pdb(file = "1hsg")
    ## 
    ##    Total Models#: 1
    ##      Total Atoms#: 1686,  XYZs#: 5058  Chains#: 2  (values: A B)
    ## 
    ##      Protein Atoms#: 1514  (residues/Calpha atoms#: 198)
    ##      Nucleic acid Atoms#: 0  (residues/phosphate atoms#: 0)
    ## 
    ##      Non-protein/nucleic Atoms#: 172  (residues: 128)
    ##      Non-protein/nucleic resid values: [ HOH (127), MK1 (1) ]
    ## 
    ##    Protein sequence:
    ##       PQITLWQRPLVTIKIGGQLKEALLDTGADDTVLEEMSLPGRWKPKMIGGIGGFIKVRQYD
    ##       QILIEICGHKAIGTVLVGPTPVNIIGRNLLTQIGCTLNFPQITLWQRPLVTIKIGGQLKE
    ##       ALLDTGADDTVLEEMSLPGRWKPKMIGGIGGFIKVRQYDQILIEICGHKAIGTVLVGPTP
    ##       VNIIGRNLLTQIGCTLNF
    ## 
    ## + attr: atom, xyz, seqres, helix, sheet,
    ##         calpha, remark, call

Use ?atom.select to read up on this function.

``` r
prot <- atom.select(hiv, "protein", value=TRUE)
lig <- atom.select(hiv, "ligand", value=TRUE)
```

Use ?write.pdb to read up on this function.

``` r
write.pdb(prot, file="1hsg_protein.pdb")
write.pdb(lig, file="1hsg_ligand.pdb")
```

Read docking results
--------------------

Read in the output of docking and make a PDB file for viewing in VMD or Pymol.

``` r
res <- read.pdb("all.pdbqt", multi=TRUE)
write.pdb(res, "results.pdb")
```
