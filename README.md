# LandmassEffectBrush
Refactored version of parts of the 4.26 Landmass Blueprint Brushes.
The latest version is for UE5.

You need:
- The Unreal Engine 5.x
- The Landmass Plugin

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

## How-to
Content\Editor\Landscape\LandmassEffectBrush contains LandmassEffectBrush.uasset
which is a Landscape brush. The class itself does nothing to the landscape.
It uses effect components that do some kind of change to the heightmap or
weightmaps. The effects can be restricted to specific area using mask
components.

In order to make it work you need to:
- Create a landscape.
- In the landscape editor create a layer and use the blueprint menu to add the LandmassEffectBrush.
- The brush is then an actor in the world (additionally a cache object is created).
- Go back to the usual selection mode.
- Select the brush actor in the outliner.
- Take a look at the Details as the actor has some settings there.
- To add an effect click the plus in the component outline of the actor and search "effect".
- You should find something that extends IsLandmassBrushEffect.uasset. like NoiseEffect.
- There should be some kind of change to the landscape, if not try a "trigger update" (the button should be in the Details).
- To mask something add a "mask" component to the effect (or the brush).
- The spline mask needs an additional spline component. Add that like the other components under the mask component. Then create some curve.
- I hope it works otherwise it can be a pain to debug it as the debugger doesnt seem to work in these classes.

If you get it working it can be easier to hack the classes or to create custom variants instead of using
the predefined stuff. This way you have more possibilities.

## Screenshots
In the picture very steep areas are supposed to be blue, areas x units 
below the brush should be green, and flatter parts red. Some areas are 
black because they dont receive any love and some are of mixed colors 
because they get more of it. Also i painted manually at some places.
___
![Screenshot](https://user-images.githubusercontent.com/4525893/119810964-da59b600-bee6-11eb-9c85-f81c104c7149.jpg)
