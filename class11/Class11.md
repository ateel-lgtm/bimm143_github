# Class 11 Protein Structure Prediction with AlphaFold
Austin Teel (PID: A17293709)

- [Background](#background)
- [EBI AlphaFold Database](#ebi-alphafold-database)
- [Running AlphaFold](#running-alphafold)

## Background

In this hands-on session we will utilize AlphaFold to predict protein
structure from sequence (Jumper et al. 2021).

Without the aid of such approaches, it can take years of expensive
laboratory work to determine the structure of just one protein. With
AlphaFold we can now accurately compute a typical protein structure in
as little as ten minutes.

The PDB database (the main repository of experimenyal structures) only
has **~250 thousand** structures (we saw this in the last lab). The main
protein sequence database has over **200 million** sequences! Only
0.125% coverage of known sequences have a known structure- this is
called the “structure knowledge gap”.

``` r
(250000/200000000)*100
```

    [1] 0.125

Structures are much harder to determine than sequences They are
expensive (on average ~\$1million each) They take an average of 3-5
years to solve!

## EBI AlphaFold Database

The EBI has a database of pre computed AlphaFold(AF) models called AFDB.
This is growing all the time and can be usefule to check before running
AF ourselves.

## Running AlphaFold

We can download and run locally (on our our computers) but we need a
GPU. Or we can use “Cloud” computing to run this on someone elses
computers :-).

We will use ColabFold\< https://github.com/sokrypton/ColabFold \>

We previously found there was no AFDB entry for our HIV sequence:

    >HIV-Pr-Dimer
    PQITLWQRPLVTIKIGGQLKEALLDTGADDTVLEEMSLPGRWKPKMIGGIGGFIKVRQYDQILIEICGHKAIGTVLVGPTPVNIIGRNLLTQIGCTLNF:PQITLWQRPLVTIKIGGQLKEALLDTGADDTVLEEMSLPGRWKPKMIGGIGGFIKVRQYDQILIEICGHKAIGTVLVGPTPVNIIGRNLLTQIGCTLNF

Here we will use AlphaFold2_MMseq2
