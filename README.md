# Introduction to DeepCell through Interactive Tutorials

This material is designed to cover three specific areas: Unix and Python Basics, Image Analysis in Python, Introduction to Deep Learning and Overview of DeepCell.

## Getting Started

### git & GitHub accounts
[Install git](https://www.atlassian.com/git/tutorials/install-git) and set up your own [GitHub account](https://github.com/).

### Python3
* Installation instructions [for MacOS](https://docs.python-guide.org/starting/install3/osx/)
* Installation instructions [for Linux](https://docs.python-guide.org/starting/install3/linux/)
* Installation instructions [for Windows](https://docs.python-guide.org/starting/install3/win/)
* Windows uses may also be interested in [Anaconda](https://www.anaconda.com/distribution/)

### Pip (Python package manager)
* Installation instructions [for MacOS](https://stackoverflow.com/questions/17271319/how-do-i-install-pip-on-macos-or-os-x)
* Installation instructions [for Linux](https://itsfoss.com/install-pip-ubuntu/)
* (Pip should come bundled with pip on Windows, whether you install using Anaconda or not.)

### Docker
While not immediately necessary, the Van Valen Lab uses Docker extensively, and it will be helpful to have it [installed on your machine](https://docs.docker.com/install/).

### FIJI
* [All platforms](https://imagej.net/Fiji/Downloads#Installation)

### Windows Specific:
Most Windows machines do not come with a built-in SSH tool. Many like to use a downloadable client such as [PuTTY](https://putty.org/), [FileZilla](https://filezilla-project.org/).


## Material

This repo currently holds:

* A tutorial on basic Python/Numpy/Scipy meant to prepare students for more in-depth image analysis work.
* An introduction to image processing with python (with a focus on live cell imaging)
* An introduction to deep learning and the DeepCell library

You can follow the iPython notebooks on github or clone and execute it locally.

For some text-only explanations, look here:
[docker tutorial](./docs/Docker.md)
[Git tutorial](./docs/Git.md)
[Unix tutorial](./docs/Unix.md)


### Acknowledgements
These notebooks and tutorials build on and include material from earlier work:
* The basic Python tutorial (including numpy, matplotlib, and some of the file handling) comes largely from work by Volodymyr Kuleshov and Isaac Caswell on the CS231n Python tutorial by Justin Johnson (http://cs231n.github.io/python-numpy-tutorial/).
* The flow statements and SciPy sections in Day 1 come largely from work by Rajath Kumar which is available at https://github.com/rajathkumarmp/Python-Lectures. Those original notes, in turn, were updated for Python 3 and amended for use in Monash University mathematics courses by Andreas Ernst (those are available here: https://gitlab.erc.monash.edu.au/andrease/Python4Maths/tree/master).
* The image processing tutorials come largely from Jonas Hartmann's (Gilmour group, EMBL Heidelberg) Python BioImage Analysis Tutorial, which is available here: https://github.com/WhoIsJack/python-bioimage-analysis-tutorial
