---
layout: page
title: NBLAST
tagline: Fast, sensitive neuron similarity search
---
{% include JB/setup %}

Neural circuit mapping efforts in model organisms are generating multi-terabyte datasets of 10,000s of labelled neurons. Such data demand new computational tools to search and organize neurons. We present a general, sensitive and rapid algorithm, NBLAST, for measuring pairwise neuronal similarity. NBLAST considers both position and local geometry and works by decomposing a query and target neuron into short segments; matched segment pairs are scored using a log-likelihood ratio scoring matrix empirically defined by the statistics of real matches and non-matches.

##Find out more ...

* Please use this website to explore [why NBLAST might be helpful](why) in your research and [how it works](how).
* With [NBLAST online](nblast_online) you can query single neurons or fragments 
  against large databases of single neurons (FlyCircuit) or Gal4 expression patterns (FlyLight).
* Power users can run [NBLAST on their desktop](nblast_desktop) using arbitrary data.
* We have used NBLAST to organise over 16,000 Drosophila neurons into [structural clusters](clusters).
* Finally, watch some [demo videos](demos), read all out about in the [paper](paper), or [contact us](about) for help.
