# Introduction to DeepCell Label

## Table of Contents

* [Overview](#overview)
* [Load files](#load-files)
    * drag & drop files onto [label.deepcell.org](https://label.deepcell.org/)
    * supported filetypes
* [Use DeepCell Label](#use-deepcell-label)

## Overview

DeepCell Label is an browser-based data labeling tool designed for biological imagess. DeepCell Label allows you to view biological image and create or modify labels on top of them, building or modifying a single-cell segmentation of the image. In this guide, we'll walk through starting up DeepCell Label and the labeling tools available on this platform.


## Load files

### Drag & drop images on [label.deepcell.org](https://label.deepcell.org/)

The easiest way to use DeepCell Label is to visit [label.deepcell.org](https://label.deepcell.org/) and drag & drop your images into the upload file box. DeepCell Label will create a new project for you and redirect to the project URL, formatted like label.deepcell.org/project/{projectID}, where projectID is 12 random characters.

We also offer a selection of test files in a drop down menu on the DeepCell Label homepage, allowing you to explore DeepCell Label without providing your own data. Opening a test file from the dropdown menu will create and redirect you to a new project URL.

We will be this [demo file](https://caliban-input.s3.us-east-2.amazonaws.com/janelia_demo/HeLa-S3_janelia_demo_version.npz) throughout the upcoming guided walkthrough. Try downloading it now and opening it in DeepCell Label by dragging and dropping.

### Supported filetypes

A project in DeepCell Label consists of a raw image stack and a labeled image stack. DeepCell Label can both load files with only a raw image stack, or a raw image stack and a labeled image stack. If you load a file with only a raw image stack, DeepCell Label will create an empty labeled stack that you can label from scratch.

At the moment, DeepCell Label supports the following filetypes:
* .npz - zipped numpy arrays
    * contains paired raw and labeled image stacks
    * we can package multiple image stacks into an .npz with [numpy's savez function](https://numpy.org/doc/stable/reference/generated/numpy.savez.html), like with the following Python code snippet:
    ```
    array_shape = (30, 512, 512, 1)  # array shape is (frames, height, width, channels)
    raw_image_stack = np.zeros(array_shape, dtype=np.uint16)
    labeled_image_stack = np.zeros(array_shape, dtype=np.uint8)
    # important to use X and y kwargs to name the zipped arrays
    np.savez('/path/to/your/file.npz', X=raw_image_stack, y=labeled_image_stack)
    ```
* .png - loaded as a single raw image
* .trk - a custom file format for DeepCell Label tracking projects
    * consists of a .tar file with a raw image stack, a labeled image stack, and lineage metadata
    * contact us at _______ for more details on working with this filetype


## Use DeepCell Label

Want to learn more about the tools available in DeepCell Label? Start with our [guided walkthrough of a provided demo file](DeepCell_Label_interactive_demo.md), or load up a test file from the menu on the [DeepCell Label homepage](https://label.deepcell.org/).

Curious about visualizing your image channels with a multicolor overlay while you work? Check out our overview of [how to switch to an RGB viewing mode, and what changes to expect.](DeepCell_Labeling_RGB.md)
