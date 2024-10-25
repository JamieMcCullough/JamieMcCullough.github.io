---
layout: page
#title:  "Dark Energy Survey Year 3: Blue shear"
teaser: "Star-forming spiral galaxies have less crowded extragalactic neighborhoods, making them excellent candidates for mapping cosmic structure."
header:
    title: "Dark Energy Survey Year 3:<br>Blue shear"
    background-color: "#212a8b;"
    image_fullwidth: "barred_spiral.jpg"
    caption: "Credit: NASA, ESA, and The Hubble Heritage Team (STScI/AURA)"
    caption_url: https://cdn.esahubble.org/archives/images/large/opo0501a.jpg
sidebar_mod: left
permalink: '/data/blueshear/'
---
<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=default'></script>
<style>.circular--square { border-radius: 50%; display: block; margin-left: auto; margin-right: auto;}</style>
### McCullough, Amon, Legnani, Gruen <em>et al.</em> 2024
## Abstract
Modeling the intrinsic alignment (IA) of galaxies poses a challenge to weak lensing analyses. The Dark Energy Survey, limited to <mark>pure <strong>blue, star-forming galaxies</strong></mark> is expected to be <mark>less impacted by IA</mark>. The cosmological parameter constraints from this <strong>blue</strong> sample are <mark>stable to IA model choice</mark>, unlike the passive galaxies in the full DES Y3 sample, the goodness-of-fit is improved and the $$\Omega_{\rm m}$$ and $$S_8$$ <mark>better agree with <em>Planck</em> Cosmic Microwave Background observations</mark>. Mitigating intrinsic alignments via sample selection, instead of flexible model choices, can reduce uncertainty in $$S_8$$ <mark>by a factor of 1.5</mark>, with less uncertain IA on small scales.

<img src="{{site.urlimg}}blueshear_summary.png" class="center" height=auto width=470px>

## Available data products
- The paper, <a href="">arxiv</a>, <a href="">journal (TBD)</a>
- _For DES Y3 data access_: See the [Year 3 Cosmology Data Release](https://des.ncsa.illinois.edu/releases/y3a2)
- For those doing cosmology with the fiducial Y3 blue sample:
<p style="text-align: center;">
<mark>data vector</mark> <em>(a .fits file with redshift distributions and 2-point measurements)</em><br>
<a class="radius button small" download="2pt_extended_data_blue_covupdated_at_3x2pt-cosmo.fits" href="https://github.com/jmccull/jmccull.github.io/blob/main/dataproducts_blueshear/2pt_extended_data_blue_covupdated_at_3x2pt-cosmo.fits?raw=true"><strong>Download FITS</strong> ›</a><br>   
fiducial <em>Polychord</em> <mark>chain</mark> <em>(.txt)</em> modeled with no intrinsic alignment, flexible baryon feedback, and analyzed at all scales<br>
<a class="radius button small" download="chain_blue_noia_hm20tagn76_83.txt" href="https://github.com/jmccull/jmccull.github.io/blob/main/dataproducts_blueshear/chain_blue_noia_hm20tagn76_83.txt?raw=true"><strong>Download Chain</strong> ›</a><br>  
</p>

## Major Collaborators
<div class="row t30">
    <div class="medium-4 columns b15">
        <img src="https://web.astro.princeton.edu/sites/g/files/toruqf1486/files/styles/3x4_750w_1000h/public/2023-10/alex.jpg?raw=true" alt="" height=auto width=200px class="circular--square">
        <p style="text-align:center"><a href="https://alexandraamon.com/">Alexandra Amon</a></p>
    </div><!-- /.medium-12.columns -->

    <div class="medium-4 columns b15">
        <img src="https://elisalegnani.github.io/assets/img/me_23_2.jpg" alt="" height=auto width=200px class="circular--square">
        <p style="text-align:center"><a href="https://elisalegnani.github.io/">Elisa Legnani</a></p>
    </div><!-- /.medium-12.columns -->

    <div class="medium-4 columns b15">
        <img src="https://www.imprs-astro.mpg.de/sites/default/files/usm_gruen.jpg" alt="" height=auto width=200px class="circular--square">
        <p style="text-align:center"><a href="https://www.physik.lmu.de/observatory/en/research/cosmology-at-usm/acai-group/">Daniel Gruen</a></p>
    </div><!-- /.medium-12.columns -->
</div><!-- /.row -->

### Using the cosmology results: an example
For an example of ingesting the chain and running a plot, using custom class <code>chain.py</code>, downloadable <a href="https://github.com/jmccull/jmccull.github.io/blob/main/dataproducts_blueshear/chain.py?raw=true" download="chain.py">here</a>.
<pre>
#some imports, including the custom chain class
from getdist import plots, MCSamples
import getdist
from chain import chain #place in same directory
import numpy as np
import matplotlib.pyplot as plt
</pre>
<pre>
#format the chain into something getdist can read
bluenoia = chain('../data_release/chain_blue_noia_hm20tagn76_83.txt')
bluenoia.add_s8()
sample = np.array([bluenoia.samples['cosmological_parameters--omega_m'], 
                   bluenoia.samples['cosmological_parameters--s8']])
bluenoia_chain = MCSamples(samples=sample.T,names=['om', 'S8'], labels=['\Omega_m', 'S_8'], 
                                   ranges = {'om':[0.1,0.9],'S8':[0.3,1.0]}, label= r'DES Y3 Blue Cosmic Shear', 
                                   weights=bluenoia.weight, settings={'boundary_correction_order':0, 
                                   'mult_bias_correction_order':1})
</pre>
<pre>
#generate an S8 - Om contour plot!
plt.rcParams['font.family'] = 'serif' 
g = plots.get_subplot_plotter(width_inch=4)
g.plot_2d([bluenoia_chain], ['om', 'S8'], filled=[True], 
           contour_args=[{'alpha':0.5,'lw':1.2, 'ls':'-','color':'blue'}], 
           diag1d_kwargs={'normalized':True})

g.add_legend(['DES Y3\nBlue Cosmic Shear'],fontsize=10,legend_ncol=1, legend_loc='upper right',framealpha=0)
plt.ylabel(r'S$_8 \equiv \sigma_8(\Omega_{\rm m}/0.3)^{1/2}$',fontsize=15)
plt.xlabel(r'$\Omega_{\rm m}$',fontsize=15)
plt.show()
</pre>
This will generate a contour plot from the chain that can be combined with other results:<br>
<img src="https://github.com/jmccull/jmccull.github.io/blob/main/dataproducts_blueshear/test_contour.png?raw=true" alt="" height=auto width=350px>

