# Making a Quarto dashboard that uses R Shiny for interactivity

Quarto dashboards without R Shiny are static. If you want visitors to your Quarto dashboard site to be able to change settings or otherwise interact with your site, one way to incorporate this kind of interactivity is R Shiny.

To use R Shiny with Quarto dashboards, you'll need to install the following packages if you don't already have them:

```{r}
install.packages("quarto")
install.packages("rmarkdown")
install.packages("shiny")
install.packages("rsconnect")
```

You can add the inputs in three basic places:

1. Vertically along the left or right side of the whole page or of a row (this option is called a sidebar)
2. Horizontally along the top or bottom of the whole page or of a column (this option is called a toolbar)
3. Within a single card (this option is called a card sidebar or card toolbar)

You can read more about these different options [here in the Quarto dashboard documentation on inputs](https://quarto.org/docs/dashboards/inputs.html).

Note that you can use these sections, such as sidebars, without Shiny if you just want to include non-interactive information there; [here's an example of such a dashboard](https://github.com/mine-cetinkaya-rundel/ld-dashboard/blob/main/dashboard.qmd).
