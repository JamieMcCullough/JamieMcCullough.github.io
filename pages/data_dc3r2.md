---
layout: page
#title:  "DESI Complete Calibration of the Color-Redshift Relation (DC3R2)"
teaser: "Disentangling galaxy evolution from galaxy distance"
header:
    title: "<font color='white'><h5>DESI Complete Calibration of the Color-Redshift Relation</h5></font>"
    background-color: "#0b0b16;"
    image_fullwidth: "desi_3duniverse.gif"
    caption: "Credit: D. Schlegel/Berkeley Lab using data from DESI"
    caption_url: https://newscenter.lbl.gov/2022/01/13/dark-energy-spectroscopic-instrument-desi-creates-largest-3d-map-of-the-cosmos/
sidebar_mod: left
permalink: '/data/dc3r2/'
---

### McCullough <em>et al.</em> 2024
## Abstract
We present initial results from the <mark>Dark Energy Spectroscopic Instrument (DESI)</mark> Complete Calibration of the Color-Redshift
Relation (DC3R2) secondary target survey. Our analysis uses <mark>230k galaxies</mark> that overlap with KiDS-VIKING _ugriZYHJKs_
photometry to calibrate the color-redshift relation and to inform photometric redshift (photo-z) inference methods of future
weak lensing surveys. Together with Emission Line Galaxies (ELGs), Luminous Red Galaxies (LRGs), and the Bright Galaxy
Survey (BGS) that provide samples of complementary color, the <mark>DC3R2 targets help DESI to span 56% of the color space
visible to Euclid and LSST with high confidence spectroscopic redshifts</mark>. The effects of spectroscopic completeness and quality
are explored, as well as systematic uncertainties introduced with the use of common Self Organizing Maps trained on different
photometry than the analysis sample. We further examine the <mark>dependence of redshift on magnitude at fixed color</mark>, important
for the use of <mark>bright galaxy spectra to calibrate redshifts in a fainter photometric galaxy sample</mark>. We find that noise in the
KiDS-VIKING photometry introduces a dominant, apparent magnitude dependence of redshift at fixed color, which indicates a
need for carefully chosen deep drilling fields, and survey simulation to model this effect for future weak lensing surveys.

## Available data products
- Read the <strong>paper</strong>: <a href="https://arxiv.org/abs/2309.13109">arxiv</a>, <a href="https://academic.oup.com/mnras/article/531/2/2582/7686823">MNRAS</a>
- The [_Astrobites_ overview](https://astrobites.org/2023/10/02/dc3r2/), put together by Katherine Lee
- The LMU press release, <a href="https://www.lmu.de/en/newsroom/news-overview/news/cosmic-wrestling-match.html"><em>A Cosmic Wrestling Match</em></a>, also available on <a href="https://www.sciencedaily.com/releases/2024/07/240715135346.htm"><em>Science Daily</em></a>
- To reproduce the figures in the paper, see the <strong>data</strong> and <strong>jupyter notebook</strong> available on [Zenodo](https://zenodo.org/record/8328495)
- _For spectroscopy access_: See [DESI's Early Data Release](https://data.desi.lbl.gov/doc/releases/edr/#value-added-catalogs)
## Data visualization widgets 
Explore the data set in your browser to understand how color, redshift, and SED type are related, alongside exposure times and the effects of bias on photometric redshift inference. Note that this runs best in full screen and may take a moment to load on first viewing.

<div class="row t60">
    <div class="medium-12 columns b30">
        <img src="{{ site.urlimg }}pz_dist.png" alt="" class="center">
        <p style="text-align:center"><a href="[http://jcorneille.de](http://jmccull.github.io/dataproducts_dc3r2/)">Redshift Distributions and SEDs</a></p>
    </div><!-- /.medium-12.columns -->
</div><!-- /.row -->
<div class="row t60">
    <div class="medium-12 columns b30">
        <img src="{{ site.urlimg }}exptimes.png" alt="" class="center">
        <p style="text-align:center"><a href="http://jmccull.github.io/dataproducts_dc3r2/exposure_time/">Exposure Time and Magnitude Distributions</a></p>
    </div><!-- /.medium-12columns -->
</div><!-- /.row -->
<div class="row t60">
    <div class="medium-12 columns b30">
        <img src="{{ site.urlimg }}tomobin.png" alt="" class="center">
        <p style="text-align:center"><a href="http://jmccull.github.io/dataproducts_dc3r2/tomography/">Spectroscopic Selection Effects and Redshift Inference via Tomography</a></p>
    </div><!-- /.medium-12.columns -->
</div><!-- /.row -->
