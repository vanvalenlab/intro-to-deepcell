# Learn to label with DeepCell Label

## Table of Contents

- [DeepCell Label interface](#deepcell-label-interface)
  - [Infopane](#the-infopane)
  - [Canvas](#the-canvas)
  - [Undo/Redo](#Undo-and-Redo-buttons)
- [Example: tissue image](#example:-tissue-image)
  - [brush tool](#brush-tool)
  - [replace action](#replace-action)
- [Example: nuclear image](#example:-nuclear-image)
  - [autofit tool](#autofit-tool)
  - [grow/shrink tool](#grow/shrink-tool)
  - [watershed tool](#watershed-tool)
- [Example: Human Protein Atlas image](#example:-human-protein-atlas-image)
  - [threshold tool](#Threshold-tool)
  - [trim tool](#Trim-tool)
  - [flood tool](#flood-tool)
- [Example: timelapse and 3D files](#Example:-timelapse-and-3D-files)
- [Export labels](#export-labels)

## DeepCell Label interface

To learn the DeepCell Label interface, open the first example file in the dropdown menu on the homepage, named **3D organoid annotation**.

You should now see an interface that looks like this:
![DeepCell Label interface](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/bebi205_demo/initial_page.png)

On the left, we see an infopane with data about what we are viewing.

On the right, we see an interactive canvas with labels overlaid on a raw image.

### The infopane

![DeepCell Label interface with infopane boxed](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/bebi205_demo/infopane_boxed.png)

The infopane tells us what we are viewing in the canvas. See the Info Table tab of the dropdown instructions in Label to learn more about each row:

![Info Table submenu in expanded instructions](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/bebi205_demo/instructions_tab_infotable_boxed.png)

### The interactive canvas

![DeepCell Label canvas region of displayed page](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/bebi205_demo/canvas_boxed.png)

#### The canvas

We use the canvas to:

- browse the image
- adjust the image for better viewing
- select labels
- edit selected labels

See the Canvas tab of the dropdown instructions to learn how to browse and adjust the images.

See the Select tab to learn how to select labels.

See the Tools and Actions tabs to learn how to edit the selected labels.

![Other tabs of infopane](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/bebi205_demo/instructions_tab_other_tabs_boxed.png)

#### Undo and Redo buttons

Made a mistake? Undo or redo your modifications with Undo and Redo buttons above the canvas. We can also use the shortcuts <kbd>Ctrl</kbd> + <kbd>Z</kbd> to undo and <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Z</kbd> to redo.

## Navigating the file

### Change the image

Files can contain information about multiple frames, channels, and features. The Info Table tab of the dropdown instructions explains these different aspects of a file, and the Canvas tab explains how to update the view of these different components.

### Move around the image

Zoom and pan functionality can be used to get a closer look at the current view. There is no limit to how far you can zoom in on a file; although there are diminishing returns for viewing details within the image, working at high levels of zoom can help make mouse movements more accurate.

### Select labels

Before we can edit a label, we must select it. When we select a label as the **foreground** label, we can add more that label, while selecting the label as the **background** lets us remove that label.
The foreground is outlined in white, while the background label is outline in red.

When highlighting is on, the foreground label also becomes bright red, making it easy to focus on. By selecting all the labels in order, we can methodically review the labels in a file.

See the Select Labels tab of the dropdown instructions for how to change the labels being highlighted.

### View multiple channels in color

In RGB viewing mode, we can see all the labels outlined in white on top of a color image, where each raw channel becomes a different color. In this view, the selected labels are highlighted in translucent white instead of bright red.

## Example: tissue image

### Download

1. Download the tissue imaging .npz file from our [S3 bucket](https://caliban-input.s3.us-east-2.amazonaws.com/janelia_demo/multiplex_janelia_demo_version.npz). This file is prepopulated with labels.
2. Drag and drop the file onto the dropzone on the <a href="https://label.deepcell.org" target="_blank">DeepCell Label</a> homepage.
3. The file will be displayed in the single-channel viewing mode at first. Press <kbd>Ctrl</kbd> + <kbd>B</kbd> to change to RGB mode.

![Change viewing mode of RGB sample image](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/bebi205_demo/toggle_RGB_mode.png)

### Relevant tools/actions

- [brush](#brush-tool)
  - [expand a label](#expand-a-label)
  - [make a label smaller](#make-a-label-smaller)
  - [fix the boundary between labels](#fix-the-boundary-between-labels)
  - [add a new label](#add-a-new-label)
  - [remove a label](#remove-a-label)
  - [paint quickly with a large brush](#paint-quickly-with-a-large-brush)
  - [adjust fine detials with a small brush](#adjust-fine-detials-with-a-small-brush)
  - [combine two labels](#combine-two-labels)
  - [split a label into two](#split-a-label-into-two)
- [replace](#replace-action)
  - [delete labels by replacing with no label](#delete-labels-by-replacing-with-no-label)
  - [fix spilt labelings](#fix-spilt-labelings)

### Brush Tool

Press <kbd>B</kbd> to use the Brush tool.

The Brush will paint the foreground label over the background label. See the Selecting Labels tab for details on selecting labels.

Click and drag with the Brush to paint the foreground label over the background label.

The Brush lets us correct label borders, or even draw labels from scratch. The Brush is the most flexible tool to make pixel-level changes, but also requires more work to get high-quality results.

#### Use cases

- #### expand a label
  - Select the label you want to pain with as the foreground and "no label" as the background.
  - Paint over unlabeled areas to expand the selected label.
- #### make a label smaller
  - Select "no label" as the foreground and the label you want to shrink as the background.
  - Paint over the label the label to remove it.
- #### fix the boundary between labels
  - Select one label as the foreground and the other as the background, and paint to expand the foreground into the background.
  - Press <kbd>X</kbd> to switch the foreground and background and paint in the other direction.
- #### add a new label
  - Press <kbd>N</kbd> to select a new, unused label as the foreground, and select "no label" as the background.
  - Paint over unlabeled areas to add the new label to the canvas.
- #### remove a label
  - Select the label to remove as the background, adn select "no label" as the foreground.
  - Completely paint over the label to remove it.
- #### paint quickly with a large brush
  - Press the <kbd> ↑</kbd> to make the brush larger.
  - Paint with a large brushes to make quick and broad changes.
- #### adjust fine detials with a small brush
  - Press the <kbd> ↓</kbd> to make the brush smaller.
  - Paint with a small brushes for precise detail work.
- #### combine two labels
  - Select one label as the foreground and the other as the background.
  - Paint over the entire background label to combine the two labels into one.
- #### split a label into two
  - Select a label you want to split as the background, and press <kbd>N</kbd> to select a new, unused label as the foreground.
  - Paint over the existing label to replace it with the new label.

### Replace Action

Unlike the brush tool that we click to use, replace is an an action that we use through a keybind.

Select the label you want to keep, then select the label you want to replace, then press <kbd>R</kbd> to replace the second label with the first. A prompt will appear in **confirm action** where we can:

- press <kbd>Enter</kbd> to replace the label in the current frame
- press <kbd>Space</kbd> to replace the label across all frames, or
- press <kbd>Esc</kbd> to cancel

#### Use cases

- #### delete labels by replacing with no label
  - Select "no label" as the foreground and the label you want to replace as the background.
  - Replace to remove the label entirely, including unconnected pieces.
  - Use this to delete labels of debris or other image artifacts.
- #### fix spilt labelings
  - Select the labels you want to combine as the foreground and the background.
  - Replace to give both regions the foreground label.

## Example: nuclear image

### Download

1. Download the nuclear imaging .npz file from our [S3 bucket](https://caliban-input.s3.us-east-2.amazonaws.com/janelia_demo/HeLa-S3_nuc_seg_demo.npz). This file is prepopulated with labels.
2. Drag and drop the file onto the dropzone on the <a href="https://label.deepcell.org" target="_blank">DeepCell Label</a> homepage.

### Relevant tools/actions

- [autofit](#autofit-tool)
  - [clean up a rough brush stroke](#clean-up-a-rough-brush-stroke)
  - [smooth rough borders](#smooth-rough-borders)
- [grow/shrink](#grow/shrink-tool)
- [watershed](#watershed-tool)
  - [split two cells with the same label](#split-two-cells-with-the-same-label)

### Autofit tool

Press <kbd>M</kbd> to use the Autofit tool. The Autofit tool adjusts foreground label boundary to hug the nearest edges in the raw image.

Click a label once to select it as the foreground label, then click on it again to Autofit the label.

Use cases

- #### clean up a rough brush stroke

  - After filling in the rough shape of a label with the Brush, click on the label with Autofit to snap the brush stroke to the cell border.

- #### smooth rough borders
  - Click on a label with Autofit after thresholding to smooth the borders.
  - Thresholding often results in rough borders with stray pixels.

### Grow/Shrink tool

Press <kbd>Q</kbd> to use the Grow/Shrink tool.

The Grow/Shrink tool expands the foreground label by one pixel or contracts the background label by one pixel.

Click on the foreground label to grow its border by one pixel.

Click on the background label with to shrink its border by one pixel.

While you using the Grow/Shrink tool, you can click on an unselected label to make it the foreground or <kbd>Shift</kbd> + click on a to make it the background.

### Watershed tool

Press <kbd>W</kbd> to use the Watershed tool. Watershed can split a single label that contains two cells into two separate labels.

The Watershed tool works best when the two cells have bright centers and a dim borders around them. You may need to undo and try other tools like the Brush or Thresholding if Watershed does not split the cells well.

Use cases

- #### split two cells with the same label
  - Click on the center of two cells that have the same label. Each spot that you click will become two separate labels.

## Example: Human Protein Atlas image

### Download

1. Download the Human Protein Atlas .png image from our [S3 bucket](https://caliban-input.s3.us-east-2.amazonaws.com/janelia_demo/HPA_512_example.png). This image is not paired with any labels.
2. Drag and drop the file onto the dropzone on the <a href="https://label.deepcell.org" target="_blank">DeepCell Label</a> homepage.

### Relevant tools/actions

- [threshold tool](#Threshold-tool)
  - [add an unlabeled cell](#add-an-unlabeled-cell)
  - [adjust the boundary of an existing label](#adjust-the-boundary-of-an-existing-label)
- [trim tool](#Trim-tool)
  - [remove stray pixels from thresholding](#remove-stray-pixels-from-thresholding)
  - [remove artifacts](#remove-artifacts)
- [flood](#flood-tool)
  - [fix reused labels](#fix-reused-labels)
  - [fill in a hole](#fill-in-a-hole)
  - [fill in an outline](#fill-in-an-outline)

### Threshold tool

Press <kbd>T</kbd> to use the Threshold tool. Thresholding adds the foreground label to the brightess pixels within a box. Click and drag to draw a bounding box.

The Threshold tool will not overwrite any labels, and instead only adds labels in areas with no label.

Thresholding works best when cells have a clear bright signal. Make sure to include some background in your bounding box.

#### Use cases:

- #### add an unlabeled cell
  - Press <kbd>N</kbd> to pick a new label as the foreground.
  - Click and drag to create a bounding box around the area to threshold. The new label will be on the brightest areas inside the bounding box.
- #### adjust the boundary of an existing label
  - Select the label you want to adjust as the foreground.
  - Draw a bounding box around the label. The brightest pixels inside the box will get the same label.

### Trim tool

Press <kbd>K</kbd> to use the Trim tool.

Click on a label once to select it as the background. Click on it again to remove the disconnected pixels. Make sure to click on the part of the label you want to keep.

#### Use cases

- #### remove stray pixels from thresholding
  - Thresholding often adds labels to stray bright pixels.
  - Clear the stray pixels by clicking on the main center of the thresholded area with the Trim tool.
- #### remove artifacts
  - Stray regions can arise from labeling mistakes made by other people or from artifacts of computational labeling.
  - Click on the main region with the Trim tool to quickly remove detached areas while keeping the main region.

### Flood tool

Press <kbd>G</kbd> to use the Flood tool. Select the foreground label that you want to flood with and select the background label you want to flood over.

While using the Flood tool, you can simply click on an unselected label to make it the background label.

#### Use cases

- #### fix reused labels
  - Flooding a region allows us to fix our work after accidentally reusing a label value.
  - Press <kbd>N</kbd> to select a new label as the foreground and click to flood one of the regions with a new value.
  - Use this approach as long as the two regions are separate.
- #### fill in a hole
  - Some tools like threshold can leave a hole in the label.
  - Select the label you want to fill the hole with as the foreground, then click on the hole to select it as the background or fill the hole.
- #### fill in an outline
  - You can intentionally create holes to quickly create a large label.
  - Paint an outline of a large object with the Brush tool, then fill in the center with the Flood tool.

## Example: timelapse and 3D files

We do not have an example timelapse file prepared for this workshop. Here are some tools and use cases specific to working with timelapse files.

### Relevant tools/actions

- replace
  - [make labels consistent across time](#make-labels-consistent-across-time)
- swap
  - [swap the places of two labels](#swap-the-places-of-two-labels)
- flood
  - [remove one region](#remove-one-region)

### Replace

- #### make labels consistent across time
  - Select the label you want to use for a cell across all frames.
  - Move through frames with <kbd>A</kbd> and <kbd>D</kbd>, or <kbd>←</kbd> and <kbd>→</kbd>
    and select inconsistent labelings of the cell as the background.
  - Replace the background label with the desired foreground label.

### Swap

- #### swap the places of two labels
  - Rather than replacing two labels in succession, you can swap the two to.
  - Select two labels, then press <kbd>s</kbd> key to swap the selected labels.
  - A prompt will appear in the "confirm action" row to confirm the swap where we can:
    - press <kbd>Enter</kbd> to swap the labels,
    - press <kbd>Esc</kbd> to abort the action.

### Flood

- #### remove one region
  - Select "no label" as the foreground and click on an unwanted region with the Flood tool to remove that region.
  - Use this as an alternative to Trim if you want to remove only some of the unconnected regions, like for a branching structure in 3D.

## Export labels

![DeepCell Label download button](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/download_button.png)

Download your labels with the download button above the infopane. Your raw images and labels are stored together in the .npz file as training data for model training. The raw images are stored in an array named `X` with shape `(frames, width, height, channels)` and the labels are stored in an array named `y` with shape `(frames, width, height, channels)`.

Ready to put your training data to use? Quickly [train your own model](../model_training) with DeepCell.
