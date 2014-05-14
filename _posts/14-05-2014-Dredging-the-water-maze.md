---
layout: post
title:  Dredging the water maze
date:   14-05-2014 15:18:30
categories: blog
tags:
  Morris-water-maze
  behaviour
  learning
  memory
comments: true
---

I guess this is what happens when you let a physicist play with data.  

It all started because I was trying to understand why there was so much variation in what appeared to be straightforward measurements of learning and memory in mice. Digging a little deeper into the data convinced me that the only way to really understand the results was to look at the raw data, namely the paths that individual mice swim in the Morris water maze.  

This turned out to be a reasonably large dataset, 4080 individual swimming trials from 120 mice of 7 different genotypes provided about 1.7 million sets of coordinates. 

This was a perfect excuse to use the following R libraries:  

{% highlight R %}
  library(dplyr)
  library(ggplot2)
  library(magrittr)
{% endhighlight %}

The first steps towards a complete analysis are presented in a [working draft][watermaze]. Once I have tidied up the code a little I will also release the full methods on [GitHub][gh].  

* Preliminary observations
  * Results from the Morris water maze should be interpreted with caution, since anxiety may override learning in a way that cannot easily be controlled for.  
  * The change in the times taken to enter the platform area on days 5 and 12 may not fairly represent memory retention in mice.  
  * There is evidence of extremely precise long lasting spatial memory formed by a single event in the similarity between swimming paths on days 5 and 12.   



 
 
[gh]: https://github.com/adrowe1/  
[watermaze]:    http://adrowe1.github.io/articles/watermazeanalysis.html


