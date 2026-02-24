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
- Read the <strong>paper</strong>: <a href="https://arxiv.org/abs/2410.22272">arxiv</a>, <a href="">journal (TBD)</a>
- Read the follow-up paper that uses the blue sample _with an externally informed baryon feedback model_: <a href="https://arxiv.org/pdf/2512.04209">Bigwood, McCullough et al. 2025</a>
- _For DES Y3 data access_: See the [Year 3 Cosmology Data Release](https://des.ncsa.illinois.edu/releases/y3a2)
- For those doing cosmology with the fiducial Y3 blue sample (citable data download [here](https://zenodo.org/records/18762855)):
<p style="text-align: center;">
<mark><strong>data vector</strong></mark> <em>(a .fits file with redshift distributions and 2-point measurements)</em><br>
<a class="radius button small" download="2pt_extended_data_blue_covupdated_at_3x2pt-cosmo.fits" href="https://github.com/jmccull/jmccull.github.io/blob/main/dataproducts_blueshear/2pt_extended_data_blue_covupdated_at_3x2pt-cosmo.fits?raw=true"><strong>Download FITS</strong> ›</a><br>   
<strong>fiducial <em>Polychord</em> <mark>chain</mark></strong><em>(.txt)</em><br><em>modeled with no intrinsic alignment, flexible baryon feedback, and analyzed at all scales</em><br>
<a class="radius button small" download="chain_blue_noia_hm20tagn76_83.txt" href="https://github.com/jmccull/jmccull.github.io/blob/main/dataproducts_blueshear/chain_blue_noia_hm20tagn76_83.txt?raw=true"><strong>Download Chain</strong> ›</a><br>  
<strong>source selection <mark>dictionary</mark></strong><em>(.pkl)</em><br><em>see instructions below to implement</em><br>
<a class="radius button small" download="blue_tomo_bins_wide_cell_dictionary.pkl" href="https://github.com/jmccull/jmccull.github.io/blob/main/dataproducts_blueshear/blue_tomo_bins_wide_cell_dictionary.pkl?raw=true"><strong>Download Source Selection Dictionary</strong> ›</a><br>  
</p>
### Calibration for the blue sample
These galaxies have different redshift distributions and shear calibration than the fiducial Y3 analysis. When running chains, take care to incorporate the relevant systematic calibrations updated here.
<table class="hover" text-align="center" margin=auto border-collapse=collapse>
  <colgroup>
    <col span="1" style="width: 20%;">
    <col span="1" style="width: 20%;">
    <col span="1" style="width: 20%;">
    <col span="1" style="width: 20%;">
    <col span="1" style="width: 20%;">
  </colgroup>
  <thead>
    <tr>
      <th>Redshift<br>Bin</th>
      <th>$$\bar{z}$$</th>
      <th>$$\Delta \bar{z}$$</th>
      <th>$$m$$</th>
      <th>$$\Delta m$$</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>0.3556</td>
      <td>0.018</td>
      <td>-0.0129</td>
      <td>0.0091</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0.5175</td>
      <td>0.015</td>
      <td>-0.0180</td>
      <td>0.0078</td>
    </tr>
    <tr>
      <td>3</td>
      <td>0.6994</td>
      <td>0.011</td>
      <td>-0.0203</td>
      <td>0.0076</td>
    </tr>
    <tr>
      <td>4</td>
      <td>0.8994</td>
      <td>0.017</td>
      <td>-0.0356</td>
      <td>0.0076</td>
    </tr>
  </tbody>
    <caption>For more information, see Table I in the paper.</caption>
</table>

### Source selection of the blue sample
The provided dictionary has keys `0, 1, 2, 3` for each tomographic bin with a list of photometric cell identifiers that meet the pure, blue, star-forming criteria we set in the paper, see <em> Myles & Alarcon et al. 2021</em> for more information on the cell definitions. For the Y3 data products, you can find the most up-to-date cell assignment for the public source catalogs <a href="https://des.ncsa.illinois.edu/releases/y3a2/Y3key-catalogs">here</a>, under `/catalog/sompz/unsheared` with column name `CELL_WIDE`. The dictionary can be read in with the following python snippet:
<pre>
    import pickle
    import numpy
    
    with open('blue_tomo_bins_wide_cell_dictionary.pkl','rb') as f:
        tomodict = pickle.load(f) #with different python versions, you may need to specify encoding=bytes or latin1

    # to produce a selection for e.g. blue tomographic bin 1 given CELL_IDs in 'cat'
    mask = np.in1d(cat['CELL_WIDE'], tomodict[0])
    cat_bin_1_blue = cat[mask]
</pre>

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

