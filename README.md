# Incorporating R Shiny into your Quarto dashboard for interactivity

Quarto dashboards without R Shiny are static. If you want visitors to your Quarto dashboard site to be able to change settings or provide input (choose what variables are plotted, for instance), one way to incorporate this kind of interactivity is R Shiny. (Note, though, that some kinds of interactivity like interactive leaflet maps can be implemented in a static Quarto dashboard without R Shiny.)

Table of Contents:

* [Setup](#setup)
* [Getting started with R Shiny](#shiny-start)
    * [Two basic components](#shiny-basics)
    * [Further resources](#shiny-resources)
* [Integrating R Shiny into your Quarto dashboard](#integrate)
    * [Where to put the user inputs in your dashboard](#integrate-where)
    * [Previewing your dashboard as you work on it](#integrate-preview)
    * [Deploying/publishing your dashboard online](#integrate-deploy)


<a name="setup"/>

## Setup

To use R Shiny with Quarto dashboards, you'll need to install the following packages if you don't already have them:

```{r}
install.packages("quarto")
install.packages("rmarkdown")
install.packages("shiny")
install.packages("rsconnect")
```

R Shiny also requires using a service outside of GitHub to host your app. There are many options, but for this demo we'll use shinyapps.io. You'll also need to make an account on shinyapps.io if you don't already have one; [see instructions here](https://shiny.posit.co/r/articles/share/shinyapps/).


<a name="shiny-start"/>

## Getting started with R Shiny

There are a lot of great resources on R Shiny, and it's important to get some familiarity with it before you try to incorporate it into your dashboard. Just keep in mind that it looks a little different when you incorporate it into a Quarto dashboard.

<a name="shiny-basics"/>

### Two basic components


<a name="shiny-resources"/>

### Further resources


<a name="integrate"/>

## Integrating R Shiny into your Quarto dashboard

<a name="integrate-where"/>

### Where to put the user inputs in your dashboard

You can add the user inputs (drop-down menus, text boxes, slidebars, and more) in three basic places in your dashboard:

1. Vertically along the left or right side of the whole page or of a row (this option is called a sidebar)
2. Horizontally along the top or bottom of the whole page or of a column (this option is called a toolbar)
3. Within a single card (this option is called a card sidebar or card toolbar)

You can read more about these different options [here in the Quarto dashboard documentation on inputs](https://quarto.org/docs/dashboards/inputs.html).

Note that you can use these sections, such as sidebars, without Shiny if you just want to include non-interactive information there; [here's an example of such a dashboard](https://github.com/mine-cetinkaya-rundel/ld-dashboard/blob/main/dashboard.qmd).

<a name="integrate-preview"/>

### Previewing your dashboard as you work on it

When you are developing your dashboard and you want to preview it, you can do one of the following three steps which all do the same thing:

1. Click the "Run Document" button in R Studio.
2. In the Console, type `quarto::quarto_serve("document.qmd")` (replace document.qmd with your actual filename).
3. In the Terminal, type `quarto serve document.qmd` (replace document.qmd with your actual filename).

This doesn't publish or update your interactive dashboard online; it just shows you a local preview.

<a name="integrate-deploy"/>

### Deploying/publishing your dashboard online

Note that deployment is a bit different for an R Shiny app ([see these instructions](https://shiny.posit.co/r/articles/share/shinyapps/)) than for a Quarto dashboard that incorporates R Shiny ([see these instructions](https://quarto.org/docs/interactive/shiny/running.html#shinyapps)).

Before deployment, make sure you have installed the necessary packages and set up a shinyapps.io account as in the Setup section above.

To deploy your dashboard, first click the "Run Document" button, then either click the "Publish" button or type `quarto::quarto_publish_app(server = "shinyapps.io")` into the Console.
