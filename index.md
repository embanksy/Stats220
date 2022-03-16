# My Meme:

![](meme.png)

### About my meme:
**My Inspo:**
1. The amount of assignments a have due next week (21/3/22), there's **LOTS** ![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSL3YPLRzFS6ny5hQe76dcLxJcllTEzMBevpw&usqp=CAU)
2. I ***love*** Pooh Bear
3. Fun Fact: Purple is my favourite colour!

I don't know much about memes so i followed a pretty basic picture-text format.

## The R code which I created it with:

```{r}
library(magick)

# Need to use these functions:
# c(), image_blank(), image_read(), image_annotate(), image_append()
# Need to use pipes (%>%) and named objects (<-)
# Save meme as image with image_write()


# square one
  comp_text <- image_blank(width = 500, height = 500, color = "#b983eb") %>%
    image_annotate(text = "When you\n complete your\n assignment", 
                   color = "#000000", 
                   size = 80,
                   font = "Impact",
                   gravity = "center")

# square two
  happy_pooh <- image_read("https://lumiere-a.akamaihd.net/v1/images/c94eed56a5e84479a2939c9172434567c0147d4f.jpeg?region=0,0,600,600&width=480") %>%
    image_scale(500)

# square three
  sad_pooh <- image_read("https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/fb3bc949-fdab-42a9-a5d0-50f4d0ee5beb/d4jtpqx-ee46f902-58a0-4c02-86a0-711dae7fa9fa.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcL2ZiM2JjOTQ5LWZkYWItNDJhOS1hNWQwLTUwZjRkMGVlNWJlYlwvZDRqdHBxeC1lZTQ2ZjkwMi01OGEwLTRjMDItODZhMC03MTFkYWU3ZmE5ZmEuanBnIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.Bwcd0ZakzEZWBopo9XOrY1fAK2bPTlrTQaVMq3MniSI") %>%
    image_scale(500)

# square four
  more_text <- image_blank(width = 500, height = 415, color = "#b983eb") %>%
    image_annotate(text = "But you have\n 5 more to go", 
                   color = "#000000", 
                   size = 80,
                   font = "Impact",
                   gravity = "center")

# making them into each row (1+2 and 3+4)
  first_row <- image_append(c(comp_text, happy_pooh))
  second_row <- image_append(c(sad_pooh, more_text))

# combining each row to make the whole thing
meme <- c(first_row, second_row) %>%
  image_append(stack = TRUE) %>%
  image_scale(800)
  
image_write(meme, "meme.png")
```
