---
title: "Leaflet Map"
author: "RH"
date: "May 7, 2020"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
library(leaflet)
```

## Favorite Coffee Shops

There are many great coffee shops in Rochester, but these 3 are my favorite. Sadly I do not live there anymore. I have lived in several cities since, and have not found a replacement for Glen Edith.  

```{r dataframe}
ge <- c(43.14707, -77.57620)
eg <- c(43.14063, -77.60466)
jv <- c(43.15708, -77.60157)

places <- data.frame(rbind(ge, eg, jv))
colnames(places) <- c("lat", "lng")

texts <- c(
  "<a href='https://www.glenedithcoffee.com/'>Glen Edith (Park Ave location)</a>",
  "<a href='http://equalgrounds.com/'>Equal Grounds</a>",                         
  "<a href='https://www.javascafe.com/'>Java's</a>" 
)
```

```{r map}
cityIcon <- makeIcon(
  iconUrl = "https://i.pinimg.com/originals/fb/bb/55/fbbb55354421bb965454c96dc5de9fb8.png",
  iconWidth = 31*215/230, iconHeight = 31,
  iconAnchorX = 31*215/230/2, iconAnchorY = 16
)

myMap <- leaflet() 
myMap %>% addTiles() %>% addMarkers(lat=places$lat, lng=places$lng, icon=cityIcon, popup=texts)

```