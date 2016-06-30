# JS1k 2012 (part 2) : Terrain generation

<section>

![Bell-shaped function](http://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Normal_Distribution_PDF.svg/350px-Normal_Distribution_PDF.svg.png "Bell-shaped function")

My [1K Minecraft](http://js1k.com/1282 "Mine[love]craft") needed a good terrain generator, so I searched for javascript implementations of random noise generators. There are [pretty cool things](https://gist.github.com/304522 "Perlin noise generators in javascript") out there but it was clear I would have to lower my mathematical ambitions to fit the algorithm in less than 1K of javascript. So I kept randomly dumping  [bell-shaped functions](http://en.wikipedia.org/wiki/Normal_distribution "Normal distribution") on a flat base, which gives pretty satisfying results. I tried various functions (exp(-x²), 1/(1+x²), cos((π/2) * x²/(1/4+x²)), etc.). I finally used the exponential, as it seemed a good compromise between simplicity and speed.

</section>

<section>

![The Thirteenth Floor](http://mimg.ugo.com/201005/44684/13thfloor.jpg "The Thirteenth Floor")

So I had my N*N table of altitudes. Negative figures represent different depth of water, 0 is the sea level (sand), and positive are emerged lands, with snow appearing above a certain threshold. To compensate an inherent problem of visibility in the isometric projection, I gave the possibility to rotate the view by +90° steps, thus facing alternatively N-E, W-N, S-W, E-S, and back to N-E. And to avoid the disturbing ["world's end effect"](http://en.wikipedia.org/wiki/Simulacron-3 "Simulacron-3"), I made the terrain "infinite" by cycling it in all directions, which may be considered superfluous since memory is not the real problem here. When digging, the altitude value for the current cell is decreased.

</section>

<section>

![Temple of Love on Mount Eldritch](http://ehouais.net/blog/wp-content/uploads/2012/03/temple-150x150.png "Temple of Love on Mount Eldritch")

The possibilty to add blocks was a non-negociable feature. So I turned each cell of the table into an array, the first value being the altitude, and the others representing a stack of the incremental altitudes of blocks put on this location. So pushing 1 onto this stack adds a block, popping the stack removes the top block, and incrementing the top value lifts the top block, which allows to have more complex buildings than just piles of stone blocks.

</section>
