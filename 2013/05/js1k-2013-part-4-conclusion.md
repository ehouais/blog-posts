<div class="series">JS1k 2013</div>
<div class="title">Part 4 : conclusion</div>
<div class="pubdate">2013-05-06</div>
<div class="lastmodifdate">2016-07-06</div>

<a class="illustration" href="">
    <img src="/cdn/img/strange-crystals-4.png" title="crystals"/>
</a>

I was pretty satisfied with the rendering and the atmosphere it created, but I also wanted to tell a story, to give a goal for this mine cart ride with the few remaining bytes. I had been impressed by [the Giant Crystal Cave](https://en.wikipedia.org/wiki/Giant_Crystal_Cave "Giant Crystal Cave"), so I worked on the concept, but finally settled on floating glowing crystals. Technically, the crystals were treated as special blocks (identified by their unique color value) whose coordinates are updated at each iteration according to a pseudo time variable and a simple trigonometric formula. They only appeared in caves (obviously), on low speed level to have time to watch them, and when railtrack is low enough to give a good angle of view. This way the demo seemed pretty consistent and aesthetic to me, and the presence of those strange crystals justified the absence of miners. So I published it a few days before the deadline.

<a class="illustration" href="//js1k.com/1451">
    <img src="/cdn/img/furbee.jpg" title="Furbee"/>
</a>

3 things happened next: Javier Román Cortés submitted [his amazing Furbee](//js1k.com/1451 "Furbee"), and our entries both went viral, pushing the JS1K site to the limits. Javier is really loving the challenge, so he quickly found a way to merge our 2 demos into [one](//js1k.com/1461 "Furbee in the mines"), by slightly downgrading his one while simulating the tunnels of mine (a technical tour de force), and challenged me to work my own mashup. In parallel, many comments showed that crystals and even caves were sometimes very long to show, which made me uneasy, even if I like demos that show their features progressively. And finally, an additional step in [code compression algorithm](//github.com/Siorki/RegPack/blob/master/regPack.html "Regpack") gave me a comfortable amounts of bytes to play with. So I had to do something, but I didn't want to depreciate my demo, given all the work I had put into it.

<a class="illustration" href="">
    <img src="/cdn/img/strange-crystals-5.png" title="trajectory"/>
</a>

On the morning of deadline sunday, I finally decided to give it a try. I tried to organize the crystals so that, from a certain point of view, they grouped in the shape of the furbee. It was difficult and the result wasn't satisfactory. I then decided to get rid of the crystals, which after all wasn't such a great loss since many didn't have the patience to see them, and use the bytes jackpot to add something really valuable. I reduced furbee to a glowing point (which this way looks more like Tinkerbell), gave it a triply trigonometric trajectory (x/y [Lissajous](//en.wikipedia.org/wiki/Lissajous_curve "Lissajous curve") + sinusoidal offset ahead of viewer), and added the corresponding light to the rendering algorithm. All furbees along the trajectory are created at generation time, but only the one relevant is displayed at render time, this specific behaviour being triggered once again by a unique color value. Then I published "[Strange Crystals II](//js1k.com/1555 "Strange Crystals II")" on the site, 15 minutes before deadline.

Comments show that some like the new version better while others find furbee too distracting. Anyway the JS1K judges ranked me #1, which I'm very proud of, given the quality of some other entries. I will probably participate in 2014's edition if there is one, but for now it's finally spring time in [Brittany](//en.wikipedia.org/wiki/Brittany "Brittany"), and I must cultivate my garden.
