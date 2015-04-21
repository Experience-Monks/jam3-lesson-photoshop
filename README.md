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

## layer comps

## measuring

## isolating

## mobile

## save for web

# illustrator

The main reason we use illustrator is to create svg files. SVG files are vector so they scale well to any resolution, perfect for reusing assets between desktop and mobile platforms.

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