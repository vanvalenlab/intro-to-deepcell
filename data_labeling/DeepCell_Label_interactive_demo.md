# Learn to label with DeepCell Label

## Table of Contents

- [DeepCell Label interface](#deepcell-label-interface)
  - [Infopane](#the-infopane)
  - [Canvas](#the-canvas)
- [View an image](#view-an-image)
  - [Change between input image and label views](#change-between-input-image-and-label-views)
  - [Change the field of view](#change-the-field-of-view)
  - [Adjust image brightness and contrast](#adjust-image-brightness-and-contrast)
  - [Highlighting labels](#highlighting-labels)
  - [Changing the displayed image slice](#changing-the-displayed-image-slice)
- [Whole-label mode](#whole-label-mode)
  - [Select labels](#select-labels-in-whole-label-mode)
  - [Swap labels](#swap-labels)
  - [Trim stray pixels](#trim-stray-pixels)
  - [Fill holes in labels](#fill-holes-in-labels)
  - [Flood a labeled region with a new label](#flood-a-labeled-region-with-a-new-label)
  - [Replace one label with another](#replace-one-label-with-another)
  - [Split one label into two with watershed transform](#split-one-label-into-two-with-watershed-transform)
  - [Create new labels](#create-new-labels)
  - [Delete labels](#delete-labels)
- [Paint mode](#paint-mode)
  - [Brush basics](#brush-basics)
  - [Conversion brush](#conversion-brush-advanced-brush-option)
  - [Thresholding](#threshold-a-raw-image)
- [Export labels](#export-labels)

### To get started on the demo file:

1. Download the .npz file from our [S3 bucket](https://caliban-input.s3.us-east-2.amazonaws.com/janelia_demo/HeLa-S3_janelia_demo_version.npz). This file is prepopulated with labels.
2. Drag and drop the file onto the <a href="https://label.deepcell.org" target="_blank">DeepCell Label</a> homepage.

## DeepCell Label interface

You should now see an interface that looks like this:
![DeepCell Label interface](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/overall_interface.png)

On the left, we see a table that tells us about the image we are viewing and which tools we are using.

On the right is an interactive canvas with a raw image and its labels.

### The infopane

![DeepCell Label interface with infopane boxed](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/overall_interface_boxed_infopane.png)

The infopane provides information on what we are viewing in the canvas and the modes & tools to edit labels. See the Info Pane tab of the dropdown instructions in Label to learn more.

### The interactive canvas

![DeepCell Label canvas region of displayed page](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/interface_boxed_canvas.png)

#### The canvas

![DeepCell Label interactive region of canvas](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/canvas_boxed_interactive_canvas.png)

We use the canvas to:

- browse the image
- adjust the image for better viewing
- select labels
- edit selected labels

See the Canvas tab of the dropdown instructions to learn how to browse and adjust the images.

#### Undo and Redo buttons

![DeepCell Label undo and redo buttons](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/canvas_boxed_undo_buttons.png)

Made a mistake? Undo or redo your modifications with these buttons above the canvas. We can also use **Ctrl+Z** to undo and **Ctrl+Shift+Z** to redo.

## Whole-label mode (TODO: change name)

### Select labels in whole-label mode

Click on a label to select it. We can select up to two labels in whole-label mode. Some actions require just one selected label, while others require two selected labels. Clicking on a label after selecting two overwrites the second selected label with the new label.

### Swap labels

Select two different labels, then press the "s" key to swap the selected labels. A prompt will appear in "state" to confirm the swap where we can:

- press "S" (again) to swap the labels in only the current frame,
- press the spacebar to swap them across all frames, or
- press "Esc" to abort the action.

This can be useful in timelapse or 3D files with many frames, where consistent labels across each frame are required for labeling correctness.

#### Suggested swap

![DeepCell Label demo labels for suggested swap](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/resized_suggested_swap.png)

Labels 16 and 19 are consistent across most frames in this file, except for in frame 5, where they have swapped places. Swap them back to fix this labeling error.

### Trim stray pixels

Hold the shift key and select a label to trim disconnected pixels. _Note: for this action, the click location of your selection does matter. Make sure to click on the part of the label you want to keep._ A prompt will appear in **state** where we can:

- press spacebar to confirm, or
- press "Esc" to abort the action.

Stray pixels can arise from labeling mistakes made by other people or from artifacts of computational labeling like thresholding. If there are no stray pixels to remove from a label, this action has no effect.

#### Suggested label to trim pixels from

![DeepCell Label demo label for suggested trim pixels action](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/suggested_trim_pixels.png)

Frame 8 in the file has a stray brushstroke with label 28. To get rid of the stray brushstroke, hold down the shift key while you click on the real part of the label to select it, and confirm the action with spacebar.

### Fill holes in labels

Select the label with a hole, then press the "f" key to fill a hole. We will see a prompt in **state** to click on the hole to fill.

Holes are most often computational artifacts. We can also use this functionality to speed up labeling objects from scratch by drawing an outline and filling in the rest of the label.

#### Suggested hole to fill

![DeepCell Label demo label for suggested hole filling action](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/suggested_fill_hole.png)

Label 28 in frame 8 has a large hole in it. Use the hole fill action to quickly fix this annotation mistake.

### Flood a labeled region with a new label

Hold down the "Alt" key while you click on the region you wish to flood. _Note: for this action, the click location of your selection does matter. Make sure to click on the part of the label that you want to change the value of._ A prompt will appear in **state** asking you to confirm the action; press spacebar to confirm and apply the action.

Flooding a region allows us to fix our work after accidentally reusing a label value. As long as the two regions are separate, this mistake can be easily fixed by flooding one of the regions with a new value.

#### Suggested label to flood

![DeepCell Label demo label for suggested flood cell action](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/suggested_flood_cell.png)

Label 27 in frame 9 appears in two locations. Select label 27 and compare frame 8 to frame 9 to see that one region of label 27 should be modified to be a different value. Use the label flooding action to fix the duplicate label 27. (Note: if you flood the wrong part of the label, you can undo the action and try again, or you can use the swap action to get the labels in frame 9 to match up with frames 8 and 10.)

### Replace one label with another

Select the label you want to keep, then select the label you want to replace, then press "R" to replace the second label with the first. A prompt will appear in **state** to confirm; we can:

- press "S" to replace the labels in the same frame
- press spacebar to replace one label with the other across all frames, or
- press "Esc" to abort the action.

Use the single-frame option for fixing split errors and the all-frames option for merging lineages.

"Split" labels are a common type of annotation mistake seen in both computationally and manually generated label files. In this type of mistake, one object is annotated with two different labels. These two labels can easily be merged into one with the replace action. "Replace" can also be used to link two sequences of labels that belong to the same object across timelapse or 3D images.

#### Suggested label to replace

![DeepCell Label demo labels for suggested single-frame replace action](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/resized_suggested_replace.png)

In frame 10, label 17 is mistakenly split into labels 17 and 42. Use the single-frame replace action to replace 42 with 17.

### Split one label into two with watershed transform

Select the center of each object (click location matters), and then press "W". Make sure to select the same label twice. Confirm the prompt shown in **state** with the spacebar.

The selected label will be split into the original label and a new label. The first click location will keep the original label and the second click location will be assigned the new label. Watershed will not necessarily work well in every case; alternatives exist for splitting apart labels in DeepCell Label.

A "merged" label error is when two adjacent objects are annotated with the same label (the opposite of a "split" label error). Sometimes, merged objects can be distinguished from each other by the brightness of the objects. When the objects are bright and have a distinct area of dimness separating them, the labels can be split apart accurately with the "watershed" action.

#### Suggested label to split with watershed

![DeepCell Label demo label for suggested watershed action](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/suggested_watershed.png)

Label 25 in frame 11 is an example of a merged label that can be fixed with watershed. Try using the watershed action to split it apart--if the resulting label boundary does not look good, you can undo the action or replace the new label with the old label, and try again with different click locations.

### Create new labels

Select the label that should get a new label, then press "C". A prompt will appear in **state** to confirm the label creation; we can:

- press "S" to create a new label in only the current frame,
- press spacebar to create the label in all subsequent frames, or
- press "Esc" to abort the action

The single-frame option is different from the label flooding action we used earlier, as creating a new label with "c" will change all pixels of the label in the frame, not just connected pixels. Use the "all subsequent frames" version of the action when unlinking two objects from each other that are otherwise labeled correctly.

Sometimes, you need to unlink sequences of labels in timelapse or 3D files. For example, if a cell divides and one of the daughter cells is given the same label as the parent, it is appropriate to give a new label to the daughter cell in the frames where it is present.

#### Suggested label to create

This file does not contain a specific error that is best fixed with the create action, but you can try it out on any labels you would like. Try creating a new label in multiple frames with the "all subsequent frames" version of the action, then link the two sequences back together with the replace action applied in all frames to understand these actions better.

### Delete labels

Select the label to be deleted, then press "X". A prompt will appear in **state** to confirm the label deletion; we can:

- press spacebar to delete the label in only that frame, or
- press "Esc" to abort the action.

The delete action will remove all of that label from the frame, even unconnected pieces. This action can be used to quickly and completely remove annotation mistakes, such as labels that have been assigned to image artifacts.

#### Suggested label to delete

This file does not contain a specific error that is best fixed with the delete action, but you can try it out on any labels you would like.

## Paint mode

Paint mode allows us to partially correct labels, or even draw labels from scratch. This section covers the tools to make pixel-level changes to labels files. We can easily switch between the whole label mode and paint mode by pressing "e".

### Brush basics

Click and drag on the canvas to draw with the brush. As we draw with the brush, it leaves a translucent trace where we have drawn. When you release the mouse, we add a label to the trace area.

#### Brush size

We can change the brush size with the up and down arrow keys. The brush has a 5-pixel radius by default. The brush size is shown in the infopane when in paint mode.

#### Brush label

The brush label is the label that the brush modifies when drawing. The brush adds this label to _only_ background regions. Existing labels will not be drawn over by the brush. When erasing, we erase only the brush label, without modifying other labels. We can see the brush label in the infopane ("brush label") and we can cycle the label with the bracket keys ( "\[" and "\]" ).

Press "N" (for "new") to set the brush to an unused value.

Press "P" (for "picker") and then click on an label to set the brush label to an existing label.

#### Highlighting

The label in the image with the same value as the brush label will be highlighted red with a white border (when highlighting is turned on). Try changing the value of the brush to see the highlighted label change as well.

#### Erasing

Press the "X" key to toggle the eraser. The brush has a red outline when the eraser is on, and a white outline when the eraser is off (and set to draw instead).

#### Suggested regions to fix with the basic brush tool

![DeepCell Label demo pixel-editing mode suggested basic brush fixes](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/suggested_brush_edits.png)

In frame 12, label 22 does not fully cover its object, and label 23 covers too much background in addition to the object. Try changing the brush value to 22 to draw in some of the missing label, then increment to 23 and erase some of the extra label.

### Conversion brush (advanced brush option)

Press "r", then select the label you want to paint over, then the label you want to paint with. Prompts will appear in **state** to walk you through these steps to use the conversion brush. Press "n" instead of selecting a second label to draw with a new label.

Once these selections have been made, the label to be overwritten will appear with a red outline around it, and the label to draw with will have a white outline around it.

Sometimes, the boundary between two labels is inaccurate, even though both objects are accurately covered by labels. Or, two objects are annotated with a single label, but cannot be accurately split using the watershed action. In these cases, instead of erasing one label and then drawing another in, we can use the conversion brush functionality to directly replace one label with another, without affecting the background or other labels.

#### Suggested regions to fix with the conversion brush

![DeepCell Label demo pixel-editing mode suggested conv brush fixes](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/suggested_conv_brush_edits.png)

In frame 13, the boundary between labels 27 and 29 is inaccurate, although the foreground/background distinction is accurate. Try using the conversion brush to adjust the boundary between these labels. You can also try using the conversion brush to draw a new label over part of label 35, which covers two objects (note: the second object is easier to see in channel 1).

### Threshold a raw image

Press "t" while in pixel-editing mode, then click and drag to create a bounding box around the area to threshold. When you release the mouse button, the brighter areas inside the bounding box will have a new label.

When objects have a clear fluorescent signal, thresholding is an alternative option to drawing in a label with the brush. The quality of the thresholded label will depend on the input image as well as the bounding box you draw. For best results, make sure to include some background in your bounding box. We often see stray pixels when using the threshold tool, which we can clear with the trim action in whole-label mode.

#### Suggested region to threshold

One of the cells in frame 14 is conspicuously unlabeled. Try using the thresholding tool to label it!

## Export labels

![DeepCell Label download button](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/download_button.png)

Download your labels with the download button above the infopane. Your raw images and labels are stored together in the .npz file as training data for model training.

Want to explore an alternate viewing option for multichannel images? Check out [what differences to expect in RGB mode](./DeepCell_Label_RGB.md).

Ready to put your training data to use? Quickly [train up your own model](../model_training) with DeepCell.
