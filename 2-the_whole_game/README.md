## RStudio

Change git path to `/usr/local/bin` in this JSON file:

```
~/.config/rstudio/rstudio-prefs.json
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