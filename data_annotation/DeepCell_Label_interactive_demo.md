# Exploring data annotation with DeepCell Label

### To get started on the demo file:
 1. Download .npz file from our [s3 bucket](link). This file is prepopulated with labels.
 2. Use drag and drop interface to open file with [DeepCell Label](link). (image?)

## Understanding the DeepCell Label interface
You should now see an interface that looks like this:
(image)

On the left is the information display for the file and the labels within it. On the right is the canvas you will interact with to make display adjustments and modify labels in the file.

### The information pane
(image)

#### Frame, Channel, and Feature information
(image)
DeepCell Label is designed to work with biological images, which often have multiple dimensions. To help keep track of what part of your file you are working on, the information pane will always display the frame, channel, and feature that are actively being viewed. 
 - "Frame" starts at zero and can refer to different timepoints in a sequence of timelapse images, or it can refer to different slices of a 3D image, depending on your data. 
 - "Channel" starts at zero and refers to different channels of the input image. 
 - "Feature" starts at zero and refers to different types of annotations that may be included in the file; "features" can be thought of like "channels" for different annotations. For example, an annotation file could contain one feature for nuclear segmentations and another for whole-cell segmentations to keep different annotations for the same cells paired together.
 
 We will see these fields update as we navigate through the demo file.

#### Field of View information
(image)
DeepCell Label supports zooming in on and panning across images. The current level of zoom and the region being viewed will always be displayed. You will not typically need to reference these values during annotation, but may find it helpful to be able to specifiy interesting regions of an image to direct others to, or to return to later.

#### Highlighting information
(image)
Highlighting is a feature of DeepCell Label that helps emphasize the label(s) you are currently interacting with. By default, highlighting is turned on and no labels are highlighted to start with. As you work, you may want to check the status of the highlight feature or see which labels are actively being highlighted. We will cover how to use the highlighting tool in more detail later in the demo.

#### Editing mode information
(image)
DeepCell Label has two modes of interacting with labels, "whole-label" and "pixel-editing". For a reminder of which mode you are in, you can check this section of the infopane. Additional information will be displayed while in the pixel-editing mode of DeepCell Label. Information specific to pixel-editing mode covers:
- "Brush size" - the current size of the brush tool
- "Editing label" - which label (if any) the brush is currently set to modify, starting at 1 by default
- "Eraser" - whether the brush is currently set to draw or erase labels

#### Label-specific information
(image)
When mousing over labels in the interactive canvas, additional information about those labels will be displayed. For typical annotation files, you will see the value of the label, as well as which frames ("slices") of the file it is present in. This information tends to be quite useful for timelapse or 3D annotations, but is not as relevant for static, 2D labeling projects. This part of the information panel will be blank if the mouse cursor is not positioned over a label.

#### State
(image)
This part of the infopane will show you information and prompts related to interactions with the file. For example, selected labels will be shown in "state" information. When using actions in whole-label mode or some features of pixel-editing mode, confirmation prompts and other messages will be displayed in "state" as well. We will cover the different information you may see in "state" during the relevant portions of the demo.

### The interactive canvas
(image)

#### Undo and Redo buttons
(image)
Made a mistake? Quickly undo or redo your modifications with the buttons above the canvas (keyboard shortcuts available as well). These buttons can only be clicked when there are changes that can be undone or redone.

#### Interactive canvas
(image)
The interactive canvas is where most of your interaction with the file will take place. This canvas displays images (labels, input images, or a combination of the two) and registers click locations as well as other information. To select a label, for example, you click on the label of interest in the canvas. The different ways you can interact with the canvas to view and modify the file will be covered in later sections of the demo.

#### Canvas borders
(image)
The borders surrounding the interactive canvas serve a purpose as well--these change colors as a visual indicator to help contextualize your work at a glance. When a border is white, that means you are viewing the edge of the image. When a border is black, that indicates that more of the image exists off-canvas in that direction, and can be accessed by panning or zooming out.

## Image viewing options and controls
You should have the demo file (link) loaded to follow along and try these controls for yourself.

### Changing between input image and label views
(image of input image, raw image, and overlay image side by side)

#### Changing interaction mode also changes display
The two main interaction modes, whole-label and pixel-editing modes, also have different image displays. The files open in pixel-editing mode by default, where the images are displayed as an overlay of labels on top of the input image. You can switch back and forth between whole-label and pixel-editing modes with the "e" key. In whole-label mode, you will see either the input image or an image of the labels.

#### Changing between input and label images in whole-label mode
To switch between these viewing modes, use the "z" key. Note that even when labels are not displayed on screen, you can still hover over image regions to see label information in the infopane, and can select these labels for actions.

### Changing the field of view

#### Zooming
To zoom in and out on the image, you can hold down the alt key on your keyboard while scrolling up and down over the interactive canvas. Alternatively, you can zoom out with the "minus" key (-) on your keyboard and zoom in with the "equals" key (=) on your keyboard. Note that you can't zoom out past 100%, since at that level of zoom, the full image is scaled so that the display fits in your browser window.

#### Panning
You can pan around the image when it is zoomed in at any level above 100%. To pan, hold down the spacebar while you click and drag. You will not be able to pan past the edges of the image.

### Adjusting image brightness and contrast

#### Adjusting contrast
To adjust the contrast of the input image, scroll up or down over the interactive canvas. This adjustment will often be the most helpful for increasing the visibility of objects. The contrast will be adjusted only if you can see the input image in your display (no adjustment will be applied if you are on the labels-only view).

#### Adjusting brightness
To adjust the brightness of the input image, hold down the shift key while scrolling up or down over the interactive canvas. Like contrast adjustment, the brightness will only change if you can see the input image in your display.

#### Resetting brightness and contrast
Press the zero (0) key to reset brightness and contrast to their default values. You can also undo and redo brightness and contrast changes with the undo/redo buttons or keyboard shortcuts.

#### Inverting light/dark (pixel-editing mode)
Inverting the grayscale input image in pixel-editing mode can sometimes help visualization of the label overlay image. To invert the image, press the "i" key while in pixel-editing mode. This will not affect the image display when in whole-label mode.

### Highlighting labels
The "h" key will turn highlighting on and off. Highlighted labels work slightly differently in pixel-editing and whole-label modes, so we will cover highlighting in more detail later. Turning highlighting on and off only affects how the labels are displayed to you, and does not affect the actual labels in the file.

### Changing the part of the file being displayed
Each of these controls will only work if there are alternate parts of the file to be displayed. Eg, you can't change frames in a file that only has a single frame.

#### Change channel
To change the channel of the input image being displayed, press "c" or shift + c. (Shift + c will change channels in the opposite order that "c" does but otherwise works the same.) Note that there must not be selected labels (whole-label mode) to change channels, as the "c" key can also be used for some actions in this mode. You do not have to have the input image visible to change channels.

When you change channels, you should see the "channel" information in the infopane update. Your brightness and contrast adjustments for each channel will be stored seperately. Try adjusting the brightness and contrast in a few channels and see what it's like to cycle between them!

#### Change feature
Changing features works similarly to changing channels in a file, and uses the "f" key or shift + f. Like changing channels, there must not be labels selected, and you do not need to have the labels displayed to change features. This demo file only contains one feature, so you will not be able to try this functionality right now.

#### Change frames
To go forward through frames in a file, press the "d" or right arrow key. To go backward through frames in a file, press the "a" or left arrow key. You can go backward from the first frame in the file to cycle back to the end of the file, and can go forward from the last frame of the file to return to the beginning. When you change frames, you should see the "frame" information in the infopane update, with the displayed image updating shortly afterward.

Now that you know how to move through and view files with DeepCell Label, take a minute to explore the file. Next, we will cover whole-label actions starting in frame 7 of the demo file, so make sure you are able to get to this frame and toggle whole-label mode using the controls covered so far.

## Whole-label modifications to annotation file
In this section, we will cover the different whole-label actions available to modify annotation files. We will use these actions to fix specific errors throughout the label file, but you can also try them on other labels to see how they work.

### Selecting labels in whole-label mode
Labels are selected by clicking on them. Up to two labels can be selected in whole-label mode. Some actions require just one label, while others require two labels. Clicking on labels once two have been selected will overwrite the second label selected.

#### Highlighted labels in whole-label mode
In whole-label mode, selected labels can be displayed with a highlight. This will change the color of the selected labels to be red, and only affects how the labels are displayed to you. We recommend that highlighting be kept on so you can be sure you have selected the label(s) you intend to modify. If only one label is selected, you can cycle the highlight to different labels with the bracket keys ( \[ and \] ); this will also deselect the original label you clicked on.

### Swapping labels
Two labels can be swapped with each other to change the value of each label. This can be useful in timelapse or 3D files, where linking labels across different frames is an important aspect of labeling the full file.

To swap two labels, select two different labels, then press the "s" key. A message will appear in "state" asking you to confirm the swap; you can either swap the labels in the same frame (press "s" again to choose this option), or swap them across all frames (press spacebar to confirm this option).

#### Suggested swap
(image)
Labels 16 and 19 are consistent across most frames in this file, except for in frame 7, where they have swapped places. Swap them back to fix this labeling error.

### Trimming stray pixels
Sometimes, labels may have a few stray, unconnected pixels that should be removed from an annotation. These are often due to labeling mistakes made by other people, but can also be artifacts of computational labeling. We can quickly and conveniently remove these from the file with the "trim pixels" functionality. This action will not have an effect if there are no stray pixels to remove from a label.

To use this action, hold down the shift key while you select a label. *Note: for this action, the click location of your selection does matter. Make sure to click on the part of the label you want to keep.* A message will appear in "state" asking you to confirm the action; press spacebar to confirm and apply the action.

#### Suggested label to trim pixels from
Frame 8 in the file has a stray brushstroke with label 28. (Label 28 has a large hole in the center, but you can also select the brushstroke to use highlighting to see where the other part of the label is.) To get rid of the stray brushstroke, hold down the shift key while you click on the real part of the label to select it, and confirm the action with spacebar.

### Filling holes in labels
Labels may have holes in them; use hole filling to quickly fix these errors instead of using a brush tool to manually fill in the gap. Holes are most often computational artifacts, but you can also use this functionality to speed up labeling objects from scratch by drawing an outline and filling in the rest of the label.

To fill a hole, first select the label you want to fill a hole in. Next, press the "f" key. Then, click on the hole to fill (there is no confirmation with spacebar for this action).

#### Suggested hole to fill
Label 28 in frame 8 has a large hole in it. Use the hole fill action to quickly fix this annotation mistake.

### Flood part of a label with a new label
Accidentally reusing a label value is a common annotation mistake. As long as the two labels are separate, this can be easily fixed by flooding one of the labels with a new value.

To flood a region of a label, hold down the alt key while you click on the region you wish to flood. *Note: for this action, the click location of your selection does matter. Make sure to click on the part of the label that you want to change the value of.* A message will appear in "state" asking you to confirm the action; press spacebar to confirm and apply the action. This action will work even if the selected label only appears in one place.

#### Suggested label to flood
(image)
Label 27 in frame 9 appears in two locations. Select label 27 and compare frame 8 to frame 9 to see that one region of label 27 should be modified to be a different value. Use the label flooding action to fix the duplicate label 27. (Note: if you flood the wrong part of the label, you can undo the action and try again, or you can use the swap action to get the labels in frame 9 to match up with frames 8 and 10.)

### Replace one label with another
"Split" labels are a common type of annotation mistake seen in both computationally and manually generated label files. In this type of mistake, one object is annotated with two different labels. These two labels can easily be merged into one with the replace action. "Replace" can also be used to link two sequences of labels that belong to the same object across timelapse or 3D images.

To replace one label with another, first select the label you want to keep, then select the label you want to replace. For this action, the order of selection matters, but the location in the label you click on does not. Press "r" to trigger the replace action. A message will appear in "state" asking you to confirm the replacement; you can either replace the labels in the same frame (press "s" to choose this option), or replace one label with the other across all frames (press spacebar to confirm this option). Use the single-frame option for fixing split errors and the all-frames option for merging lineages.

#### Suggested label to replace
In frame 10, label 17 is mistakenly split into labels 17 and 42. Use the single-frame replace action to replace 42 with 17.

### Split one label into two with watershed transform
A "merged" label error is when two adjacent objects are annotated with the same label (the opposite of a "split" label error). Sometimes, merged objects can be distinguished from each other by the brightness of the objects. When the objects are bright and have a distinct area of dimness separating them, the labels can be split apart accurately with the "watershed" action.

To use this action, select the center of each object (click location matters). You will have the same label selected twice. Then, press "w" and confirm the prompt shown in "state" with the spacebar. The selected label will be split into the original label and a new label. The first click location will keep the original label and the second click location will be assigned the new label. Watershed will not necessarily work well in every case; alternatives exist for splitting apart labels in DeepCell Label.

#### Suggested label to split with watershed
(image)
Label 25 in frame 11 is an example of a merged label that can be fixed with watershed. Try using the watershed action to split it apart--if the resulting label boundary does not look good, you can undo the action or replace the new label with the old label, and try again with different click locations.

### Creating new labels
Sometimes, you need to unlink sequences of labels in timelapse or 3D files. For example, if a cell divides and one of the daughter cells is given the same label as the parent, it is appropriate to give a new label to the daughter cell in the frames where it is present. This can be done with the "create" action: select the label that should get a new label, then press "c". A message will appear in "state" asking you to confirm the label creation; you can either create a new label in just that frame (press "s" to choose this option), or in all subsequent frames (press spacebar to confirm this option). The single-frame option is different from the label flooding action we used earlier, as creating a new label with "c" will change all pixels of the label in the frame, not just connected pixels. Use the "all subsequent frames" version of the action when unlinking two objects from each other that are otherwise labeled correctly.

This file does not contain a specific error that is best fixed with the create action, but you can try it out on any labels you would like. Try creating a new label in multiple frames with the "all subsequent frames" version of the action, then link the two sequences back together with the replace action applied in all frames to understand these actions better.

## Pixel-level modifications to annotation file
