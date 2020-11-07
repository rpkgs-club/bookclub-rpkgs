## RStudio

Change git path to `/usr/local/bin` in this JSON file:

```sh
cat ~/.config/rstudio/rstudio-prefs.json
```

```r
lapply(.libPaths(), list.dirs, recursive = FALSE, full.names = FALSE)
```

More on library search see
[4.7 Package libraries](https://r-pkgs.org/package-structure-state.html#library).

For example, on MacOS I have:
```r
.libPaths()
# "/Library/Frameworks/R.framework/Versions/4.0/Resources/library"
```


## Fixes for chapter 2: The whole game

```r
packageVersion("devtools")
## [1] ‘2.3.2’
options(buildtools.check=NULL)
devtools::install_github("r-lib/devtools")
packageVersion("devtools")
# [1] ‘2.3.1.9000’
# after Update Packages
# [1] '2.3.2'
```

```r
library(devtools)
library(tidyverse)
library(fs)

dir_info(all = TRUE) %>% select(path, type)

# dir_info(all = TRUE, regexp = "^[.]git$") %>%
#  select(path, type)
```

## Write the first function

```r
create_package("~/RRR/rpkgs-club/foofactors")
dir_info(all = TRUE) %>% select(path, type)
```

```r
use_git()
use_r()
```
```
✓ Creating 'R/'
● Modify 'R/fbind.R'
● Call `use_test()` to create a matching test file
```

```r
exists("fbind", where = globalenv(), inherits = FALSE)
```

```r
(a <- factor(c("character", "hits", "your", "eyeballs")))
(b <- factor(c("but", "integer", "where it", "counts")))
#> [1] character hits      your      eyeballs
#> Levels: character eyeballs hits your
#> [1] but      integer  where it counts
#> Levels: but counts integer where it
c(a, b)
(a <- factor(c("character", "hits", "your", "eyeballs")))
#> [1] character hits      your      eyeballs
#> Levels: character eyeballs hits your
(b <- factor(c("but", "integer", "where it", "counts")))
#> [1] but      integer  where it counts
#> Levels: but counts integer where it
c(a, b)
#> [1] 1 3 4 2 1 3 4 2```
```

```r
load_all()
fbind(a, b)
check()
```