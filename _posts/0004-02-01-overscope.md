---
layout: slide
title: "Overscope"
---
<section markdown="1">
## When data scope comes first 
{% highlight r %}
z  <- 2 * c(1:5)
x  <- "Not even a number."
df <- data.frame(x=c(1:5),y=c(1:5))
{% endhighlight %}

{% highlight r %}
lm( y ~ x, data=df)   # Coefficients:
                      #  (Intercept)  x  
                      #  1.192e-15    1.000e+00
{% endhighlight %}

{% highlight r %}
lm( y ~ z, data=df)   # Coefficients:
                      #  (Intercept)  z  
                      #  1.192e-15    5.000e-01
{% endhighlight %}
</section>

<section markdown="1">
## Same for dplyr
{% highlight r %}
z  <- 2 * c(1:5)
x  <- c(1:9999)
df <- data.frame(x=c(1:5), y=c(1:5))
{% endhighlight %}

{% highlight r %}
df %>% summarize(sum(x), sum(y), sum(z))
  # sum(x) sum(y) sum(z)
  # 1     15     15     30
{% endhighlight %}
</section>
