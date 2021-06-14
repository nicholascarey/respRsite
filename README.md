
[![GitHub R package version](https://img.shields.io/github/r-package/v/januarharianto/respR)](https://github.com/januarharianto/respR)
[![Travis (.com)](https://img.shields.io/travis/com/januarharianto/respR?label=Travis-CI)](https://travis-ci.org/github/januarharianto/respR)
[![Codecov](https://codecov.io/gh/januarharianto/respR/branch/master/graph/badge.svg)](https://app.codecov.io/gh/januarharianto/respR)
[![License](https://img.shields.io/badge/license-GPL--3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0.en.html)
[![Github Star](https://img.shields.io/github/stars/januarharianto/respR?style=social)](https://GitHub.com/januarharianto/respR/stargazers/)
[![Github watchers](https://img.shields.io/github/watchers/januarharianto/respR?label=Watch&style=social)](https://img.shields.io/github/watchers/januarharianto/respR?style=social)
[![Twitter](https://img.shields.io/twitter/follow/respR_pkg.svg?label=Follow&style=social)](https://twitter.com/respR_pkg?ref_src=twsrc%5Etfw)


## <font style="font-family:'Courier New'">respR : A package for processing and analysing respirometry data</font> 

`respR` is a package for `R` that provides a structural, reproducible workflow for the processing and analysis of respirometry data. 
While the focus of the package is on aquatic respirometry, `respR` is largely unitless and so can process, explore, and determine rates from any respirometry data, and indeed linear relationships in any time-series data.

Use `respR` to:

- Automatically **import** raw data from various oxygen sensing equipment
- Rapidly **inspect** data for common issues before analysis
- **Explore** and **visualise** timeseries data
- Perform **multiple regression analysis** on linear segments of data manually or automatically to calculate rates
- **Adjust** rates for background oxygen consumption or production
- **Convert** rates to any common unit of oxygen consumption or production
- **Export** results quickly for reporting

The package has also been [**peer reviewed and published**](https://besjournals.onlinelibrary.wiley.com/doi/10.1111/2041-210X.13162) in *Methods in Ecology and Evolution*. Please cite this publication if you use `respR` in your published work. If you don't have the space, or feel you haven't used it enough to justify a citation, not a problem, but please do [**let us know**](mailto:nicholascarey@gmail.com) anyway. We would like to keep track of studies which have found `respR` useful, and we can help publicise your research, and add to the list [here]() of papers which have used it. 

We also have a [**Twitter account**](https://twitter.com/respR_pkg). Please follow for latest news and regular updates from the world of respirometry!

## Installation
`respR` will be submitted soon to CRAN. For now, use the `devtools` package to install the latest stable version:

```r
install.packages("devtools")
devtools::install_github("januarharianto/respR")
```

## Getting started

See `vignette("respR")` to get started.

## Usage

For a quick evaluation of the package, try out the following code:

```r
library(respR) # load the package

# 1. check data for errors, select cols 1 and 15:
urch <- inspect(urchins.rd, time = 1, oxygen = 15) 
# 2. automatically determine linear segment:
rate <- auto_rate(urch)
# 3. convert units
out <- convert_rate(rate, 
                    o2.unit = "mg/L", 
                    time.unit = "min", 
                    output.unit = "mg/h/kg", 
                    volume = 0.6, 
                    mass = 0.4)
print(out)

## Alternatively, use pipes:
urchins.rd %>%        # using the urchins dataset,
  select(1, 15) %>%   # select columns 1 and 15
  inspect()     %>%   # inspect the data, then
  auto_rate()   %>%   # automatically determine most linear segment
  print()       %>%   # a quick preview
  convert_rate("mg/L", "min", "mg/h/kg", 0.6, 0.4) # convert to units
```

## Feedback and contributions

`respR` is under continuous development. If you have any bugs or feedback, you can contact us easily by [opening an issue](https://github.com/januarharianto/respr/issues). Alternatively, you can fork this project and create a pull request.

Please also feel free to [**email**](mailto:nicholascarey@gmail.com) with any feedback or problems you may encounter.

## Developers

- [**Januar Harianto**](https://github.com/januarharianto), University of Sydney
- [**Nicholas Carey**](https://github.com/nicholascarey), Scottish Association of Marine Science


## See also

These packages may also help you analyses your respirometry data:

- [respirometry](https://cran.r-project.org/package=respirometry) - Matthew A. Birk
- [rMR](https://cran.r-project.org/package=rMR) - Tyler L. Moulton
- [FishResp](https://fishresp.org) - Sergey Morozov
- [LoLinR](https://github.com/colin-olito/LoLinR) - Colin Olito and Diego Barneche
- [segmented](https://cran.r-project.org/package=segmented) - Vito M. R. Muggeo


## References

Clark, T. D., Sandblom, E., & Jutfelt, F. (2013). Aerobic scope measurements of fishes in an era of climate change: respirometry, relevance and recommendations. Journal of Experimental Biology, 216(15), 2771–2782. [doi: 10.1242/Jeb.084251](https://doi.org/10.1242/Jeb.084251)

Gamble, S., Carton, A. G., & Pirozzi, I. (2014). Open-top static respirometry is a reliable method to determine the routine metabolic rate of barramundi, Lates calcarifer. Marine and Freshwater Behaviour and Physiology, 47(1), 19–28. [doi: 10.1080/10236244.2013.874119](https://doi.org/10.1080/10236244.2013.874119)

Leclercq, N., Gattuso, J.-P. & Jaubert, J. (1999). Measurement of oxygen metabolism in open-top aquatic mesocosms: Application to a coral reef community. Marine Ecology Progress Series, 177, 299–304. [doi: 10.3354/meps177299](https://doi.org/10.3354/meps177299)

Lighton, J.R.B. (2008). Measuring Metabolic Rates: A Manual for Scientists. Oxford University Press, USA.

Morozov S., McCairns R.J.S., Merilä J. (2019) FishResp: R package and GUI application for analysis of aquatic respirometry data. Conservation Physiology 7(1). [doi:10.1093/conphys/coz003](https://doi.org/10.1093/conphys/coz003)

Muggeo, V.M.R. (2003). Estimating regression models with unknown break-points. Statistics in Medicine, 22, 3055–3071. [doi: 10.1002/sim.1545](https://doi.org/10.1002/sim.1545)

Muggeo, V. (2008). Segmented: An R package to fit regression models with broken-line relationships. R News, 8, 20–25.

Silverman, B.W. (1986). Density Estimation for Statistics and Data Analysis. Chapman; Hall/CRC Press.

Steffensen, J. F. (1989). Some errors in respirometry of aquatic breathers: How to avoid and correct for them. Fish Physiology and Biochemistry, 6(1), 49–59. [doi: 10.1007/BF02995809](https://doi.org/10.1007/BF02995809)

Svendsen, M.B.S., Bushnell, P.G. & Steffensen, J.F. (2016). Design and setup of intermittent-flow respirometry system for aquatic organisms. Journal of Fish Biology, 88, 26–50. [doi: 10.1111/jfb.12797](https://doi.org/10.1111/jfb.12797)

White, C.R. & Kearney, M.R. (2013). Determinants of inter-specific variation in basal metabolic rate. Journal of Comparative Physiology B: Biochemical, Systemic, and Environmental Physiology, 183, 1–26. [doi: 10.1007/s00360-012-0676-5](https://doi.org/10.1007/s00360-012-0676-5)

Yeager, D.P. & Ultsch, G.R. (1989). Physiological regulation and conformation: A BASIC program for the determination of critical points. Physiological Zoology, 62, 888–907. [doi: 10.1086/physzool.62.4.30157935](https://doi.org/10.1086/physzool.62.4.30157935)
