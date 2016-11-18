---
title: "Installing latest version of RStudio from R"
layout: post
---


{% highlight r %}
rstudio_ubuntu_daily_url <- "https://www.rstudio.org/download/daily/desktop/ubuntu64/"

r <- readLines(curl::curl(rstudio_ubuntu_daily_url))

file <- regmatches(r, regexpr("https\\S+?deb", r))[1]
file

destfile <- paste("/tmp/", basename(file))

download.file(file, destfile = destfile)

cmd <- sprintf("dpkg -i %s", destfile)
system(cmd)
{% endhighlight %}
