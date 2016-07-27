<div class="series">JS1k 2015</div>
<div class="title">Part 2 : Buggy Island</div>
<div class="pubdate">2015-04-02</div>
<div class="lastmodifdate">2016-07-06</div>

<a class="illustration" href="//en.wikipedia.org/wiki/Tessellation">
    <img src="/cdn/img/tessellation.jpg" title="Tessellation"/>
</a>

In [the previous post](/2015/03/js1k-2015-part-1-introduction "js1k 2015 (part 1) : introduction"), I explained that my 2014 and 2015 demos were exploring the same rendering method, which basically is a simple combination of heightmap, vertical [voxels](//en.wikipedia.org/wiki/Voxel "voxel"), and standard perspective calculations. The way you perform heightmap [tessellation](//en.wikipedia.org/wiki/Tessellation "Tessellation") (chunking the surface into contiguous small parts) can bring bonus features, such as simple z-index compliance if you can easily bind traversal order and distance to viewer, and variable LOD if you can handle multiple tessellations with different degree of precision. One elegant (and compact) way to achieve both these goals is to use recursive tessellation, in which the surface is recursively divided into smaller parts, using a unique geometric formula.

<a class="illustration" href="//en.wikipedia.org/wiki/Gosper_curve#Properties">
    <img src="/cdn/img/gosper-island.png" title="Gosper island"/>
</a>

When preparing my 2014 entry, I knew the canonical recursive tessellation scheme used in computer graphics was the well-known [quadtree](//en.wikipedia.org/wiki/Quadtree "Quadtree"), but I wanted something more exotic for my use. What if each node didn't transform into 4 subnodes, but 7, one at the center, and the 6 others spread evenly around it ? Sure the surface of the juxtaposed subnodes isn't the same as the parent's (hexagons are not [rep-tiles](//en.wikipedia.org/wiki/Rep-tile "Rep-tile")), but if you find [the correct geometric transformation](//ecademy.agnesscott.edu/~lriddle/ifs/ksnow/flowsnake.htm "A bit of maths..."), all the nodes at a particular depth are perfectly contiguous. Turns out the resulting shape is well known to mathematicians under the name of "[Gosper island](//en.wikipedia.org/wiki/Gosper_curve#Properties "Gosper island")". This island is fractal by construction, which means that, even if its surface is finite, you'd better have good shoes and some [lembas](//en.wikipedia.org/wiki/List_of_Middle-earth_food_and_drink#Lembas "Lembas") if you intend to walk the coastal path (math nerd joke).

The Gosper island tessellation scheme had a number of benefits for my use:
- The generated heightmap is a tree that you traverse using standard [tree-traversal](//en.wikipedia.org/wiki/Tree_traversal "Tree traversal") algorithms, and for which depth is bound to LOD, which thus enables variable LOD applied to distance.
- The recursive surface is naturally island-shaped (hence the name), which was consistent with the use I intended.
- Given the camera angle, and the geometric distribution of the subnodes, you can determine the order in which you must traverse the list of subnodes to go from farthest to nearest, which seems to solve the z-index problem.

But it also has a few intrinsic drawbacks:
- As you go down one depth level, the granularity is multiplied by 1/√7 ≈ 0.38 , which is not as smooth a progression as for the quadtree (0.5).
- Due to the nature of the transformation, subzones are not convex, which makes the previously described z-index algorithm nothing more than a heuristic, and produces visual glitches where parts of the terrain are not rendered in the proper order and wrongly overlap over closer zones.
- The generation and traversal of 7 subnodes are a bit more complex to code and compress than their quadtree equivalent

<a class="illustration" href="//js1k.com/1966">
    <img src="/cdn/img/buggy-island.png" title="Buggy island"/>
</a>

Given the inherent problems and the lack of time, I struggled to put up a decent entry, but finally released "[Buggy island](//js1k.com/1966 "Buggy island")" with the following additions:
- elevation and landscape artifacts (rocks, trees, crenellated towers)
- water with sinusoidal waves
- [Z-clipping](//en.wikipedia.org/wiki/Clipping_%40computer_graphics%41#Occlusion_clipping_.28Z-_or_depth_clipping.29 "Z-clipping") disguised as fog to improve framerate

Colors were poor, framerate was awful, glitches were outrageous, but it still managed to reach 6th place.
In next post I'll explain how I put exotism aside for js1k 2015 and went back to good ol' quadtrees.
