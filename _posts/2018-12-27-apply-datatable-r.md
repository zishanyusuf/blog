---
layout: post
title: "Using Apply functions in data.table in R"
date: 2018-12-25
comments: true
share: true
---

* Table of Contents
{:toc}

# 1. DATA STRUCTURES & ASSIGNMENT
---

## Columns of lists

Well... Finally some placeholder to write my own Blog about data.table in R that i will continue adding as i learn. In general based on my studies and experiments, it's known that data manipulation with data.table is [faster][1] than python pandas. Hence, i am going to put together my few explorations with data.table. Consider the following example:

{% highlight r %}
DT <- data.table(V1=c(1L,2L), V2=LETTERS[1:3],V3=round(rnorm(4),4),V4=1:12)
DT[, lapply(.SD, sum), by=V2]

OR, 

DT[, V5 := lapply(.SD, sum), by=V2] #Adds back the summation value to DT table
{% endhighlight %}

This is a data manipulation that was carried over columns with grouping on a particular column (V2). Well, i wondered can i do the similar operations over ROW values instead of columns. Well, yes, you guessed it right - using "apply".

{% highlight r %}
DT[, apply(.SD, 1, sum), by=V2]

OR,

DT[, V5 := apply(.SD, 1, sum), by=V2]
{% endhighlight %}

Have you run the code yet? Come on run it and see it's results. I am not going to show you the results here.

Let's move on. What about definding some user defined function within column and rows operations of data.table. Well...here you go.

Powered by [Jekyll](http://jekyllrb.com) and tutored by Hank Quinlan, Thank You!! It actually is a lot easier than I thought it was going to be.


[1]: https://datascience-enthusiast.com/R/pandas_datatable.html "Data Manipulation with Python Pandas and R Data.Table"
