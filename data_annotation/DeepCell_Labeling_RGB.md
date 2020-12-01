# Visualize multiplexed data

## Table of Contents
- [Multi-channel viewing mode](#multi-channel-viewing-mode)
- [File specifications](#file-specifications)
- [Differences when viewing files](#differences-when-viewing-files)
- [Differences in available actions](#differences-in-available-actions)

## Multi-channel viewing mode
By default, DeepCell Label projects display one image channel at a time. However, some labeling projects benefit from a multi-channel display, which can be accessed by adding `?rgb=True` to the end of your project url.

For example:

![Eliot npz in single-channel vs rgb viewing modes](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/single_channel_to_rgb.png)

If you want to switch back, just remove the `?rgb=True` flag from the url. Your project labels will be maintained across these two viewing options.

## File specifications
Raw images should be in the shape (frames, rows, cols, channels) to work properly with DeepCell Label. Up to six channels can be displayed concurrently by the multi-channel viewing mode. The order of the channels in the raw image will determine their color; the first channel of the image will be displayed as red, the second as green, then blue, then cyan, magenta, and yellow in that order. 

## Differences when viewing files
Label overlays, no channel switching, no brightness inversion

## Differences in available actions
Thresholding and watershed not supported in rgb mode
