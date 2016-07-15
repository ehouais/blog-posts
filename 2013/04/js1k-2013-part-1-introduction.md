<div class="series">JS1k 2013</div>
<div class="title">Part 1 : introduction</div>
<div class="pubdate">2013-04-13</div>
<div class="lastmodifdate">2016-07-06</div>

<a class="illustration" href="//en.wikipedia.org/wiki/White_Rabbit">
    <img src="//blog.gatewaydrumsmokers.com/wp-content/uploads/2015/06/mctwisp___the_white_rabbit_by_fallenangel1224-291x300.jpg" title="&quot;Oh dear! Oh dear! I shall be too late!&quot;"/>
</a>

Last year I stumbled upon <a title="JS1K" href="//js1k.com">the js1k contest </a>and it clicked at once. The combination of constraints and freedom, added to the fun and possibilities brought by javascript/canvas was a magic cocktail I couldn't resist. But since the competition had already started, I only had a few weeks to complete my entry, and though [my Mine[love]craft entry](//js1k.com/1282 "Mine[love]craft (js1k 2012)") was pretty satisfactory and ranked fourth, I was frustrated that many good ideas to improve it came to my mind too late. So this time I decided to start early, so that I could refactor my ideas/algorithms/functions as many times as necessary, while also having enough time to polish the details. Thus the first jsfiddle I wrote dates back to august 2012. However this did not protect me from the last minute syndrome, and my second version was <a title="Strange crystal II" href="//twitter.com/ehouais/status/318673499017338880">submitted</a> only a few minutes before the deadline.

<a class="illustration" href="//en.wikipedia.org/wiki/Clockwork_universe">
    <img src="//ehouais.net/blog/wp-content/uploads/2013/04/clockwork1-e1365863873450-150x150.jpg" title="Designing my own clockwork universe"/>
</a>

This time, my goal was to implement a watch-only demo, because handling user input is costly, and since the instructions are not visible by default on the demo page, one is never sure that the visitors (including the judges) are aware of the controls. Both the subject of the demo and the graphical rendering technique came progressively to my mind, after I started optimizing the rendering of randomly generated <a title="octree" href="//en.wikipedia.org/wiki/Octree">3D voxel octrees</a>. The idea of a mine cart simulation has nothing to do with last year's mini minecraft, even if Minecraft fans have designed <a title="Beetle Juice - A Minecraft Roller Coaster" href="//www.youtube.com/watch?v=afcudstM9zA">some incredible mine cart rides</a>. What they have in common though is that they both try to fit seemingly complex but consistent universes in a small space, with much importance given to details. This is almost obsessive, and I surely would have been a watch maker in other times.

<a class="illustration" href="//www.youtube.com/watch?v=8oaccb5NxOc">
    <img src="//ehouais.net/blog/wp-content/uploads/2013/04/templeofdoom-e1365854409491-150x150.jpg" title="Indiana Jones and the Temple of Doom"/>
</a>

The mine cart idea came with some heavy [cinematographic](//www.youtube.com/watch?v=pvmXmIHjQ2E "Temple of Doom") [references](//www.youtube.com/watch?v=z-o1cNXUzoE "Gringotts"), which increased the need to produce something as realistic as possible (update: there's also [a vintage game](//www.youtube.com/watch?v=GQd3FFT7pnc "Rail Chase") I didn't know which uses the same rendering technique). I browsed many of the genre's clichés, keeping some of them (rails, sleepers, stull pieces, turns, slopes, lightbulbs, wooden bridges, stala[ct|gm]ites <a title="stalactites or stalagmites ?" href="//www.goodreads.com/quotes/253813-i-never-know-harry-called-to-hagrid-over-the-noise">"what's the difference, Hagrid ?"</a>), while eliminating others (bats, lava, underground lakes, etc.). I had at some point a small particle engine that allowed me to show burning torches and water streams, but its cost was a bit high. To add some story telling to the demo while making use of the last available bytes, I added the eponymous crystals and a few teasing words in the description and the tweets. I like the idea that some aspects of the demo are only discovered if you wait long enough and Math.random() is kind to you, but it was a risky bet, and I'm convinced that many viewers did not wait to see the crystals fly. We'll see that a challenge from the excellent <a title="Román Cortés" href="//romancortes.com/">Román Cortés</a> (and <a title="RegPack" href="//github.com/Siorki/RegPack">some improvements in the compression tools</a>) brought me to improve this in my second and final version.

In [the next part](/2013/04/js1k-2013-part-2-tunnel-generation "tunnel generation"), I get technical and describe the tunnel generation algorithm.

Note: the annotated code is available [here](//github.com/ehouais/js1k).
