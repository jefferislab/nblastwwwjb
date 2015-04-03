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
These tools are designed as an addon for the [NeuroAnatomy Toolbox (nat)](https://github.com/jefferis/nat) R package, which you must first install.


## Installation
As well as development versions available from GitHub through the previous links, stable versions are periodically released to CRAN ([nat](http://cran.r-project.org/web/packages/nat/index.html) and [nat.nblast](http://cran.r-project.org/web/packages/nat.nblast/index.html)).
These can be installed in an interactive R session via the command ``install.packages(c('nat', 'nat.nblast'))``.

<iframe width="480" height="360" src="https://www.youtube.com/embed/C9arQ0Sws7k?rel=0" frameborder="0" allowfullscreen></iframe>


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
plot3d(hckcs, k=3, db=kcs20)
par3d(userMatrix=structure(c(0.89571213722229, 0.196490913629532, -0.398862272500992, 0, -0.438298493623734, 0.541087925434113, -0.717717468738556, 0, 0.074794590473175, 0.817688941955566, 0.570780634880066, 0, 0, 0, 0, 1), .Dim = c(4L, 4L)))
{% endhighlight %}

![Kenyon cell clustering in 3D](../images/kc_clustering_3d.png)
