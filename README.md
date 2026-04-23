# Making a Quarto dashboard that uses R Shiny for interactivity

Quarto dashboards without R Shiny are static. If you want visitors to your Quarto dashboard site to be able to change settings or provide input (choose what variables are plotted, for instance), one way to incorporate this kind of interactivity is R Shiny. (Note that some kinds of interactivity like interactive leaflet maps can be implemented in a static Quarto dashboard without R Shiny.)

To use R Shiny with Quarto dashboards, you'll need to install the following packages if you don't already have them:

```{r}
install.packages("quarto")
install.packages("rmarkdown")
install.packages("shiny")
install.packages("rsconnect")
```

You can add the user inputs (drop-down menus, text boxes, slidebars, and more) in three basic places in your dashboard:

1. Vertically along the left or right side of the whole page or of a row (this option is called a sidebar)
2. Horizontally along the top or bottom of the whole page or of a column (this option is called a toolbar)
3. Within a single card (this option is called a card sidebar or card toolbar)

You can read more about these different options [here in the Quarto dashboard documentation on inputs](https://quarto.org/docs/dashboards/inputs.html).

Note that you can use these sections, such as sidebars, without Shiny if you just want to include non-interactive information there; [here's an example of such a dashboard](https://github.com/mine-cetinkaya-rundel/ld-dashboard/blob/main/dashboard.qmd).

When you are developing your dashboard and you want to preview it, you can do one of the following three steps which all do the same thing:

1. Click the "Run Document" button in R Studio.
2. In the Console, type `quarto::quarto_serve("document.qmd")` (replace document.qmd with your actual filename).
3. In the Terminal, type `quarto serve document.qmd` (replace document.qmd with your actual filename).
