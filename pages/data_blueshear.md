---
layout: page
#title:  "Dark Energy Survey Year 3: Blue shear"
teaser: "Star-forming spiral galaxies have less crowded extragalactic neighborhoods, making them excellent candidates for mapping cosmic structure."
header:
    title: "Dark Energy Survey Year 3:<br>Blue shear"
    background-color: "#EFC94C;"
    image_fullwidth: "barred_spiral.jpg"
    caption: "Credit: NASA, ESA, and The Hubble Heritage Team (STScI/AURA)"
    caption_url: https://cdn.esahubble.org/archives/images/large/opo0501a.jpg
sidebar_mod: left
permalink: '/data/blueshear/'
---
<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=default'></script>

### McCullough <em>et al.</em> 2024
## Abstract
Modeling the intrinsic alignment (IA) of galaxies poses a challenge to weak lensing analyses. The Dark Energy Survey, limited to <mark>pure <strong>blue, star-forming galaxies</strong></mark> is expected to be <mark>less impacted by IA</mark>. The cosmological parameter constraints from this <strong>blue</strong> sample are <mark>stable to IA model choice</mark>, unlike the passive galaxies in the full DES Y3 sample, the goodness-of-fit is improved and the $$\Omega_{\rm m}$$ and $$S_8$$ better agree with <em>Planck</em> Cosmic Microwave Background observations. Mitigating intrinsic alignments via sample selection, instead of flexible model choices, can reduce uncertainty in $$S_8$$ <mark>by a factor of 1.5</mark>, with less uncertain IA on small scales.

## Available data products
- The paper, <a href="">arxiv</a>, <a href="">PRL</a>
- _For DES Y3 data access_: See the [Year 3 Cosmology Data Release](https://des.ncsa.illinois.edu/releases/y3a2)
- For the blue sample datavector
- For the corresponding sampled polychord chain  
<pre>
>>> import getdist
>>> from chain import chain
>>> import numpy as np
>>> bluenoia = chain('./chain_blue_noia_hm20tagn76_83.txt')
>>> bluenoia.add_s8()
>>> sample = np.array([bluenoia.samples['cosmological_parameters--omega_m'], bluenoia.samples['cosmological_parameters--s8']])
>>> bluenoia_chain = getdist.MCSamples(samples=sample.T,names=['om', 'S8'], labels=['\Omega_m', 'S_8'], ranges = {'om':[0.1,0.9],'S8':[0.3,1.0]}, label= r'DES Y3 Blue Cosmic Shear', weights=bluenoia.weight, settings={'boundary_correction_order':0, 'mult_bias_correction_order':1})
>>> g = getdist.plots.get_subplot_plotter()
>>> g.plot_2d([bluenoia_chain], ['om', 'S8'], filled=[True],alphas=[0.9], contour_args=[{'alpha':1.0,'lw':1.2, 'ls':'-','color':'blue'}], diag1d_kwargs={'normalized':True})
>>> g.add_legend(labels,fontsize=12,legend_ncol=1, legend_loc='lower center')
>>> plt.ylabel(r'$S_8 \equiv \sigma_8(\Omega_{\rm m}/0.3)^{1/2}$')
>>> plt.xlabel(r'$\Omega_{\rm m}$')
>>> plt.show()
</pre>
## Data visualization widgets 
Explore the data set in your browser to understand how color, redshift, and SED type are related ...

<div class="row t60">
    <div class="medium-12 columns b30">
        <img src="{{ site.urlimg }}pz_dist.png" alt="" class="center">
        <p style="text-align:center"><a href="[http://jcorneille.de](http://jmccull.github.io/dataproducts_dc3r2/)">Redshift Distributions and SEDs</a></p>
    </div><!-- /.medium-12.columns -->
</div><!-- /.row -->
