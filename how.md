---
layout: page
title: "How?"
description: ""
group: navigation
weight: 2
permalink: /how/
---
{% include JB/setup %}

<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/KaTeX/0.2.0/katex.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/KaTeX/0.2.0/katex.min.js"></script>

NBLAST works by decomposing neurons into point and tangent vector representations.
One neuron is designated the query and the other the target.
For each query segment (defined by a midpoint and tangent vector) the nearest neighbor (using straight-forward Euclidean distance) is identified in the target neuron.
A score for the segment pair is calculated as a function of two measurements: <span id="katexd">d</span>, the distance between the matched segments (indexed by <span id="katexi">i</span>), and <span id="katexdotprod">u_i . v_i</span>, the absolute dot product of the two tangent vectors; the absolute dot product is used because the orientation of the tangent vectors has no meaning in our data representation (see image).

![Comparing neurons](../images/neuron_comparison.png)

The scores are then summed over each segment pair to give a raw score, <span id="katexs">S</span>:
<p><span id="katexscore">S = sum of f(d, u_i . v_i)</span></p>
To determine a suitable <span id="katexf">f</span>, we developed an approach inspired by the scoring system of the BLAST algorithm.
For each segment pair we defined the score as the log probability ratio:
<p><span id="katexlogodds">f = log_2 p_match / p_rand</span></p>
i.e. the probability that the segment pair was derived from a pair of neurons of the same type, versus a pair of unrelated neurons.

We then defined <span id="katexpmatch">p_match</span> empirically by considering 150 olfactory projection neurons innervating the same glomerulus.
<span id="katexprand">p_rand</span> was calculated simply by drawing 5,000 random pairs of neurons from the database, assuming that the large majority of such pairs are unrelated neurons.
Joint distributions were calculated using 10 bins for the absolute dot product and 21 bins for the distance to give two 21 row by 10 column matrices.
The 2D histograms were then normalized to convert them to probabilities and the log ratio defined the final scoring matrix.

<script>
katex.render("d", katexd);
katex.render("i", katexi);
katex.render("|\\vec{u_i} \\cdot \\vec{v_i}|", katexdotprod);
katex.render("S", katexs);
katex.render("\\displaystyle S(\\text{query}, \\text{target}) = \\sum_{i=1}^{n} f(d_i, |\\vec{u_i} \\cdot \\vec{v_i}|).", katexscore);
katex.render("f", katexf);
katex.render("\\displaystyle f = \\log_2 \\frac{p_\\text{match}}{p_\\text{rand}},", katexlogodds);
katex.render("p_\\text{match}", katexpmatch);
katex.render("p_\\text{rand}", katexprand);
</script> 