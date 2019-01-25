
# Bad Plot 1

```{r}
library(ggplot2)
library(ggthemes)
library(tibble)
library(dplyr)
library(tidyr)
library(stringr)
mtcars <- mtcars
```

**mtcars**

* mpg	Miles/(US) gallon

* cyl	Number of cylinders

* disp	Displacement (cu.in.)

* hp	Gross horsepower

* drat	Rear axle ratio

* wt	Weight (1000 lbs)

* qsec	1/4 mile time

* vs	Engine (0 = V-shaped, 1 = straight)

* am	Transmission (0 = automatic, 1 = manual)

* gear	Number of forward gears

* carb	Number of carburetors


```{r}
mg <- ggplot(mtcars, aes(x = mpg, y = wt)) + geom_point() + facet_grid(vs + am ~ gear)
mg
```

New code:

```{r}
mtcars$gear <- as.character(mtcars$gear)
mtcars$vs <- as.character(mtcars$vs)
mtcars$am <- as.character(mtcars$am)
mtcarsnew <- mtcars %>% mutate(Transmission = str_replace_all(am, c("0" = "Automatic", "1" = "Manual")))
mtcarsnew2 <- mtcarsnew %>% mutate(Engine = str_replace_all(vs, c("0" = "V-shaped", "1" = "Straight")))
mggood <- ggplot(data = mtcarsnew2, aes(x= mpg, y = wt, color = gear, shape=Engine)) + geom_point() + facet_grid(~ Transmission) + labs(title="Car Efficiency", x="Miles per gallon", y="Weight (1000lbs)", color = "Gears") + theme_bw() + scale_colour_colorblind() + theme(legend.position = c(0.79, 0.8), legend.direction = "horizontal", legend.text = element_text(size=6), legend.background = element_rect(colour=NA, fill=NA))
mggood
```

#Bad plot 2

mpg data set

* manufacturer

* model model name

* displ engine displacement, in litres

* year year of manufacture

* cyl number of cylinders

* trans type of transmission

* drv f = front-wheel drive, r = rear wheel drive, 4 = 4wd

* cty city miles per gallon

* hwy highway miles per gallon

* fl fuel type

* class "type" of car

Get standard error the same color, put the legend inside the graph

```{r warning=FALSE}
ds <- ggplot(mpg, aes(displ, hwy, colour = class)) + geom_point() + geom_smooth()
ds
```


New code:

```{r warning = FALSE}
mpg <- mpg
dsnew <- ggplot(mpg, aes(displ, hwy, colour = class)) + geom_point(alpha = 0.3) + geom_smooth(aes(fill = class), alpha=0.15) + theme_bw() + labs(title="Cars", x="Engine Displacement (L)", y="Highway MPG", colour = "Type", fill = "Type")+ scale_colour_colorblind() + scale_fill_colorblind() + theme(legend.position = c(0.64, 0.9), legend.text = element_text(size=6), legend.direction = "horizontal", legend.background = element_rect(colour=NA, fill=NA))
dsnew
```

