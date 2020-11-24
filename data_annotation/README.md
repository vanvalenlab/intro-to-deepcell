# Introduction to DeepCell Label (Codename: Caliban)

## Table of Contents

Label your data with DeepCell Label (Codename: Caliban)

DeepCell Label is an browser-based data labeling tool designed for single-cell segmentation. In this guide, we'll walk through what filetypes are supported in DeepCell Label and how to beginning labeling your files in DeepCell Label.

To train a model, we require both the raw images coming off a microscope, and the labeled images with a complete single-cell segmentation. DeepCell Label allows you to view your raw image files and create segmentation. We offer both a "paint mode" to segment an iamge down to the pixel-level, and a "whole label mode" that acts on whole areas with the same label.

* [Supported filetypes](./data_annotation)

A project in DeepCell Label consists of a raw image stack and a labeled image stack. DeepCell Label can both load files with only a raw image stack, or a raw image stack and a labeled image stack. If you load a file with only a raw image stack, DeepCell Label will create an empty labeled stack that you can label from scratch.

At the moment, DeepCell Label can load the following filetypes:
* .npz - zipped numpy arrays; may contain just a raw image stack, or both raw and labeled image stacks
* .png - loaded as a raw image stack
* .trk - a custom file format for DeepCell Label tracking projects; consists of a .tar file with a raw image stack, a labeled image stack, and lineage metadata

Note that an image "stack" can have just one image, such as image formats with only one frame like a PNG.

* [Getting started with DeepCell Label](./data_annotation)

### Drag & drop images on [caliban.deepcell.org](caliban.deepcell.org)

The easiest way to use DeepCell Label is to visit [caliban.deepcell.org](caliban.deepcell.org) and drag & drop your images into the upload file box. DeepCell Label will create a new project for you and redirect to the project URL, formatted like caliban.deepcell.org/project/{projectID}, where projectID is 12 random characters.

We also offer a selection of test files in a drop down menu on the DeepCell Label homepage, allowing you to explore DeepCell Label without providing your own data. Opening a test file from the dropdown menu will create and redirect you to a new project URL.

### Deploy your own DeepCell Label application

When you find that DeepCell Label meets your image labeling needs, you may want to create your own deployment of Caliban to scale up your labeling pipeline and label images _en masse_. Currently, DeepCell Label supports deployments on a local server, and on [Amazon Web Service's [Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/).

At the moment, DeepCell Label must load and export its project files from a [S3 bucket](https://aws.amazon.com/s3/). We are currently developing support to load and export project work onto the local file system where the DeepCell Label application is deployed.

If you are interested in creating your own DeepCell Label deployment, please contact us at _______ for more details and guidance.


* [Caliban modes and actions](./data_annotation)

Once you've created a project in DeepCell Label, you'll see a canvas on the right and an info table on the left. Here, we'll walk you through how to navigate your image, how to start labeling, and 

### View an image

* changing frames
* changing channels
* changing features
    * both nuclear & cytoplasmic labelings in the same file

* panning
* zooming
* changing brightness & contrast
    * reseting brightness & contrast

### Create a new labeling from scratch (paint mode)


* brush
* eraser
* conversion brush

* changing brush size
* changing label
    * increment/decrement
    * label picker
    * new label

* threshold

### Fix labeling errors (whole label mode)

* trim pixels
* fill holes
* swap labels
* delete labels
* split labels (watershed transformation)
* flood label
    * with new label (fix duplicated label)
    * with existing label (fix split label)