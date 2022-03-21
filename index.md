```r
#creating meme
library(magick)
#Insering pictures from Pinterest and scaling
sleepy_jk <- image_read("https://pm1.narvii.com/6855/8699ffe6997411f94ad138e0027e79371a24cedbv2_hq.jpg") %>%
  image_scale(500)

angry_jk <- image_read("https://pm1.narvii.com/6865/31b6231e0cd15c5f28b855700584e4dbf465381dr1-592-749v2_hq.jpg") %>%
  image_scale(500)


#Creating purple background for with white text
meme1_text <- image_blank(width = 500,
                          height = 500,
                          color = "#5b2c6f") %>%
  image_annotate(text = "Turning up to 8am\n zoom lectures be like",
                 color = "#FFFFFF",
                 size = 40,
                 font = "Fira Sans",
                 gravity = "center")

meme2_text <- image_blank(width = 500,
                          height = 500,
                          color = "#5b2c6f") %>%
  image_annotate(text = "When you realise you joined\n the wrong class",
                 color = "#FFFFFF",
                 size = 40,
                 font = "Fire Sans",
                 gravity = "center")

#appending the memes together
first_row <- c(sleepy_jk, meme1_text) %>%
  image_append()

second_row <-c(angry_jk, meme2_text) %>%
  image_append()

c(first_row, second_row) %>%
  image_append(stack = TRUE)

#saving the file to the device
image_write(first_row, second_row, "my meme.png")
```
