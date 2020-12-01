# Introduction to DeepCell.org

Deepcell.org is a web-based interface to access our pre-trained deep learning models. The website allows you to easily upload example images, run them on our available models, and download the results without requiring any local installation. The backend is managed by the [kiosk](https://github.com/vanvalenlab/kiosk-console), which provides an efficient and scalable way to analyze large volumes of data using cloud computing.

## Table of Contents

* [Formatting data for web-based models](README.md/#formatting-data-for-web-based-models)
* [Generating predictions with DeepCell.org](README.md/#generating-predictions-with-deepcellorg)
* [Plugging in to DeepCell.org with ImageJ](README.md/#plugging-in-to-deepcellorg-with-imagej)

## Formatting data for web-based models

#### Multiplex Model

The multiplex model performs whole-cell segmentation of tissue imaging data. The input to the model is two-channel images. The first channel must be a nuclear channel (such as DAPI). The second channel must be a membrane or cytoplasmic channel (such as E-Cadherin).

#### Nuclear Segmentation Model

TODO: do we describe both nuclear and cytoplasm model? Only one? Keep this blank?

## Generating predictions with DeepCell.org

Deepcell.org is a web-based interface to access our pre-trained deep learning models. The website allows you to easily upload example images, run them on our available models, and download the results without requiring any local installation.

DeepCell.org is run by the [DeepCell Kiosk](https://github.com/vanvalenlab/kiosk-console).
 The Kiosk provides an efficient and scalable way to analyze large volumes of data using cloud computing.
  By automatically scaling up when usage increases and scaling down when usage decreases, the Kiosk is able to quickly deliver results for large numbers of images when demand increases, while reducing costs by downscaling when demand decreases.

### Submitting data to the website

Generating data from the website is quite easy.

1. Go to DeepCell.org, and click on `PREDICT`.
![image](resources/DeepCell_website_predict.png)

2. This will take you to the image upload interface. The default model is `multiplex`. Before submitting your image, make sure you understand [the available models and data formatting requirements](models.md). Upload your image by dragging it into the upload box, or by clicking and then browsing to find your image
![image](resources/DeepCell_website_upload.png)

3. Once your image has been successfully uploaded, click `Submit`, and the server will begin processing your data.
![image](resources/DeepCell_website_submit.png)

4. Once complete, you can download the results, and then process additional images
![image](resources/DeepCell_website_download.png)

## Plugging in to DeepCell.org with ImageJ

The ImageJ plugin provides an easy interface to access our pre-trained deep learning models within ImageJ itself. Data is automatically uploaded to our server, processed, and then returned within ImageJ.

Before getting started, make sure you understand [the available models and data formatting requirements](README.md/#formatting-data-for-web-based-models).

### Installation

To install the ImageJ plugin, follow the [instructions](https://github.com/vanvalenlab/kiosk-imageJ-plugin#how-to-install).

### Generate predictions

To generate predictions using the plugin, follow the [instructions](https://github.com/vanvalenlab/kiosk-imageJ-plugin#how-to-run-the-plugin).
