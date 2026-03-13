# Class 19: Cancer mutation mini project
Austin Teel (A17293709)

- [Background](#background)
- [Identifying the protein](#identifying-the-protein)

## Background

I downloaded the Fasta file from the webpage that wa specific to my PID.
I then added it to my class 19 folder so that I could have access to
them in my directory.

> wt_healthy
> MEHQLLCCEVETIRRAYPDANLLNDRVLRAMLKAEETCAPSVSYFKCVQKEVLPSMRKIV
> ATWMLEVCEEQKCEEEVFPLAMNYLDRFLSLEPVKKSRLQLLGATCMFVASKMKETIPLT
> AEKLCIYTDNSIRPEELLQMELLLVNKLKWNLAAMTPHDFIEHFLSKMPEAEENKQIIRK
> HAQTFVALCATDVKFISNPPSMVAAGSVVAAVQGLNLRSPNNFLSYYRLTRFLSRVIKCD
> PDCLRACQEQIEALLESSLRQAQQNMDPKAAEEEEEEEEEVDLACTPTDVRDVDI

> mutant_tumor
> MEHQLLCCEVETIRRAYPDANLLNDRVLRAMLKAEETCAPSVSYFKCVQKEVLPSMRKIV
> ATWMLEVCEEQKCEEEVFPLAMNYLDRFLSLEPVKKSRLQLLGATCMFVASKMKETIPLT
> AEKLCIYTDNSIRPEELLQMELLLVNKLKWNLAAMTPHDFIEHFLSKMPEAEENKQIIRK
> HAQTFVALCATDVKFISNPPSMVAAGSVVAAVQGLNLRSPNNFLSYYRLTRFESRVIKCD
> PRCLRACYEQIEALLESSLRQAQQNMDPKAAEEEEEEEEEVDLACTPTDVRDVDI

## Identifying the protein

To identify the protein I put it into the NCBI BlastP.

I got a match with a protein called G1/S-specific cyclin-D1 \[Homo
sapiens\].Official symbol: CCND1. Sequence ID: NP_444284.1

This protein is an supproessor protein that interacts a lot with
regulation of mitosis and other cell growth events. So when it is over
expressed, mutated, or amplified it can lead to the formation of a
tumor.

> Q2. What are the tumor specific mutations in this particular case
> (e.g. A130V)

``` r
library(bio3d)

a <- read.fasta("A17293709_mutant_seq.fa")
```

``` r
attributes(a)
```

    $names
    [1] "id"   "ali"  "call"

    $class
    [1] "fasta"

``` r
s <- conserv(a)
```

``` r
mutation.position <- which( s != 1 )
mutation.position
```

    [1] 233 242 248

``` r
a$ali[1, mutation.position]
```

    [1] "L" "D" "Q"

``` r
mutation.position
```

    [1] 233 242 248

``` r
a$ali[2, mutation.position]
```

    [1] "E" "R" "Y"

The tumor specific mutations in this particular case are L233E, D242R,
Q248Y

> Q3. What Domain do these mutations reside in?

We can use HMMEr at the EBI (if it works) to find this information

A_CYCLIN_CCND1_rpt2

InterPro Representative Domain 155-287
