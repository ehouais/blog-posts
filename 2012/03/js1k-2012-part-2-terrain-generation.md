<div class="series">JS1k 2012</div>
<div class="title">Part 2 : terrain generation</div>
<div class="pubdate">2012-03-26</div>
<div class="lastmodifdate">2016-07-06</div>

<a class="illustration" href="//en.wikipedia.org/wiki/Normal_distribution">
    <img src="/cdn/img/normal-distribution.png" title="Bell-shaped function" />
</a>

My [1K Minecraft](//js1k.com/1282 "Mine[love]craft") needed a good terrain generator, so I searched for javascript implementations of random noise generators. There are [pretty cool things](//gist.github.com/304522 "Perlin noise generators in javascript") out there but it was clear I would have to lower my mathematical ambitions to fit the algorithm in less than 1K of javascript. So I kept randomly dumping  [bell-shaped functions](//en.wikipedia.org/wiki/Normal_distribution "Normal distribution") on a flat base, which gives pretty satisfying results. I tried various functions (exp(-x²), 1/(1+x²), cos((π/2) * x²/(1/4+x²)), etc.). I finally used the exponential, as it seemed a good compromise between simplicity and speed.

<a class="illustration" href="//en.wikipedia.org/wiki/Simulacron-3">
    <img src="/cdn/img/13th-floor.jpg" title="Douglas Hall reaches the limits of his virtual world in Daniel F. Galouye's Simulacron-3 Hollywood adaptation (The Thirteenth floor)" />
</a>

So I had my N*N table of altitudes. Negative figures represent different depth of water, 0 is the sea level (sand), and positive are emerged lands, with snow appearing above a certain threshold. To compensate an inherent problem of visibility in the isometric projection, I gave the possibility to rotate the view by +90° steps, thus facing alternatively N-E, W-N, S-W, E-S, and back to N-E. And to avoid the disturbing ["world's end effect"](//en.wikipedia.org/wiki/Simulacron-3 "Simulacron-3"), I made the terrain "infinite" by cycling it in all directions, which may be considered superfluous since memory is not the real problem here. When digging, the altitude value for the current cell is decreased.

<a class="illustration" href="demo">
    <img src="/cdn/img/temple-of-love.png" title="&quot;Temple of Love on mount Eldritch&quot;: a snapshot showcasing the demo's day/night cycling and building features" />
</a>

The possibilty to add blocks was a non-negociable feature. So I turned each cell of the table into an array, the first value being the altitude, and the others representing a stack of the incremental altitudes of blocks put on this location. So pushing 1 onto this stack adds a block, popping the stack removes the top block, and incrementing the top value lifts the top block, which allows to have more complex buildings than just piles of stone blocks.
