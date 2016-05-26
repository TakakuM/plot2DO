## plot2DO: Plot 2D Occupancies

**plot2DO** is an R package for computing and visualizing the two-dimensional (2D) occupancies. Instead of using the typical one-dimensional (1D) occupancy/coverage, obtained by stacking all the mapped reads regardless of their lengths, we show the relative occupancy given by DNA fragments of specific lengths in a matrix form.

## Installing
This tool uses the following R packages: *`caTools`*, *`colorRamps`*, *`GenomicAlignments`*, *`GenomicRanges`*, *`optparse`*, *`rtracklayer`*.
To install these packages, open R and execute the following commands:
```{r}
> # Install caTools, colorRamps and optparse packages from CRAN:
> install.packages(c("caTools", "colorRamps", "optparse"))
>                  
> # Get the latest version of Bioconductor:
> source("https://bioconductor.org/biocLite.R")
> biocLite()
> 
> # Install the remaining Bioconductor packages:
> biocLite(c("GenomicAlignments", "GenomicRanges", "rtracklayer"))
```


## Running

After the R packages have been installed, you can execute **plot2DO** from bash. To get to the help page, open a terminal and run:
```
$ Rscript plot2DO.R --help
Usage: plot2DO.R [options]


Options:
        -f FILE, --file=FILE
                Dataset file name [options: BED or BAM format]

        -r REFERENCE, --reference=REFERENCE
                Reference points to align [options: TSS (default), TTS, Plus1]

        -l MINLENGTH, --minLength=MINLENGTH
                The smallest DNA fragment to be considered [default = 50]

        -L MAXLENGTH, --maxLength=MAXLENGTH
                The largest DNA fragment to be considered [default = 200]

        -u UPSTREAM, --upstream=UPSTREAM
                Length of the upstream region that will be plotted [default = 1000]

        -d DOWNSTREAM, --downstream=DOWNSTREAM
                Length of the downstream region that will be plotted [default = 1000]

        -h, --help
                Show this help message and exit
```
The only required input is the name of the file that contains the aligned genomic data (*e.g.* *`data.bam`*, *`data.bed`*). To generate the default 2D occupancy plot (around TSS, all DNA fragments with the length L between 50 - 200 bp, 2kb windows centered on TSS), run the following command:
```
$ Rscript plot2DO.R --file data.bam
```
This is equivalent to either of the extended forms:
```
$ Rscript plot2DO.R --file data.bam --reference TSS --minLength 50 --maxLength 200 --upstream 1000 --downstream 1000
$ Rscript plot2DO.R -f data.bed -r TSS -l 50 -L 200 -u 1000 -d 1000
```


## Results

**plot2DO** will create a new folder called **2D_occupancy**, which will contain the 2D occupancy, saved in *RData* format, and the plots, saved in a *pdf* format. An example figure generated by **plot2DO** (Dataset: *`439J_3_H4_25U_IP`*; Reference: TSS; 50 bp $\leq$ L $\leq$ 200 bp; Upstream/Downstream window = 1 kb) is shown below:
![](img.png)


## Citation
If you use this program in your research, please cite our article. (not available yet)
