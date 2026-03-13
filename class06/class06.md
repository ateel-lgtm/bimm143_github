# Class06: R functions
Austin Teel (A17293709)

- [Background](#background)
- [A first function](#a-first-function)
- [A second function](#a-second-function)

## Background

Functions are at the heart of using R. Everything we do involves calling
and using functions (from data input, analysis to results output).

All functions in R have at least 3 things:

1.  A **name** the thing we use to call the function.
2.  One or more input **arguments** that are comma seperated
3.  The **body**, lines of code between curly brackets {} that does the
    work of the function.

## A first function

Let’s write a silly wee function to add some numbers:

``` r
add <- function(x) {
  x+1
}
```

Lets try it out

``` r
add(100)
```

    [1] 101

Will this work

``` r
add( c(100,200,300))
```

    [1] 101 201 301

Modify to be more useful and add more than just 1

``` r
add <- function(x,y=1) {
  x+y
}
```

``` r
add(100,10)
```

    [1] 110

Will this still work

``` r
add(100)
```

    [1] 101

``` r
plot(1:10, col="blue", typ="b")
```

![](class06_files/figure-commonmark/unnamed-chunk-7-1.png)

``` r
log(10, base=10)
```

    [1] 1

> **N.B.** input arguments can be either **required** or **optional**.
> The later have a fall-back default that is specified in the function
> code with an equals sign.

``` r
#add(x=100,y=200,z=300)
```

## A second function

All function sin R look like this

    name <- function(arg) {
    body
    }

The `sample()` function in R takes random samples from the group of
numbers it represents it can be with or without replacement based on the
arguments you give it. It defaults to picking without replacement. Only
need sample amounts and size, the rest is optional.

``` r
sample(1:10,size=4)
```

    [1] 7 6 9 5

> Q. Return 12 numbers picked randomly from the input 1:10

``` r
sample(1:10,size=12, replace=TRUE)
```

     [1]  7  5  2  7  9 10  9  5 10  3 10  7

> Q. Write the code to generate a random 12 nucleotide long DNA
> sequence.

``` r
bases <- c("A","C","G","T")
sample(bases, size=12, replace=TRUE)
```

     [1] "G" "T" "A" "T" "A" "A" "T" "A" "A" "C" "G" "G"

> Q. Write a first version function called `Generate_dna()` that
> generates a user specified length `n` random DNA sequence?

``` r
name <- function(arg){
  
}
```

``` r
generate_dna <- function(n=6) {
  sample(bases, size=n, replace=TRUE)
}
```

``` r
generate_dna(100)
```

      [1] "T" "G" "T" "C" "T" "T" "G" "C" "T" "G" "A" "T" "A" "A" "T" "T" "G" "A"
     [19] "C" "A" "A" "T" "A" "G" "A" "G" "T" "A" "G" "C" "T" "C" "C" "G" "T" "C"
     [37] "C" "T" "A" "T" "A" "T" "G" "C" "G" "G" "C" "G" "C" "G" "A" "T" "G" "C"
     [55] "A" "G" "A" "C" "C" "C" "T" "G" "A" "T" "C" "G" "G" "G" "C" "A" "T" "T"
     [73] "C" "C" "C" "C" "T" "C" "T" "G" "C" "C" "C" "G" "C" "G" "G" "G" "T" "T"
     [91] "G" "A" "T" "A" "C" "C" "C" "T" "C" "A"

> Q. Modify you function ot return a FASTA like sequence so rather than
> \[1\] “T” “A” “G” “T” “C” “G” “C” we want “TAGTCGC”

``` r
generate_dna <- function(n=6) {
  paste(sample(bases, size=n, replace=TRUE),collapse="")
}
```

``` r
generate_dna(100)
```

    [1] "TATTGGGCCCCGCCATCGGGTCATTAGTTCAATTCGGGCCTACAAGCTCGCAAAACCACAATAAACATGCCGATCCTCTTAAGAACATGAAAGAGTTTTT"

> Q. Give the user an option to return FASTA format output sequence or
> standard multi-element vector format?

``` r
generate_dna <- function(n=6, fasta= TRUE) {
  ans <- sample(bases, size=n, replace=TRUE)
  
  if(fasta) {ans <- paste(ans,collapse = "")}
  
return(ans)  

}
```

``` r
generate_dna(20)
```

    [1] "CCAACAACCATGAAGACTGT"

``` r
generate_dna(20,FALSE)
```

     [1] "T" "C" "C" "T" "C" "T" "A" "T" "G" "A" "G" "A" "A" "G" "A" "T" "T" "A" "T"
    [20] "T"

\##A new cool function

> Q. Write a function called `generate_protein()` that generates a user
> specified length protein sequence in FASTA like format?

``` r
aa <- c("A","R","N","D","C","E","Q","G","H","I",
  "L","K","M","F","P","S","T","W","Y","V")

generate_protein <- function(n=6, fasta= TRUE) {


aas <- sample(aa, size=n, replace=TRUE)

  
  if(fasta) {paste(aas,collapse = "")}
return(paste(aas,collapse = ""))
}

generate_protein(10)
```

    [1] "QTCCYPIGIQ"

> Q. Use your new `generate_protein()` function to generate sequences
> between length 6 and 12 amino acids in length and check if any of
> these are unique in nature (i.e. found in the NR database at NCBI)?

``` r
aa <- c("A","R","N","D","C","E","Q","G","H","I",
  "L","K","M","F","P","S","T","W","Y","V")

generate_protein <- function(n=6, fasta= TRUE) {


aas <- sample(aa, size=n, replace=TRUE)

  
  if(fasta) {paste(aas,collapse = "")}
return(paste(aas,collapse = ""))
}

generate_protein(6)
```

    [1] "YPEKDM"

``` r
generate_protein(7)
```

    [1] "STINISD"

``` r
generate_protein(8)
```

    [1] "KANHQWKI"

``` r
generate_protein(9)
```

    [1] "GYSVAMSVG"

``` r
generate_protein(10)
```

    [1] "CARDVDSTKT"

``` r
generate_protein(11)
```

    [1] "HWPNERWYEDI"

``` r
generate_protein(12)
```

    [1] "HYGKNKSNNCRV"

Or we could do a `for()` loop:

``` r
for(i in 6:12){
  cat(">", i, sep="", "\n")
  cat(generate_protein(i),"\n")
}
```

    >6
    KPLHKE 
    >7
    SIQIMSQ 
    >8
    RGIDFGSL 
    >9
    MDKNAHENC 
    >10
    WWTSLANPYL 
    >11
    MWCIDVENCPV 
    >12
    HVTPNKQDMFAS 
