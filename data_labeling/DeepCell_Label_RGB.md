# Visualize multiplexed data

## Table of Contents

- [Multi-channel viewing mode](#multi-channel-viewing-mode)
- [File specifications](#file-specifications)
- [Differences when viewing files](#differences-when-viewing-files)
- [Differences in available actions](#differences-in-available-actions)

## Multi-channel viewing mode

By default, DeepCell Label projects display one image channel at a time. However, some labeling projects benefit from a multi-channel display, which can be accessed by adding `?rgb=True` to the end of your project URL.

For example:

![Eliot npz in single-channel vs rgb viewing modes](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/single_channel_to_rgb.png)

If you want to switch back, just remove the `?rgb=True` flag from the URL. Your project labels will be maintained across these two viewing options.

## File specifications

Raw images should be in the shape (frames, rows, cols, channels) to work properly with DeepCell Label. Up to six channels can be displayed concurrently by the multi-channel viewing mode. The order of the channels in the raw image will determine their color; the first channel of the image will be displayed as red, the second as green, then blue, then cyan, magenta, and yellow in that order. 

## Differences when viewing files

The first difference between the two visual modes is the way raw images are displayed. Labels are displayed differently as well: in the multi-channel viewing mode, label outlines (instead of solid-color labels) are displayed on top of the raw image. 

![DeepCell Label image with rgb label outlines shown](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/rgb_display.png)

To view solid-color labels in whole-label editing mode, press "L" to switch between these label viewing modes. Highlighted labels also appear differently. Instead of being bright red, highlighted labels have a translucent interior in both paint and whole-label editing modes.

A few other image viewing options are different as well:

- no light/dark inversion with "i" in paint mode
- no switching between channels of image
- existing labels can be hidden in paint mode by pressing "z"

Brightness and contrast adjustment are available in multi-channel viewing mode and affect all channels.

## Differences in available actions

Currently, the watershed action (whole-label mode) and threshold functionality (paint mode) are not available when multi-channel viewing is active. These actions are based on a single-channel input and can be used if projects are switched out of multi-channel viewing by removing the `?rgb=true` URL flag.

All other DeepCell Label functionality is present in this alternate viewing mode, and there is no difference in output files based on which mode was used to create labels.

Want to try out this mode but aren't sure which file to start with? Use the `512-RGB.npz` example file available on <a href="http://label.deepcell.org" target="_blank">DeepCell Label</a> and add `?rgb=true` to the URL after the project loads. Alternatively, upload a copy of [this multi-channel demo file](https://caliban-input.s3.us-east-2.amazonaws.com/janelia_demo/multiplex_janelia_demo_version.npz) if you'd like to download the label file after making changes.
