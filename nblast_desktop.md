---
layout: page
title: "NBLAST Desktop"
description: ""
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
