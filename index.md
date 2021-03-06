---
title       : Titanic Data
subtitle    : 
author      : Kristy Wedel
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides

---
## Titanic Survival Data

## Titanic Disaster
- The Titanic struck an iceburg at 23:40 on Sunday, April 14, 1912
- There were 3547 passengers and crew
<p>
<iframe src = 'https://upload.wikimedia.org/wikipedia/commons/thumb/f/fd/RMS_Titanic_3.jpg/300px-RMS_Titanic_3.jpg', height='600px'></iframe>

---

## Who survived

```r
mosaicplot(Titanic, main = "Survival on the Titanic", color = "blue")
```

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png)

---

## server.R
library(shiny)

data(Titanic)
df <- as.data.frame(Titanic)

shinyServer( function(input, output) {
    output$plot1 <- renderPlot({

        selectedData <- df[df$Class==input$inClass & df$Sex==input$inGender & df$Age==input$inAge,5]
        titanicplot <- barplot(selectedData,
                        main="Titanic Survival Stats",
                        ylab="Total #",
                        col=c("darkorchid1", "darkolivegreen3"),
                        legend = c("Fatalities", "Survivors")
        )
    })

})

---

## Shiny App
Explore the data with the Shiny application located at:
<a href="https://kristywedel.shinyapps.io/TitanicData/">Titanic Shiny App</a>
<iframe src = 'https://kristywedel.shinyapps.io/TitanicData/', height='800px'></iframe>
