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

## Whole-label modifications to annotation file

## Pixel-level modifications to annotation file
