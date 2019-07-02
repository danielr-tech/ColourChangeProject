## Changing a colour

Find and name an image:

![Pencils, named](images/myImagePencils.png)

Choose a colour in the image (e.g. Green) and change it to another colour (e.g. Blue):

```
ImageRecolor[myImage, Green -> Blue]
```

![Pencils recoloured manually](en/images/PencilsRecolour1.png)

Find the dominant colours in the image. Choose one and change that colour:

```
chosenColour = DominantColors[myImage][[5]];

ImageRecolor[myImage, chosenColour -> Purple]
```

![Pencils recoloured by dominant colours](images/PencilsRecolour2.png)


## Choosing a tolerance

Use `ColorsNear` to set a tolerance level (e.g. 0.1):

```
ImageRecolor[
    myImage,
    ColorsNear[Green, 0.1] -> Blue
]
```


## Creating a tool

--- task ---

Use `Manipulate` to change the tolerance level:

```
Manipulate[
    ImageRecolor[
        myImage,
        ColorsNear[Purple, tolerance] -> Blue
    ],
    {tolerance, 0.1, 1, 0.05}
]
```

![Pencil Manipulate 1](images/PencilManipulate1.png)

Add parameters for the first and second colour in the tool:

```
Manipulate[
    ImageRecolor[
        myImage,
        ColorsNear[colour1, tolerance] -> colour2
    ],
    {tolerance, 0.1, 1, 0.1},
    {colour1, DominantColors[myImage]},
    {colour2, Blue}
]
```

![Pencil Manipulate 2](images/PencilManipulate2.png)


## Challenges

Show the original and modified images side by side:

```
GraphicsGrid[
    {{
        myImage,
        ImageRecolor[
            myImage,
            ColorsNear[Purple, tolerance] -> Blue
        ]
    }},
    ImageSize -> 500
]
```

Create a colour-changing function:

```
imageRecolouring[image_, numberOfColours_] :=
    Manipulate[
        GraphicsGrid[
            {{
                image,
                ImageRecolor[
                    image,
                    ColorsNear[colour1, tolerance] -> colour2
                ]
            }},
            ImageSize -> 500
        ],
        {colour1, DominantColors[image, numberOfColours]},
        {colour2, Blue},
        {tolerance, 0.1, 1, 0.5}
    ]
```

![Colouring function](images/ColouringFunction.png)