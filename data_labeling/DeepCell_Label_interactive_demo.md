# Learn to label with DeepCell Label

## Table of Contents

- [DeepCell Label interface](#deepcell-label-interface)
  - [Infopane](#the-infopane)
  - [Canvas](#the-canvas)
  - [Undo/Redo]()
- [Example: tissue images](#example:-tissue-images)
- [Example: nuclear image](#example:-nuclear-image)
- [Example: Human Protein Atlas image](#example:-human-protein-atlas-image)
- Tools
- [Export labels](#export-labels)

## DeepCell Label interface

To learn the DeepCell Label interface, open the first example file on the homepage, named **3D organoid annotation**.

You should now see an interface that looks like this:
![DeepCell Label interface](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/overall_interface.png)

On the left, we see an infopane with data about what we are viewing.

On the right, we see an interactive canvas with labels overlaid on a raw image.

### The infopane

![DeepCell Label interface with infopane boxed](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/overall_interface_boxed_infopane.png)

The infopane tells us what we are viewing in the canvas. See the Info Pane tab of the dropdown instructions in Label to learn more about each row.

### The interactive canvas

![DeepCell Label canvas region of displayed page](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/interface_boxed_canvas.png)

#### The canvas

We use the canvas to:

- browse the image
- adjust the image for better viewing
- select labels
- edit selected labels

See the Canvas tab of the dropdown instructions to learn how to browse and adjust the images.

See the Select tab to learn how to select labels.

See the Tools and Actions tabs to learn how to edit the selected labels.

#### Undo and Redo buttons

Made a mistake? Undo or redo your modifications with Undo and Redo buttons above the canvas. We can also use the shortcuts **Ctrl+Z** to undo and **Ctrl+Shift+Z** to redo.

## Example: tissue image

### Download

1. Download the tissue imaging .npz file from our [S3 bucket](). This file is prepopulated with labels.
2. Drag and drop the file onto the dropzone on the <a href="https://label.deepcell.org" target="_blank">DeepCell Label</a> homepage.

## Example: nuclear image

## Example: Human Protein Atlas image

## Example: time-lapse images (?)

## Select Labels

Before we can edit a label, we must select it. When we select a label as the foreground label, we can add more that label, while selecting the label as the background lets us remove that label.

See the Select Labels tab of the dropdown instructions for more details and controls.

## Tools (fold into examples?)

### Brush Tool

Press <kbd>B</kbd> to use the Brush tool.

The Brush will paint the foreground label over the background label. See the Selecting Labels tab for details on selecting labels.

Click and drag with the Brush to paint the foreground label over the background label.

The Brush lets us correct label borders, or even draw labels from scratch. The Brush is the most flexible tool to make pixel-level changes, but also requires more work to get high-quality results.

#### Use case: expand a label

Select the label you want to expand as the foreground and "no label" as the background. You can now

#### Use case: make a label smaller

Select "no label" as the foreground and the label you want to shrink as the background. The Brush can now remove area from that label.

#### Use case: fix the boundary between two labels

Select one label as the foreground and the other as the background, and paint to expand the foreground into the background. Press <kbd>X</kbd> to switch the foreground and background and paint in the other direction.

#### Use case: change the brush size

Press the <kbb>↑</kbd> to make the brush larger.

Press the <kbd> ↓</kbd> to make the brush smaller.

Larger brushes let us make quick and broad changes, while smaller brushes are better for detail work.

#### Use case: combine two labels

Select one label as the foreground and the other as the background, and paint over the entire background label.

#### Use case: split a label into two

Select the label you want to split as the background, and press <kbd>N</kbd> to select a new, unused label as the foreground. Painting over the background will now replace it with the new label.

### Threshold tool

Press <kbd>T</kbd> to use the Threshold tool. Thresholding adds the foreground label to the brightess pixels within a box. Click and drag to draw a bounding box.

The Threshold tool will not overwrite any labels, and instead only adds labels in areas with no label.

Thresholding works best when cells have a clear bright signal. Make sure to include some background in your bounding box.

#### Use case: add an unlabeled cell

Press <kbd>N</kbd> to pick a new label as the foreground. Click and drag to create a bounding box around the area to threshold. After you release the mouse, the brightest areas inside the bounding box will have the new label.

#### Use case: expand the boundary of an existing label

Select the label you want to adjust as the foreground, and then draw a bounding box around it. The brightest pixels around that label will get the same label.

### Trim

Press <kbd>K</kbd> to use the Trim tool. Click on a label once to select it as the background. Click on it again to remove the disconnected pixels. Make sure to click on the part of the label you want to keep.

#### Use case: remove

Stray pixels can arise from labeling mistakes made by other people or from artifacts of computational labeling. Trimming will quickly remove them while keeping the main region.

#### Use case: remove stray pixels from thresholding

Thresholding often adds labels to stray bright pixels.
We can clear the stray pixels by clicking on the main center of the thresholded area.

### Flood

Press <kbd>G</kbd> to use the Flood tool. Select the foreground label that you want to flood with and select the background label you want to flood over.

While using the Flood tool, you can simply click on an unselected label to make it the background label.

#### Use case: draw and flood an outline

We can quickly label from scratch by drawing an outline of a large object and flooding in the center of the label.

#### Use case: fix reused labels

Flooding a region allows us to fix our work after accidentally reusing a label value. As long as the two regions are separate, this mistake can be easily fixed by flooding one of the regions with a new value.

#### Use case: fill in a hole

When flooding a hole in a label, the Flood tool will not flood diagonally connected pixels. Not flooding these diagonal connections prevents flooding all unlabeled regions accidentally. Holes are often artifacts that we want to remove.

#### Use case: remove regions by flooding with no label

You can select "no label" as the foreground to remove unwanted labeled regions. Use this as an alternative to Trim if you want to remove only some of the unconnected regions.

### Watershed Tool

Press <kbd>W</kbd> to use the Watershed tool. Watershed can split a single label that contains two cells into two separate labels.

#### Use case: split two cells that have the same label

Click on the center of two cells that have the same label. Each spot that you click will become two separate labels.

The Watershed tool works best when the two cells have bright centers and a dim borders around them. You may need to undo and try other tools like the Brush or Thresholding if Watershed does not split the cells well.

### Grow/Shrink Tool

Press <kbd>Q</kbd> to use the Grow/Shrink tool.

The Grow/Shrink tool expands the foreground label by one pixel or contracts the background label by one pixel.

When you Click on the foreground label, its boundary grows.

When you Click on the background label, its boundary shrinks.

### Autofit Tool

Press <kbd>M</kbd> to use the Autofit tool. The Autofit tool adjusts foreground label boundary to hug the nearest edges in the raw image.

Click a label once to select it as the foreground label, then click on it again to Autofit the label.

#### Use case: improve a rough brush stroke

After filling in the rough shape of a label with the Brush, you can use Autofit to snap the brush stroke to the cell border.

#### Use case: clean border with artifacts

Thresholding often results in rough borders with stray pixels. Autofitting after thresholding can be an easy way to smooth the borders.

## Actions

### Swap labels

Select two labels, then press <kbd>s</kdb> key to swap the selected labels. A prompt will appear in the "confirm action" row to confirm the swap where we can:

- press <kbd>Enter</kbd> to swap the labels,
- press <kbd>Esc</kbd> to abort the action.

Swapping only affects the labels in the current frame.

This can be useful in timelapse or 3D files with many frames, where consistent labels across each frame are required for labeling correctness.

### Replace one label with another

Select the label you want to keep, then select the label you want to replace, then press <kbd>R</kbd> to replace the second label with the first. A prompt will appear in **confirm action** where we can:

- press <kbd>Enter</kbd> to replace the label in the current frame
- press <kbd>Space</kbd> to replace the label across all frames, or
- press <kbd>Esc</kbd> to cancel

#### Use case: delete labels by replacing with no label

Select "no label" as the foreground and the label you want to replace as the background. Replacing will remove the background label entirely, including unconnected pieces. Use this to delete labels of debris or other image artifacts.

#### Use case: fix spilt labelings

You can combine two labels that should be the same cell by replacing one adjacent label with the other in the current frame.

"Split" labels are a common error in both computationally- and manually- labeled files.

#### Use case: combine lineages in time lapses or image stacks

If one cell has multiple labels across a time lapse or 3D stack, use replace across all frames to make that cell have a consistent label throughout the timelapse.

## Export labels

![DeepCell Label download button](https://figure-eight-deepcell.s3.us-east-2.amazonaws.com/instructions_and_examples/janelia_demo/download_button.png)

Download your labels with the download button above the infopane. Your raw images and labels are stored together in the .npz file as training data for model training. The raw images are stored in an array named `X` with shape `(frames, width, height, channels)` and the labels are stored in an array named `y` with shape `(frames, width, height, channels)`.

Want to explore an alternate viewing option for multichannel images? Check out [what differences to expect in RGB mode](./DeepCell_Label_RGB.md).

Ready to put your training data to use? Quickly [train your own model](../model_training) with DeepCell.
