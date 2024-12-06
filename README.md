# syntenyPlotteR.beta

Updates to syntenyplotteR package - IN ACTIVE DEVELOPMENT

WARNING! These functions are in active development and might contain bugs


## To install:

### Using github

``` r
install.packages("devtools")
library(devtools)
devtools::install_github("Farre-lab/syntenyPlotteR.beta")
library(syntenyPlotteR.beta)
```

------------------------------------------------------------------------

## Input files

### Input Alignment file

**input Alignment file separated by tabs**

DO NOT include a header line

- Reference chromosome ID
- Reference start position
- Reference end position
- Target chromosome
- Target start position
- Target end position
- Orientation
- Reference species ID
- Target species ID

**Example input alignment file format for the functions**

<img src="vignettes/images/example.alignment.input.png" width="521" />

### Chromosome Length file

Please provide a file containing all aligned species in order from
newest species – top of file – to ancestor – end of file, following this
format, separated by tabs

DO NOT include a header line

- Chromosome ID
- Chromosome length
- Species ID

OPTIONAL: 

add a final column with centromere position to add annotation of centromere

**Example file format**

## <img src="vignettes/images/example.lengths.input.png" width="263" />



------------------------------------------------------------------------

## Linear microsynentic alignment style

Recommended for syntenic blocks <30Kbp 

The `draw.microsynteny` plot works similarly to `draw.linear` in the original syntenyPlotteR package (https://github.com/Farre-lab/syntenyPlotteR)

### Usage

``` r
library(syntenyPlotteR.beta)

draw.microsynteny(output,sizefile,...,fileformat = "png",colours = c("red","blue"),w=13,h=5,opacity = .1,curve=.75,thickness=.5)

```

- output - string assigned to the output file name
- sizefile - tab separated file of all chromosome, scaffold, or contig
  lengths and the species identifier, in order from first target species
  in the alignment files followed by the first reference species in the
  alignment files – top of file – to the last target species and
  reference species in the alignment files – end of file.
- … - files containing the syntenic blocks (one file per alignment, in
  order from first target/reference (most recent species pairwise
  alignment in ancestral reconstruction data) alignment file to last
  target/reference (ancestor pairwise alignment in ancestral
  reconstruction data) alignment file)

Please ensure any species identifiers used between length and alignment
files are matching (same identifiers and letter case)

There are optional parameters for some customization of this function:

- fileformat - format for saving the image i.e. png or pdf, parameter
  use: `fileformat = "pdf"` (the default value is “png”)
- colours - colours to assign to the bands between ideograms in a
  concatenated string of chromosome IDs with assigned colour values
  which can be found with R colour Pallette, paramter use:
  `colours = c("1" = "red", "2" = "blue", "3" = "green","4" = "orange", "5" = "purple","X" = "grey")`
  if no colours are assigned default values will be used but colours
  MUST be assigned to all chromosomes
- w - The width of the image created can be changed by using: `w = 5.5`
  (default)
- h - The height of the image created can be changed by using: `h = 10`
  (default)
- opacity - the opacity of the ribbons can be changes using inputting:
  `opacity = .5` (default)
- curve - curvature of syntenic line `curve = .75` (default)
- thickness - thickness of drawn lines `thickness = .5` (default)

**Example code using data files in *inst/extdata/***

``` r
`draw.microsynteny("outputname","test_lengths.txt","test_alignment_1.txt",fileformat = "png",colours = c("red","blue"),w=13,h=5,opacity = .1,curve=.75,thickness=.5)`
```

**Example output**

<img src="vignettes/images/example_linear.png" width="519" />

------------------------------------------------------------------------

## Linear synteny alignment style 2.0

Optimisation for `draw.linear` from the original syntenyPlotteR package (https://github.com/Farre-lab/syntenyPlotteR)

### Usage

``` r
library(syntenyPlotteR.beta)

draw.linear.2.0(output, sizefile, ..., fileformat = "png", colours = colours.default, w=13, h=5, opacity = .5, insert.size = 6000000, chr.label.size = 4, sps.label.size = 7, angle.chr.label = 45, chr.label.height = 0.6)
```

- output - string assigned to the output file name
- sizefile - tab separated file of all chromosome, scaffold, or contig
  lengths and the species identifier, in order from first target species
  in the alignment files followed by the first reference species in the
  alignment files – top of file – to the last target species and
  reference species in the alignment files – end of file.
- … - files containing the syntenic blocks (one file per alignment, in
  order from first target/reference (most recent species pairwise
  alignment in ancestral reconstruction data) alignment file to last
  target/reference (ancestor pairwise alignment in ancestral
  reconstruction data) alignment file)

Please ensure any species identifiers used between length and alignment
files are matching (same identifiers and letter case)

There are optional parameters for some customization of this function:

- fileformat - format for saving the image i.e. png or pdf, parameter
  use: `fileformat = "pdf"` (the default value is “png”)
- colours - colours to assign to the bands between ideograms in a
  concatenated string of chromosome IDs with assigned colour values
  which can be found with R colour Pallette, paramter use:
  `colours = c("1" = "red", "2" = "blue", "3" = "green","4" = "orange", "5" = "purple","X" = "grey")`
  if no colours are assigned default values will be used but colours
  MUST be assigned to all chromosomes
- w - The width of the image created can be changed by using: `w = 5.5`
  (default)
- h - The height of the image created can be changed by using: `h = 10`
  (default)
- opacity - the opacity of the ribbons can be changes using inputting:
  `opacity = .5` (default)
- insert.size - alter the size of the gaps between the chromosomes to allow for more proportional sizes if working with larger or smaller genomes than generally expected `insert_size = 6000000` (default)
- chr.label.size - sizes for the chromosome ID label `chr.label.size = 2` (default)
- sps.label.size - sizes for the species label `sps.label.size = 2` (default)
- angle.chr.label - angle for the chromosome label `angle.chr.label = 45` (default)
- chr.label.height - height of chromosome ID label above chromosome drawing `chr.label.height = 0.2` (default)


**Example code using data files in *inst/extdata/***

``` r
`draw.linear.2.0(output,sizefile,..., fileformat = "png", colours = colours.default, w=13, h=5, opacity = .5,insert.size = 6000000,chr.label.size = 4, sps.label.size = 7, angle.chr.label = 45, chr.label.height = 0.6)`
```

**Example output**

<img src="vignettes/images/example_linear.png" width="519" />

--------------------------------------------------------------------------

### Citation:

Sarah Quigley, Joana Damas, Denis M Larkin, Marta Farré, syntenyPlotteR: a user-friendly R package to visualize genome synteny, ideal for both experienced and novice bioinformaticians, Bioinformatics Advances, Volume 3, Issue 1, 2023, vbad161, https://doi.org/10.1093/bioadv/vbad161
