---
layout: page
title: "About"
description: ""
group: navigation
weight: 9
permalink: /about/
---
{% include JB/setup %}

This website accompanies the paper [Neuron: Costa et al. (2014) NBLAST: Rapid, sensitive comparison of neuronal structure and construction of neuron family databases](http://dx.doi.org/10.1016/j.neuron.2016.06.012) and preprint [bioRxiv: Costa et al. (2014) NBLAST: Rapid, sensitive comparison of neuronal structure and construction of neuron family databases](http://dx.doi.org/10.1101/006346) and acts as a hub for demonstrations of the core NBLAST algorithm (package [nat.nblast](https://github.com/jefferislab/nat.nblast)), along with some features of the [NeuroAnatomy Toolbox](https://github.com/jefferis/nat).

## Contact
For problem-solving, or for more information beyond that contained in the manuscript, please use the [nat-user google group](https://groups.google.com/forum/#!forum/nat-user) shown in the [FAQ page](../faq).

You can also contact Greg Jefferis at jefferis \<at\> mrc-lmb \<dot\> cam \<dot\> ac \<dot\> uk.


## Software / data used
We used the [Computational Morphometry Toolkit](http://www.nitrc.org/projects/cmtk) for image registration, particularly the munger script therein, using [these scripts](https://github.com/jefferis/MakeAverageBrain) for template brain construction. 
Image processing and analysis was performed with a combination of [Fiji/ImageJ](http://fiji.sc) and [unu](http://teem.sourceforge.net/unrrdu/).
Image registration and skeletonisation was coordinated using [nat.as](https://github.com/jefferis/nat.as), with [R](http://www.r-project.org/) being used for general analysis.

Images from [FlyCircuit](http://flycircuit.tw) ([Chiang et al., 2011](http://dx.doi.org/10.1016/j.cub.2010.11.056)) were obtained from the National Center for High-performance Computing and National Tsing Hua University, Hsinchu, Taiwan. 


## Preparing own data for use with NBLAST
Protocols for [immunostaining and imaging fly brains](http://cshprotocols.cshlp.org/content/2013/4/pdb.prot071720.full), as well as [registration of the resulting images](http://cshprotocols.cshlp.org/content/2013/4/pdb.prot071738.full) are available from Cold Spring Harbor Protocols.
We recommend the use of [Simple Neurite Tracer](http://fiji.sc/Simple_Neurite_Tracer) for tracing neurons from the acquired images, detailed instructions for which are available from [here](http://fiji.sc/Simple_Neurite_Tracer:_Step-By-Step_Instructions).

### Examples with datasets from other species
We have previously explored neuronal data from other species using NBLAST and have made these analyses available through our [nat.examples](https://github.com/jefferis/nat.examples) R package.
In particular, we have looked at [monarch butterfly neurons](https://github.com/jefferis/nat.examples/tree/master/07-insectbraindb) from [insectbraindb.org](http://insectbraindb.org) and the [zebrafish olfactory projectome](https://github.com/jefferis/nat.examples/tree/master/05-miyasaka2014) from [Miyasaka et al. _Olfactory projectome in the zebrafish forebrain revealed by genetic single-neuron labelling_, Nature Communications](http://dx.doi.org/10.1038/ncomms4639).
