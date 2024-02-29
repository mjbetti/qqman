# qqman: An R package for creating Q-Q and manhattan plots from GWAS results.

[![CRAN_Status_Badge](https://www.r-pkg.org/badges/version/qqman)](https://cran.r-project.org/package=qqman)

[![DOI](https://joss.theoj.org/papers/10.21105/joss.00731/status.svg)](https://doi.org/10.21105/joss.00731)

![qqman.gif](tools/qqman.gif)

## Modifications from original qqman package
I (Michael Betti) have modified the original qqman package to incorporate the following changes to Manhattan plotting:
* Only annotate the top association at each locus, rather than all associations.
* Enlarged the font size of the association annotations.
* Added the option to plot two highlights, each of which can have a custom color rather than the default green in the original code.

The following is an example of how this modified script can be run:
```
pdf("manhattan.pdf", width=15, height=5)
manhattan(gwas_df, 
          col = c("black", "lightblue4"), 
          genomewideline = -log10(1.25e-8),
          suggestiveline = -log10(1.25e-8), 
          annotatePval = 1.25e-8,
          ylim = c(0, 80),
          annotateTop = FALSE,
          highlight = novel,
          highlight2 = lost,
          highlightColor = "red1",
          highlightColor2 = "blue3")
dev.off()
```

...and the following is the resulting Manhattan plot:

![lc_afr_metal_meta_analysis_manhattan_loci_se_highlight_gained_lost](https://github.com/mjbetti/qqman/assets/63562495/61765249-3edd-45e4-9ca2-a1784c15bde0)

## Citation

If you'd like to cite qqman (appreciated but not required), please cite the publication below:

Turner, (2018). qqman: an R package for visualizing GWAS results using Q-Q and manhattan plots. _Journal of Open Source Software_, 3(25), 731, https://doi.org/10.21105/joss.00731

More details are found in the preprint:

Turner, S.D. qqman: an R package for visualizing GWAS results using Q-Q and manhattan plots. [*biorXiv* DOI: 10.1101/005165](https://biorxiv.org/content/early/2014/05/14/005165).

## Installation
This modified package should be installed using devtools:

```coffee
library(devtools)
install_github("mjbetti/qqman")
```

Load the package each time you use it:

```coffee
library(qqman)
```

## Usage

See the [online package vignette](https://cran.r-project.org/web/packages/qqman/vignettes/qqman.html) for more examples:

```coffee
vignette("manhattan")
```

Take a look at the built-in data:

```coffee
head(gwasResults)
```

Basic manhattan plot using built-in data:

```coffee
manhattan(gwasResults)
```

Basic Q-Q plot using built-in data:

```coffee
qq(gwasResults$P)
```

Get help:

```coffee
?manhattan
?qq
```

## Notes

* This release is substantially simplified for the sake of maintainability and creating an R package. The old code that allows confidence intervals on the Q-Q plot and allows more flexible annotation and highlighting is still available at the [version 0.0.0 tag](https://github.com/stephenturner/qqman/tree/v0.0.0).
* Special thanks to Dan Capurso and Tim Knutsen for useful contributions and bugfixes.
* Thanks to all the blog commenters for pointing out bugs and other issues.
