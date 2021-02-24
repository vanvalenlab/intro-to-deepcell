# Introduction to DeepCell

This material is intended to help users become acclimated with the [DeepCell](https://www.deepcell.org/about) ecosystem. DeepCell addresses three key needs for deep learning and biological images:

1. How can I use deep learning easily on my data?
2. How can I interact with these predictions?
3. How can I improve these model predictions?

This tutorial will provide a gentle introduction to all three areas. Additionally, we have included a "Getting Started" section for users that may be unfamiliar with the basic tools covered in this material.

## Table of Contents

[Getting started](./getting_started)

* Required software installations
* Intro to Unix, Docker, and Git
* Python best practices
* Basic Python, Numpy, and Scipy exercises
* Intro to Python image processing for live-cell imaging
* Intro to deep learning with tensorflow

[Analyzing my images with pre-trained models](./pretrained_models)

* Summary of available models
* Running pre-trained models in the cloud
* Running pre-trained models locally

[Labeling my data with DeepCell Label](./data_labeling)

* Load files
* Use DeepCell Label

[Building new and improved models with deepcell-tf](./model_training)

* Introduction to `deepcell-tf`
* Training a model in Google Colab

## Publications
The following are a list of DeepCell resources associated with specific publications that use DeepCell.

### [Greenwald, Miller et al. (2021) Accurate whole-cell segmentation in multiplexed images of tissues with large-scale data annotation and deep learning]()
* The TissueNet dataset will be released through `deepcell.datasets` at the time of publication.
* The pretrained Mesmer model is available through `deepcell.applications` as shown in this [example notebook](https://github.com/vanvalenlab/deepcell-tf/blob/master/notebooks/applications/Multiplex-Application.ipynb). The model can also be run in the cloud and you can learn more about those resources in our guide about [running pretrained models in the cloud](./pretrained_models#running-pre-trained-models-in-the-cloud).
* The notebooks used to train Mesmer models for publication are available in our [publication figure repo](https://github.com/vanvalenlab/publication-figures/tree/mesmer_update/2021-Greenwald_Miller_et_al-Mesmer). Additional code for generating each figure is alo available.

### [Bannon et al. (2021) DeepCell Kiosk: scaling deep learning–enabled cellular image analysis with Kubernetes. Nature Methods.](https://doi.org/10.1038/s41592-020-01023-0)
* The DeepCell Kiosk can be downloaded from the [github repo](https://github.com/vanvalenlab/kiosk-console) and additional documentation is hosted on [Read the Docs](https://deepcell-kiosk.readthedocs.io/en/master/GETTING_STARTED.html).
* A persistent deployment of the Kiosk is hosted at [https://deepcell.org/](https://deepcell.org/).
* The code used to generate figures from the paper is available in our [publication figure repo](https://github.com/vanvalenlab/publication-figures/tree/mesmer_update/2020-Bannon_et_al-Kiosk).

## Copyright

Copyright © 2016-2021 [The Van Valen Lab](http://www.vanvalen.caltech.edu/) at the California Institute of Technology (Caltech), with support from the Shurl and Kay Curci Foundation, Google Research Cloud, the Paul Allen Family Foundation, & National Institutes of Health (NIH) under Grant U24CA224309-01.
All rights reserved.

## License

This software is licensed under a modified [APACHE2](https://github.com/vanvalenlab/intro-to-deepcell/blob/master/LICENSE). See [LICENSE](https://github.com/vanvalenlab/intro-to-deepcell/blob/master/LICENSE) for full details.

## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## Credits

[![Van Valen Lab, Caltech](https://upload.wikimedia.org/wikipedia/commons/7/75/Caltech_Logo.svg)](http://www.vanvalen.caltech.edu/)
