---
layout: page
title: "NBLAST Desktop"
description: "Installing NBLAST in your own computer"
group: navigation
weight: 4
permalink: /nblast_desktop/
---
{% include JB/setup %}

Our reference implementation of NBLAST is available through the function ``nblast`` provided through our R package [nat.nblast](https://github.com/jefferislab/nat.nblast).
In addition to basic pairwise comparison, the package implements search of databases of neurons.
There is also support for all by all comparison for a group of neurons.
This can produce a distance matrix suitable for hierarchical clustering, which is also implemented in the package.
These tools are designed as an addon for the [NeuroAnatomy Toolbox (nat)](https://jefferis.github.io/nat/) R package, which will be installed as as dependency.

## Data

The source data for the ``nblast`` function includes the reformatted FlyCircuit neurons processed as a dotprops (aka vector cloud) objects. These are accessible as a single R object of class neuronlist named ``dps``. 

To load the dps object into R follow these commands.

{% highlight r %}
if(!require("devtools")) install.packages("devtools")
devtools::source_gist("bbaf5d53353b3944c090", filename = "FlyCircuitStartupNat.R")
{% endhighlight %}

See https://gist.github.com/jefferis/bbaf5d53353b3944c090 for further details.

You can also download the original registered image data [here](http://www.virtualflybrain.org/site/vfb_site/Chiang2010.htm)(2Gb). 

The dotprops data for the GMR (Janelia) GAL4 lines is also available. It can be (down)loaded into R using 
{% highlight r %}
library(flycircuit)
gmrdps<-read.neuronlistfh("http://flybrain.mrc-lmb.cam.ac.uk/si/nblast/gmrdps/gmrdps.rds", localdir=getOption('flycircuit.datadir'))
remotesync(gmrdps, download.missing = TRUE)

{% endhighlight %}

it can then be used as a target for ``nblast`` searches. You can omit the `remotesync` command in subsequent sessions where you just want to use the downloaded data. Note the download (8.4Gb) will take a while depending on your distance from Cambridge ...

## Installation

### Prerequisites

* [R](http://r-project.org)
* [RStudio](http://www.rstudio.com) (recommended)
* [XQuartz](http://xquartz.macosforge.org/landing/) (if on Mac OS X > 10.6, for 3D plots)

As well as development versions available from GitHub through the previous links, stable versions are periodically released to CRAN ([nat](http://cran.r-project.org/web/packages/nat/index.html) and [nat.nblast](http://cran.r-project.org/web/packages/nat.nblast/index.html)).
These can be installed in an interactive R session via the following command:
{% highlight r %}
install.packages('nat.nblast')
{% endhighlight %}

alternatively to use the latest development versions:

{% highlight r %}
devtools::install_github(c("jefferis/nat", "jefferislab/nat.nblast"))
{% endhighlight %}

## Kenyon cells example
Below, we briefly show how our R packages can be used to cluster Kenyon cells using NBLAST, and show that they match the neuronal types defined by lobe innervation.
To follow along, simply copy and paste the code below into an interactive R session.


{% highlight r %}
# Create a 20 x 20 NBLAST score matrix for 20 Kenyon cells included with the nat package
library(nat.nblast)
library(nat)
kcscores <- nblast_allbyall(kcs20)

# Hierarchically cluster the Kenyon scores
hckcs <- nhclust(scoremat=kcscores)

# Divide the hierarchical clustering into three groups
library(dendroextras)
dkcs <- colour_clusters(hckcs, k=3)

# Plot a dendrogram of the clustering, with leaves labelled by true neuron type
labels(dkcs) <- with(kcs20[labels(dkcs)], type)
plot(dkcs)
{% endhighlight %}

![Kenyon cell clustering dendrogram](../images/kc_clustering_dendrogram.png)

{% highlight r %}
# Plot neurons in those clusters in 3D (with matching colours)
open3d()
plot3d(hckcs, k=3, db=kcs20, soma=T)
par3d(userMatrix=diag(c(1,-1,-1,1), 4))
plot3d(MBL.surf, alpha=.1)
{% endhighlight %}

![Kenyon cell clustering in 3D](../images/kc_clustering_3d.png)
