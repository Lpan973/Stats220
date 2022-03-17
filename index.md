# index.md
### *Laura Pan lpan973*
### *Assignment1 Stats220*


# Introduction and Motivation
Attached below is the meme created through using R code as well the original code. 

The meme was created to reflect the different moods throughout the weekday from Monday through to Friday. Pictures from online were combined with text 
through using R code and {magick} package to achieve the final meme. The meme is an adaption to the meme in Lab 2 through using cute kids put together with
text. 


# Meme 

![Meme](https://raw.githubusercontent.com/Lpan973/Stats220/main/220meme.jpg)

# R Code 

```
---
title: "meme"
author: "Laura Pan"
---
  
library(magick)
library(tidyverse)

tired_girl <- image_read("http://n.sinaimg.cn/sinakd2020623s/268/w534h534/20200623/d811-ivmqpci1554737.jpg") %>% image_scale(500)

confused_girl <- image_read("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQKyjBAj1p6MTCTgy7EMDC5vWGMVNM-1EJohA&usqp=CAU") %>% image_scale(500)

happy_girl <- image_read("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR0vny8tPNXv6LpIGSyWzYS8s_3FJf4z9B6zg&usqp=CAU") %>% image_scale(500)



text_monday <- image_blank(width = 500, 
                           height = 500, 
                           color = "#E4BDB5") %>%
  image_annotate(text = "Monday", 
                color = "#FFFFFF",
                 size = 80,
                 font = "Playfair Display",
                 gravity = "center")

text_wed <- image_blank(width = 500, 
                           height = 500, 
                           color = "#E4BDB5") %>%
  image_annotate(text = "Wednesday", 
                 color = "#FFFFFF",
                 size = 80,
                 font = "Playfair Display",
                 gravity = "center") 

text_fri <- image_blank(width = 500, 
                           height = 500, 
                           color = "#E4BDB5") %>%
  image_annotate(text = "Friday", 
                 color = "#FFFFFF",
                 size = 80,
                 font = "Playfair Display",
                 gravity = "center")

row1 <- c(confused_girl, text_monday) %>%
  image_append()

row2 <- c(text_wed, tired_girl) %>%
  image_append()

row3 <- c(happy_girl, text_fri) %>%
  image_append()

final_meme <- c(row1, row2, row3) %>% image_append(stack = TRUE)

image_write(final_meme, "220meme.jpg")


```
