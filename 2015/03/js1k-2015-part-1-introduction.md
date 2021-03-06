<div class="series">JS1k 2015</div>
<div class="title">Part 1 : introduction</div>
<div class="pubdate">2015-03-25</div>
<div class="lastmodifdate">2016-07-06</div>

<a class="illustration" href="//js1k.com/1966">
    <img src="/cdn/img/buggy-island.png" title="Buggy island"/>
</a>

Though the final version of [my js1k 2014 entry](//js1k.com/1966 "Buggy Island") wasn't a potential winner with its visual glitches and poor frame rate, I had put some hard work into it, and had a lot of (mainly mathematical) fun exploring recursive data structures and optimizing graph traversal algorithms. I felt this research area was a great mathematical and artistical playground, especially in the context of constrained creative coding such as js1k, so I decided to continue on the same path to publish [something really satisfactory](//js1k.com/2015-hypetrain/demo/2324 "Islands") for the 2015 edition.

<a class="illustration" href="//js1k.com/2013-spring/demo/1555">
    <img src="/cdn/img/strange-crystals-6.png" title="Strange crystals II"/>
</a>

[My 2013 entry](//js1k.com/2013-spring/demo/1555 "Strange crystals II") proved that a few thousands well used coloured rectangles can bring a satisfactory pseudo-realistic visual experience. Canvas' `fillRect` is fast enough for the job, as long as it is backed by a powerful engine to keep the rendering loop is as simple as possible. The "Strange Crystals" demo used this technique in conjunction with old-school 2.5D techniques to simulate a first-person mine cart ride. The data structure was directly bound to the z-index and made the rendering loop dead simple, letting room to enhance the visual evocation with stalactites, lightbulbs and other goodies.

<a class="illustration" href="//en.wikipedia.org/wiki/Pin_Art">
    <img src="/cdn/img/pinart.jpg" title="Pin art"/>
</a>

In 2014, I decided to go 3D by adapting the rectangle-based rendering technique to a heightmap. The idea was, given a terrain (altitude = f(x,y)), to tile the surface of the terrain, give each tile the height corresponding to the terrain's altitude at the center of the tile, and render the tiles with vertical rectangles to produce an approximate view of the terrain. When the tiles' width become smaller, the rendering gets more accurate and hopefully realistic. [Pin art](//en.wikipedia.org/wiki/Pin_Art "Pin Art") frames are a good real-world equivalent to this rendering technique.

<a class="illustration" href="//en.wikipedia.org/wiki/3D_projection">
    <img src="/cdn/img/projection.png" title="3D projection"/>
</a>

The 3D rendering process must be able to perform standard tasks:
- View frustum : only the tiles that are in the <a title="View frustum" href="//en.wikipedia.org/wiki/Viewing_frustum">view frustum</a> need to be rendered.
- Perspective: given a point of view, apply <a title="3D projection" href="//en.wikipedia.org/wiki/3D_projection">perspective calculations</a> when mapping the terrain coordinates to the canvas coordinates.
- Z-index: the distance between the tile and the viewer must be taken into account so that [distant tiles do not overlap closer tiles](//en.wikipedia.org/wiki/Hidden_surface_determination "Hidden surface determination").

<a class="illustration" href="//js1k.com/1966">
    <img src="/cdn/img/bonus.png" title="Bonus"/>
</a>

Bonus features include:
- Variable <a title="Level of detail" href="//en.wikipedia.org/wiki/Level_of_detail">level of detail (LOD)</a>: since distant zones don't need same rendering accuracy as closer zones, the rendering algo can profit from a multi-level tiling data structure.
- Memory efficiency: if some zones need less detail, the same layered data structure can help store sparse data in a more efficient way.

In [the next post](/2015/04/js1k-2015-part-2-buggy-island "Buggy Island") , I'll present the 2014 implementation of these principles, with its mathematical goodness and its inherent flaw.
