##### [jam3-lesson](https://github.com/Jam3/jam3-lesson) » photoshop

---

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

---

# Designing efficient SVGs for smooth animation

### Minimize the number of individual shapes in each file (use patterns when possible)
![image](https://cloud.githubusercontent.com/assets/743976/12837163/cce20dee-cb8d-11e5-9ae3-d5866f0fe99d.png)

When creating images with repeating patterns, create an actual [repeating pattern](https://helpx.adobe.com/illustrator/how-to/create-apply-patterns.html) in Illustrator, and set that pattern as a shape's fill. Do not copy and paste hundreds of individual dotted shapes.

This can be the difference between a 12MB file and a 5kb file.

#### Delete all shapes that aren't visible

When using a mask, it's tempting to not bother to remove the shapes that are hidden behind by the mask. But if you export the SVG, each of those hidden shapes still take up space.

Please trim your shapes so that shapes outside the mask are not included in exporting

### Expand your strokes.
When an svg is scaled, stroke widths remain the same.  
If you want a line's thickness to scale along with the image, you need to select the line and expand it into a shape

### Do not use raster/photoshop filters

Only use "Illustrator filters". 

![image](https://cloud.githubusercontent.com/assets/743976/12837325/925a2d44-cb8f-11e5-9e59-58bdeae24066.png)

You can download more illustrator filters from the internet.
Using raster/photoshop filters will result in the exported image no longer being a vector file but instead a vector bitmap (can't scale, can't animate, can't change colors)

### Avoid filters  

SVG filters result in laggy animations, especially opacity and noise and grains. Adding noise as a filter will make the svg ridiculously slow to animate on anything except Chrome.  

### Test on Safari and IE to see if SVGs are performant

Developers will likely only try and "okay" it in Chrome. Safari and IE deal with SVG animations significantly more poorly than Chrome does

### Check your exported SVG's filesize
SVGs should usually be under 30kb. If your SVG ends up being larger than 200kb, something probably went wrong.
Grab a developer and have him/her take a look.
