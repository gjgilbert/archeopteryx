# ALDERAAN
**ALDERAAN** is a pipeline for **A**utomated **L**ightcurve **D**etrending, **E**xoplanet **R**ecovery, and **A**nalysis of **A**utocorrelated **N**oise.

The pipeline is currently capable of processing photometric lightcurve data from the *Kepler* Space Telescope, but in the future will be extended to handle data from *K2* and *TESS*.

Detrending and transit fitting are optimized to detect low-amplitude transit timing variations (TTVs). Autocorrelated noise arising from both instrumental and astrophysical sources is handled using a combination of narrow bandstop filters and Gaussian Process regression. Sampling can be performed either using Dynamic Nested Sampling or using Hamiltonian Monte Carlo + umbrella sampling.

This software is powered by  ``astropy``, ``batman``, ``celerite``, ``dynesty``, ``exoplanet``, ``lightkurve``, ``PyMC3``, ``scipy``, and ``starry``.


# Installation instructions

```
$ git clone https://github.com/gjgilbert/alderaan <LOCAL_DIR>
$ conda env create -n <ENV_NAME> -f <LOCAL_DIR>/environment.yml

if <ENV_NAME> is not specified, the conda environment will be named "alderaan"
```

# Running the pipeline

Before running the ALDERAAN pipeline, raw photometric lightcurves must be downloaded from the Mikulski Archive for Space Telescopes (MAST). Instructions for accessing these files can be found either at MAST (https://archive.stsci.edu/kepler/download_options.html) or at the Exoplanet Archive (https://exoplanetarchive.ipac.caltech.edu/bulk_data_download/).

ALDERAAN currently uses the Pre-Search Data Conditioning Simple Aperature Photometry (PDC-SAP) data products. These files will be in FITS format and should be placed in a user-specified <DATA_DIRCTORY> on your local machine.

To run the pipeline, navigate into the cloned repository <LOCAL_DIR>. From there, execute three commands in sequence:
  1. ``python bin/detrend_and_estimate_ttvs.py``
  2. ``python bin/analyze_autocorrelated_noise.py``
  3. ``python bin/fit_transit_shape_*.py``

Each command takes a number of commmand line arguments which must be explicitly given.
