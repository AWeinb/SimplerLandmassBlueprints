# SimplerLandmassBlueprints
Refactored version of parts of the 4.26 Landmass Blueprint Brushes

You need:
- The Unreal Engine 4.26
- The Landmass Plugin
- A mouse to move the golden objects around to refresh the landscape.

## Description
My initial painpoint was that the usual auto-paint approach for
landscapes was not allowing me to use the grass tool because no
real paint-layer weights were available. At least this
was my understanding.

In order to create these weights I tried to use the existing landmass
plugins brushes but they were somewhat hard to understand and modify.
I extracted the weight-adjustment features and, as it was similar, also
the material based height-adjustment features.

There are some masks provided which most base on a somewhat working
algorithm to compute the normal of the landscape.

In my understanding it should not matter what you do in these
brushes as they are not really shipped in the final product but
only used to customize your landscape. If thats true, this approach
to coloring the landscape may be a bit more efficient than
evaluating the masks in the real landscape material. But take this
with a grain of salt as I am no Unreal professional.

I found that the brushes tend to "forget" values of the private
variables (I dont mean the local ones). This made the refactoring
really hard as this wasnt something i expected. I went ahead and
reused the original manager approach but used it only as a cache.

I dont think I will make anything useful with these brushes and
this all was probably just to play around with the engine. But
as it could be something useful for other I thought I would just
put it here.

## Screenshots
In the picture very steep areas are supposed to be blue, areas x units 
below the brush should be green, and flatter parts red. Some areas are 
black because they dont receive any love and some are of mixed colors 
because they get more of it. Also i painted manually at some places.
___
![Screenshot](https://user-images.githubusercontent.com/4525893/119810964-da59b600-bee6-11eb-9c85-f81c104c7149.jpg)
___
![grafik](https://user-images.githubusercontent.com/4525893/119811330-450af180-bee7-11eb-8c93-86ba86919974.png)
