Lecture 05:Data visualization and graphics in R
================

``` r
plot(1:5, col="blue", typ="o")
```

![](class05_files/figure-markdown_github/unnamed-chunk-1-1.png)

``` r
baby <- read.table("bimm143_05_rstats/weight_chart.txt")
```

``` r
View(baby)
```

``` r
baby <- read.table("bimm143_05_rstats/weight_chart.txt", 
                   header = TRUE)
```

``` r
plot(baby$Age, baby$Weight, col="pink", typ="o", 
     xlab= "Age (months)", ylab= "Weight (kg)",
     ylim= c(2,10), main="Baby Weight vs. Age",
     lwd=2, pch=15, cex=1.5)
```

![](class05_files/figure-markdown_github/unnamed-chunk-5-1.png)

?plot
=====

``` r
plot(1:5, pch=1:5, cex=1:5, col=1:5)
```

![](class05_files/figure-markdown_github/unnamed-chunk-6-1.png)

``` r
mouse <- read.table("bimm143_05_rstats/feature_counts.txt", 
                             header = TRUE, sep = "\t")
```

``` r
dotchart(mouse$Count)
```

![](class05_files/figure-markdown_github/unnamed-chunk-8-1.png)

?par()$mar
==========

?barplot
========

``` r
par(mar=c(5.1, 12.1, 4.1, 2.1))
barplot(mouse$Count, horiz = TRUE, ylab="", names.arg = mouse$Feature, 
        main="Mouse GRCm38 Genome Features", las=1, xlim=c(0,80000))
```

![](class05_files/figure-markdown_github/unnamed-chunk-9-1.png)

``` r
mf <- read.delim("bimm143_05_rstats/male_female_counts.txt")
barplot(mf$Count, names.arg = mf$Sample, col=rainbow(10))
```

![](class05_files/figure-markdown_github/unnamed-chunk-10-1.png)

``` r
rainbow(10)
```

    ##  [1] "#FF0000FF" "#FF9900FF" "#CCFF00FF" "#33FF00FF" "#00FF66FF" "#00FFFFFF"
    ##  [7] "#0066FFFF" "#3300FFFF" "#CC00FFFF" "#FF0099FF"

``` r
mf <- read.delim("bimm143_05_rstats/male_female_counts.txt")
barplot(mf$Count, names.arg = mf$Sample, col=c("lightblue", "pink"), las=2)
```

![](class05_files/figure-markdown_github/unnamed-chunk-12-1.png)

``` r
barplot(mf$Count, names.arg=mf$Sample, col=rainbow(nrow(mf)))
```

![](class05_files/figure-markdown_github/unnamed-chunk-13-1.png)
