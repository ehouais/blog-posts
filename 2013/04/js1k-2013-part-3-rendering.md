<div class="series">JS1k 2013</div>
<div class="title">Part 3 : rendering</div>
<div class="pubdate">2013-04-21</div>
<div class="lastmodifdate">2016-07-06</div>

We've seen in [the previous post](js1k-2013-part-2-tunnel-generation "Tunnel generation") that each iteration began by generating a new trunk of tunnel, so that there are always 1400 tunnel positions ahead available to render. The second phase of the algorithm is to render the elements that are present in some of these positions. One of the advantages of this pseudo 3D rendering is that processing layers from the farthest to the nearest solves the costly z-index problem: nearest elements automatically hide the distant ones. For each position containing elements to render, the algorithm applies simple perspective calculus using layer's horizontal and vertical shift (x and y at the layer's position), distance to the cart, and orientation of the cart (x' and y' at the cart's position). The simplicity of the rendering method allows using only 2 canvas primitives: fillRect and fillStyle, but still the latter is costly and is only used when the fill color really changes.

![Light coming from the cart](http://ehouais.net/blog/wp-content/uploads/2013/04/light1.png "Light coming from the cart")

When I began working on colors and light, I soon decided not to use colors but instead focus on light. Using a simplified hsl(0,0%,x%) syntax was saving bytes, and I was convinced that in this context, contrast was much more significant than color. I tested different lighting algorithms, and naturally the one where the light came from the cart seemed [the most realistic](http://www.youtube.com/watch?v=vx2o3AhLHrA "Minecart ride") to me. But the problem was that the nearest layers were overexposed and appeared in all their ugliness: the rendering technique was only acceptable if its consequences on nearest layers were softened by darkness and speed.

![Light coming from the background](http://ehouais.net/blog/wp-content/uploads/2013/04/light2.png "Light coming from the background")

So I inversed the formula, and it created a light coming from the end of the tunnel. It wasn't realistic at all (unless you're chasing another cart which is carrying a lamp), but it was nice to watch, simple to implement, and created a depth where closer elements were darker and contrasted nicely in front of brighter distant elements. To shorten color values, I encoded lightness on 3 bits, and used a fourth bit to differentiate blocks emitting light from those only reflecting it.

![Ambient and lightbulbs](http://ehouais.net/blog/wp-content/uploads/2013/04/light3.png "Ambient and lightbulbs")

When I abandoned the particle engine, I got a comfortable amount of bytes back, so I used them to enrich the lighting environment by adding bulbs to create local spots of light. This implied to generate two specific blocks (the bulb and the cord) twice in each flat section (at positions 200 and 600), and to provide to the rendering algorithm the amount of additional light for each position, computed at generation time by applying the swiss-knife bell function exp(-x<sup>2</sup>) to the distance to the nearest light. I added a fifth bit to lightness encoding to indicate blocks that should reflect light but that don't in certain cases (light from bulbs don't reflect on cave walls).

![Real mineshaft](http://ehouais.net/blog/wp-content/uploads/2013/04/mineshaft.jpg "Real mineshaft")

The result was really worth the bytes, and at last the rendering seemed pretty realistic to me. But now that the torches were gone, it lacked a bit of fancy in these mines, so I had the idea of making some lights flicker. It proved a bit costly, but in the end, I liked this so much that I didn't want to rollback. Technically, It needed two more values in the parameters generated at each position, one acting as an indicator being null only when changing of "light zone", the other indicating whether the bulb is defective, in this case triggering at each iteration a random draw deciding whether the light is on or off. When looping through the light zones, the rendering algorithm uses these indicators to modulate the light provided by the zone bulb.

In [the next and final part](../05/js1k-2013-part-4-conclusion "Conclusion") I will talk about the "strange crystals", the [Román Cortés challenge](http://js1k.com/1461 "Furbee in the mines"), and will wrap it all up.
