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
* [An example](#example)


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

You can find a great introduction for total Shiny beginners [on the Shiny website here](https://shiny.posit.co/getstarted.html). This Shiny intro is detailed; if you take the time to go start to finish, you will learn a lot, but (1) you might not have the time to do that within this course and (2) you might find other resources in combination with parts of this guide helpful, such as the first few Shiny apps in [this repository](https://github.com/tribalxg/PNWTCG2026_shiny_intro/). Then you can see [here in the Quarto dashboard documentation](https://quarto.org/docs/dashboards/interactivity/shiny-r.html) how to adapt R Shiny code when you are using it as part of a Quarto dashboard; make sure to click on the numbered circles along the right side of the code in the Walkthrough section to see their guidance on what each piece is doing.

Keep in mind that mastering Shiny could be a whole course on its own! The purpose of this demo is to help get you started and point you to further resources.

<a name="shiny-basics"/>

### Two basic components

A Shiny app has two basic components:

The user interface (ui) object controls the layout and appearance of your app.

1. The user interface (ui) defines the specific number and [types of user inputs](https://shiny.posit.co/r/getstarted/shiny-basics/lesson3/) such as slider bars, checkboxes, or drop-down menus. It also defines the kinds of [reactive outputs](https://shiny.posit.co/r/getstarted/shiny-basics/lesson4/) in your dashboard/app, outputs that respond/update when the user provides/changes some input. The ui controls the app layout and appearance.
2. The server code contains the code for what the app should do with the user inputs.

[This page of the Quarto documentation](https://quarto.org/docs/interactive/shiny/execution.html#render-server-contexts) summarizes how these two components work in a Quarto document. Make sure to click on the numbered circles along the right side of the code in the Walkthrough section to see their guidance on what each piece is doing.

<a name="shiny-resources"/>

### Further resources

- You can find so many resources for learning R Shiny [here](https://shiny.posit.co/r/articles/)!
- You can find a great introduction for total Shiny beginners [on the Shiny website here](https://shiny.posit.co/getstarted.html). 
- The first few Shiny apps in [this repository](https://github.com/tribalxg/PNWTCG2026_shiny_intro/) are a great hands-on intro.
- You can see [here in the Quarto dashboard documentation](https://quarto.org/docs/dashboards/interactivity/shiny-r.html) how to adapt R Shiny code when you are using it as part of a Quarto dashboard. Make sure to click on the numbered circles along the right side of the code in the Walkthrough section to see their guidance on what each piece is doing.

<a name="integrate"/>

## Integrating R Shiny into your Quarto dashboard

<a name="integrate-where"/>

### Where to put the user inputs in your dashboard

You can add the user inputs (drop-down menus, text boxes, slider bars, and more) in three basic places in your dashboard:

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

<a name="example"/>

## An example

This repo contains the example of converting the static Quarto dashboard generated by the index.qmd file in [the example_quarto_dashboard repo](https://github.com/jpierkunke/example_quarto_dashboard) to a partially interactive dashboard using R Shiny and hosted on shinyapps.io. In other words, we want to go from [this](https://jpierkunke.github.io/example_quarto_dashboard/) to [this](https://jpierkunke.shinyapps.io/example_shiny_quarto_dashboard). They are virtually the same, but we've added interactivity to the right-hand plot on the Results page.

The changes we have to make:

1. In the YAML header, we need to add `server: shiny`.
2. Any code that we want to run at the time that the page is first loaded has to be in a code chunk toward the top with the YAML option `context: setup`. In our case, that means we need to move some code from the first plot code chunk to the setup chunk.
3. We need to add the user inputs somewhere. Since they apply to a single plot in this dashboard, I'll add them as part of the card (a sidebar or a toolbar); in that case, we need to create an input code chunk right before or right after the plot chunk, and that input code chunk has to have the YAML option `content: card-sidebar` or `content: card-toolbar` depending on whether you want the options to appear along the side or along the top/bottom of the plot card.
4. Now I need to split the plot code chunk into two code chunks: one chunk which is part of the shiny ui that specifies the plot output using `plotOutput()`, and another chunk which has the server code that actually generates the plot. Any YAML options that format the plot output should go in the first (ui) code chunk, while the code for the plot as well as the YAML option `context: server` has to go in the second (server) chunk. The plot code is wrapped inside of `output$timeSeriesPlot <- renderPlot({<your plot code here>})`, where `timeSeriesPlot` must match the name of the plot in `plotOutput(timeSeriesPlot)`.
5. In the server code, we need to use the user inputs. If the user input was called `variable_choice` (look at `inputId` which is the object name in the code, not `label` which is the text displayed to the user visiting your site), then you can refer to this input object as `input$variable_choice` in the server code.
5. I've added the YAML options `padding: 0px` to both the plots to remove the white space around them within the card borders. For the interactive plot, that means I have to add this YAML option to the chunk that actually generates the plot with `plotOutput()`.

I've also adjusted the row heights to 60% and 40% instead of 70% and 30% to make the arrangement of plots and table on the page a little nicer.

Here is the resulting code, with comments indicating these changes:

```{r}
```



