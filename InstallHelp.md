Some users have been having a bit of trouble using
[`devtools`](https://cran.r-project.org/package=devtools) to install
[`WVPlots`](https://github.com/WinVector/WVPlots). I thought I would
write a note with a few instructions to help. These are things you
should not have to do often, and things those of us already running `R`
have stumbled through and forgotten about.

First you will need install (likely admin) privileges on your machine
and a network connection that is not blocking and of cran, RStudio or
Github. Make sure you have up to date copies of both
[R](https://cran.r-project.org) and [RStudio](https://www.rstudio.com).
We have to assume you are somewhat familiar with R and RStudio (so
suggest a tutorial if you are not). Once you have these we will try to
"knit" or render a R markdown document. To do this start RStudio select
`File->"New File"->"R Markdown"` as shown below (menus may be different
on different systems, you will have to look around a bit).
![RStudio1](http://www.win-vector.com/blog/wp-content/uploads/2016/05/RStudio1.png "RStudio1.png")
Then click "OK". Then press the "Knit HTML" button as shown in the next
figure.
![RStudio2](http://www.win-vector.com/blog/wp-content/uploads/2016/05/RStudio2.png "RStudio2.png")
This will ask you to pick a filename to save as (anything ending in
".Rmd" will do). If RStudio asks to install anything let it. In the end
you should get a rendered copy of RStudio's example document. If any of
this doesn't work you can look to [RStudio
documentation](http://rmarkdown.rstudio.com). Assuming the above worked
paste the following commands into RStudio's "Console" window (entering a
"return" after the paste to ensure execution). \[Note any time we say
paste or type, watch out for any errors caused by conversion of normal
machine quotes to insidious smart quotes.\] ``

    install.packages(c('RCurl','ggplot2','tidyr',
                        'devtools','knitr'))

The set of packages you actually need can usually be found by looking at
the `R` you wish to run and looking for any `library()` or `::`
commands. R scripts and worksheets tend not to install packages on their
own as that would be a bit invasive. If the above commands execute
without error (messages and warnings are okay) you can then try the
command below to install `WVPlots`: ``

    devtools::install_github('WinVector/WVPlots',
                            build_vignettes=TRUE)

If the above fails it can be a problem with your machine (perhaps
permissions, or not curl library installed), network, anti-virus, or
firewall software. If it does fail you can try to install `WVPlots`
yourself by doing the following:

1.  Navigate a web browser to <http://winvector.github.io/WVPlots/>.
2.  From there download the file `WVPlots_0.1.tar.gz`.
3.  In the RStudio "Consoel" window type:
    `install.packages('~/Downloads/WVPlots_0.1.tar.gz',repos=NULL)`
    (replacing `'~/Downloads/WVPlots_0.1.tar.gz'` with wherever you
    downloaded `WVPlots_0.1.tar.gz` to).

If the above worked you can test the `WVPlots` package by typing
`library("WVPlots")`. Now you can try knitting one of our example
worksheets.

1.  Navigate a web browser to
    <https://github.com/WinVector/Examples/blob/master/PCR/XonlyPCA.Rmd>
2.  Download the file `XonlyPCA.Rmd` by right-clicking on the "Raw"
    button (towards the top right).
3.  Rename the downloaded file from `XonlyPCA.Rmd.txt` to
    `XonlyPCA.Rmd`.
4.  In Rstudio use `File->"Open File"` to open `XonlyPCA.Rmd`.
5.  Press the "Knit HTML" button (top midle of the editor pane) and this
    should produced the rendered result.

If this isn't working then something is either not installed or
configured correctly, or something is blocking access (such as
anti-virus software or firewall software). The best thing to do is find
another local `R` user and debug together.