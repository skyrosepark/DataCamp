### Labeling and reusing code chunks
1. The first code chunk contains the library() functions, for which no messages are shown in the output document.
2. The second code chunk contains the ggvis and dplyr functions, for which no output is shown; give this code chunk the label chained.
3. The third and last code chunk shows the output of the second code chunk, without the code that generated it. Use the ref.label option.
```
```{r message=FALSE}
library(dplyr)
library(ggvis)
```


```{r chained, results='hide'}
mtcars %>%
  group_by(factor(cyl)) %>%
  ggvis(~mpg, ~wt, fill = ~cyl) %>%
  layer_points()
```
The `ggvis` plot gives us a nice visualization of the `mtcars` data set:

```{r ref.label='chained', echo=FALSE}
```
```
