Introduction to svatools
================

# svatools

<!-- badges: start -->
<!-- badges: end -->

The goal of svatools is to help with [SWAT+
model](https://swat.tamu.edu/software/plus/) input data preparation,
visualization and model output assessment. There are mostly functions,
which were developed for the implementation of modeling tasks in the
[OPTAIN project](https://www.optain.eu/). These tools are intended to
fill the gaps in the SWAT+ workflow along side the main tools developed
by [Christoph Schuerz](https://www.ufz.de/index.php?en=49467).
Therefore, we highly recommend trying&using these tools:

- [SWATfarmR](http://chrisschuerz.github.io/SWATfarmR/) - R tool for
  preparing management schedules for SWAT model;
- [SWATplusR](https://chrisschuerz.github.io/SWATplusR/articles/SWATplusR.html) -
  R tool for sensitivity analyse, model calibration and validation;
- [SWATbuilder](https://git.ufz.de/users/sign_in) - R tool for building
  SWAT+ setups.

## Installation

You can install the development version of svatools from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("biopsichas/svatools")
devtools::install_github("tkdweber/euptf2")
```

## Data

All the data required to run and test package is installed with package
in extdata folder. Exact location on computer could be found running
lines below. Please run it on your system to get it for you.

``` r
library(svatools)
temp_path <- system.file("extdata", package = "svatools")
print(temp_path)
#> [1] "C:/Users/laptop/AppData/Local/R/win-library/4.2/svatools/extdata"
```

## Templates

In order to use *svatools* package functions with your data you should
prepare your data to be inline with templates we have provided in
*extdata* folder. Such are:

- **calibration_data.xlsx** - template for loading calibration (Q and WQ
  variables) data.
- **weather_data.xlsx** - template for loading weather variables.
- **soil_parameters.xlsx** - template for loading soil parameters
  dataset.
- **GIS** - folder with GIS layers needed to run some functions.

Data prepared according to templates can be directly loaded into R and
all the functions applied as described.

## Example

Simple example to load and display data on one stations indented to be
used in calibration.

``` r
temp_path <- system.file("extdata", "calibration_data.xlsx", package = "svatools")
cal_data <- load_template(temp_path, 4326)
#> [1] "Loading data from template."
#> [1] "Loading of data is finished."
plot_fractions(cal_data$data, station = c("4"), c("PT"), c("P-PO4"))
#> $regretion
```

![](man/figures/README-example-1.png)<!-- -->

    #> 
    #> $fraction

![](man/figures/README-example-2.png)<!-- -->
