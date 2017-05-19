### Labeling and reusing code chunks
1. The first code chunk contains the library() functions, for which no messages are shown in the output document.
2. The second code chunk contains the ggvis and dplyr functions, for which no output is shown; give this code chunk the label chained.
3. The third and last code chunk shows the output of the second code chunk, without the code that generated it. Use the ref.label option.

```
{r message=FALSE}
library(dplyr)
library(ggvis)
```

```
{r chained, results='hide'}
mtcars %>%
  group_by(factor(cyl)) %>%
  ggvis(~mpg, ~wt, fill = ~cyl) %>%
  layer_points()
```

The `ggvis` plot gives us a nice visualization of the `mtcars` data set:

```
{r ref.label='chained', echo=FALSE}
```

[example](https://rpubs.com/potentialwjy/Rmarkdown2)

[reference](http://www.rstudio.com/wp-content/uploads/2015/03/rmarkdown-reference.pdf)


### Specify knitr and pandoc options
The YAML header below overwrites the default code highlight style of the pdf_document template to create a document that uses the zenburn style:
```
---
title: "Demo"
output:
  pdf_document:
    highlight: zenburn
---
```

The YAML header below overwrites the default bootstrap CSS theme of the html_document template.
```
---
title: "Demo"
output:
  html_document:
    theme: spacelab
---
```

Add a table of contents
```
---
title: "Ozone"
author: "Anonymous"
date: "January 1, 2015"
output: 
  html_document :
    toc : true
    number_sections : true
---
```
주의 : 'true' should be lower case.
