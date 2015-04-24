# Photoshop for developers

This is a brief intro on how to use photoshop as a developer, with a little sprinkling of illustrator

# sections

- [files](#files)
- [photoshop](#photoshop)
    - [layer comps](#layer-comps)
    - [measuring](#measuring)
    - [isolating](#isolating)
    - [mobile](#mobile)
    - [save for web](#save-for-web)
- [illustrator](#illustrator)
    - [svg formatting](#svg-formatting)
    - [svg exporting](#svg-exporting)

# files

Photoshop files are kept in a consistent folder structure on the fridge 

```ruby
THEFRIDGE \ Private \ _Projects \ [PROJECT NAME] \ DESIGNS \ DESIGN
└─┬ 02 Desktop \ 01 Working
| └── 01 psd
| └── 02 ai
| └── 03 ae
└─┬ 03 Mobile \ 01 Working
  └── 01 psd 
  └── 02 ai
  └── 03 ae
```

In each of those folders, you will find the files named by date.

# photoshop

Here are some useful tips and tricks for working with Photoshop as a developer. These methods do not describe the only way to do something, but are a good primer to getting started. Feel free to add a github issue if you want to add / modify to this lesson.

## layer comps

Our designers use Layer Comps to organize their photoshop files. It is a way of recording the current state of a photoshop document and quickly being able to switch to it. Usually we will have at least one layer comp per section. To open the Layer Comps panel, simply click Window -> Layer Comps. Here is an example of what the Layer Comps panel may look like.

![img](http://i.imgur.com/FPtbt2f.jpg)

## measuring

First of all, ensure the info panel is open (Window -> Info), this will display your x, y, width, and height as well as other values.

The easiest way to measure an object is to select any of the Marquee tools and simply trace the object. The info panel will update as you are changing your selection.

![img](http://i.imgur.com/4lnLhqq.jpg)

## isolating

It is often useful to isolate a layer to help measure things or export the image properly. To isolate a layer follow these steps:

- Select the Move Tool
- Hold alt/cmd and right-click on object in the image you want (this will select the correct layer)
- In the layers panel, hold alt/cmd and left-click on the eye (layer visibility)
    - You can alt/cmd and left-click the eye again to return the document to the previous state

To crop the document to a layer's width / height:

- Hold ctrl/cmd and left-click the layer thumb in the layer panel
    - At this stage you can get width / height from the info panel
- Click Image -> Crop to resize the document

## mobile

Our mobile documents are often designed in a retina state. This means that the document size is a twice or three times the size of the intended device's resolution. When exported images from the PSD, they should be kept at their twice the size state and then shrunk down via CSS. This ensures a crisp image when it is rendered on a device. This also means that any measurements / fonts sizes will have to be divided by the retina size to be displayed correctly.

Currently the common designed mobile resolution is 640 x 1136. This is for the iPhone 5/5s which has a screen resolution of 320 x 568 and a retina value of 2.

For example, if a font in the design is 24px, in your CSS, you would use 12px. The same goes for dom elements.

http://devices.jam3.net/ will help you determine a devices resolution and retina value.

## save for web

Make sure to save all images with the "save for web" option. Here are some default settings for the common export file types:

JPEG
compression: 80%
Optimized for smaller files, Progressive for larger filers

PNG-24
Default settings is fine as we compress gifs in the command line when publishing a project

GIF
Default settings is fine

# illustrator

The main reason we use illustrator is to create SVG files. SVG files are vector so they scale well to any resolution, perfect for reusing assets between desktop and mobile platforms.

## svg formatting

To create and optimal exported SVG, it is best to follow these steps:

- ctrl/cmd + a to select the entire SVG.
- Object -> Ungroup (If applicable)
- Object -> Expand
- Open the Pathfinder Panel (Window -> Pathfinder)
- Click Unite (Top left option)
- Object -> Artboards -> Fit to Artwork Bounds
- Save SVG

## svg exporting

For exporting SVG's for the web, these are currently the most optimal options

Profile: SVG 1.1
Fonts: Type — SVG; Subsetting — Only Glyphs Used (If using a custom font)
Image Location: Link
CSS Properties: Style Elements
Decimal Places: 1
Select: Output Fewer <tspan> Elements
Select: Use <textPath> Element For Text On Path

![img](http://i.imgur.com/v5PnlVK.jpg)
