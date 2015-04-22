
library(ggplot2)
data(diamonds)

# price vs. x
ggplot(aes(x = x, y = price), data = diamonds) +
  geom_point()
# Correlations between price and x,y,z 
with(diamonds, cor.test(price, x))
with(diamonds, cor.test(price, y))
with(diamonds, cor.test(price, z))

#price vs. depth
ggplot(aes(x = depth, y = price), data = diamonds) +
  geom_point(alpha = 1/150) 

# Adjustments - price vs. depth
ggplot(data = diamonds, aes(x = depth, y = price)) + 
  geom_point(alpha = 1/100) + scale_x_continuous(breaks=c(55,68,2))

#price vs. carat
a scatterplot of price vs carat and omit the top 1% of price and carat values.

ggplot(aes(x = carat, y = price), data = diamonds) +
  geom_point() +
  coord_cartesian(xlim = c(0, quantile(diamonds$carat, 0.99)),
                  ylim = c(0, quantile(diamonds$price, 0.99)))

#price vs. volume
diamonds$volume<- diamonds$x * diamonds$y * diamonds$z
ggplot(data = diamonds, aes(x = volume, y = price)) + 
  geom_point() 

library(plyr); library(dplyr)
count(diamonds$volume == 0)

detach("package:plyr", unload=TRUE)

#Adjustments - price vs. volume 
with(subset(diamonds, volume > 0 & volume <= 800),
     cor.test(volume, price))

# Mean Price by Clarity
diamondsByClarity <- diamonds %.%
  group_by(clarity) %.%
  summarise(mean_price = mean(price),
            median_price = median(as.numeric(price)),
            min_price = min(price),
            max_price = max(price),
            n = n()) %.%
  arrange(clarity)


#Bar Charts of Mean Price
library(dplyr)
diamonds_by_clarity <- group_by(diamonds, clarity)
diamonds_mp_by_clarity <- summarise(diamonds_by_clarity, mean_price = mean(price))

diamonds_by_color <- group_by(diamonds, color)
diamonds_mp_by_color <- summarise(diamonds_by_color, mean_price = mean(price))
p1 = ggplot(aes(x = clarity, y = price), data = diamonds) +
  geom_bar(stat = 'identity', aes(fill = clarity))

p2 = ggplot(aes(x = color, y = price), data = diamonds) +
  geom_bar(stat = 'identity', aes(fill = color))

grid.arrange(p1,p2,ncol = 1)



