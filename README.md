# TidyTuesday
A compilation of several data visualization challenges using data organized by #TidyTuesday.

The first example of my work is a replication of a DuBois graph for #TidyTuesday on 2/16/2021.

```{r, echo = FALSE}
library(tidyverse)
library(ggplot2)
library(ggtext)
library(extrafont)
library(readr)
knitr::opts_chunk$set(echo = TRUE, fig.path = "plots/", fig.width = 8, fig.height =5)
tuesdata <- tidytuesdayR::tt_load(2021, week = 8)
freed_slaves <- tuesdata$freed_slaves
windowsFonts(Charter = windowsFont("Charter"))

a <- ggplot(fr_sl, aes(x=factor(Year), y=Free, group = 1)) +
  
  #Remove x- and y-axis labels
  
  geom_line(size = 0.25) + xlab("") + ylab("") + 
  
  #Fill the area underneath the curve green and the rest of the plot background black to mimic DuBois color design
  #Remove gridlines
  
  geom_area(fill = "forestgreen") +
  theme(axis.text = element_blank(),
        axis.ticks = element_blank(),
        panel.background = element_rect(fill = "black",
                                size = 0.5, linetype = "solid"),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank()) +
  
  #Apply unique font to the plot and following title/subtitle/labels
  
  theme(text = element_text(family = "Charter")) +
  
  labs(title = "PROPORTION OF FREEMEN AND SLAVES AMONG AMERICAN NEGROES .\n\nPROPORTION DES NÈGRES LIBRES ET DES ESCLAVES EN AMÉRIQUE .",
       subtitle = "\nDONE BY ATLANTA UNIVERSITY .") +
  
  theme(plot.title = element_text(size = 12.5, hjust = 0.45,
                                      color = "black"),
        plot.subtitle = element_text(size = 8.5, hjust = 0.5, color = "black")) +
  
  #Add vertical lines corresponding to the years after erasing major/minor grid lines
  
  geom_vline(xintercept = "1800") +
  geom_vline(xintercept = "1810") +
  geom_vline(xintercept = "1820") +
  geom_vline(xintercept = "1830") +
  geom_vline(xintercept = "1840") +
  geom_vline(xintercept = "1850") +
  geom_vline(xintercept = "1860") +
  
  #Add unique text/positions of labels and specify indiidual size
  
  geom_text(aes(5.04,5,      
                label = "FREE - LIBRE",
                fontface = 2),
            color = "black",
            size = 4.25) +
  
  geom_text(aes(5.03,50,
                label = "SLAVES\nESCLAVES",
                fontface = 2),
            color = "white",
            size = 4.75) +
  
  #Add unique positions of each percentage
  
  geom_text(aes(1.16,5,
                label = "8%"),
            color = "black",
            size = 3.25) +
  
  geom_text(aes(1.98,8.5,
                label = "11%"),
            color = "black",
            size = 3.25) +
  
  geom_text(aes(2.99,10.5,
                label = "13.5%"),
            color = "black",
            size = 3.25) +
  
  geom_text(aes(3.98,10.5,
                label = "13%"),
            color = "black",
            size = 3.25) +
  
  geom_text(aes(4.98,11.5,
                label = "14%"),
            color = "black",
            size = 3.25) +
  
  geom_text(aes(5.98,10.5,
                label = "13%"),
            color = "black",
            size = 3.25) +
  
  geom_text(aes(6.98,9.5,
                label = "12%"),
            color = "black",
            size = 3.25) +
  
  geom_text(aes(7.98,8.5,
                label = "11%"),
            color = "black",
            size = 3.25) +
  
  geom_text(aes(8.765,8.5,
                label = "100%"),
            color = "black",
            size = 3.25) +

#Add distinct years to the top of the y-axis

  geom_text(aes(1.25,-5, label = "1790"),
            color = "darkgrey", size = 3.75) +
  
  geom_text(aes(2,-5, label = "1800"),
            color = "darkgrey", size = 3.75) +
  
  geom_text(aes(3,-5, label = "1810"),
            color = "darkgrey", size = 3.75) +
  
  geom_text(aes(4,-5, label = "1820"),
            color = "darkgrey", size = 3.75) +
  
  geom_text(aes(5,-5, label = "1830"),
            color = "darkgrey", size = 3.75) +
  
  geom_text(aes(6,-5, label = "1840"),
            color = "darkgrey", size = 3.75) +
  
  geom_text(aes(7,-5, label = "1850"),
            color = "darkgrey", size = 3.75) +
  
  geom_text(aes(8,-5, label = "1860"),
            color = "darkgrey", size = 3.75) +
  
  geom_text(aes(8.75,-5, label = "1870"),
            color = "darkgrey", size = 3.75) 
  
#Reverse the direction of the y-axis

b <- a + scale_y_reverse() + 
  
  #Adjust the margins on the side
  
  theme(plot.margin = unit(c(0.25,-1.55,0,-2.1), "cm"))

b
```
