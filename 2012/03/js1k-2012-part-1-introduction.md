<div class="series">JS1k 2012</div>
<div class="title">Part 1 : introduction</div>
<div class="pubdate">2012-03-25</div>
<div class="lastmodifdate">2016-07-06</div>

<a class="illustration" href="http://js1k.com">
    <img src="http://js1k.com/img/js1k.png" title="JS1k" />
</a>

This is the first post of a series about [my contribution](http://js1k.com/1282 "1K Minecraft") to the [2012 JS1k contest](http://js1k.com/2012-love "js1k 2012") ([annotated source](https://github.com/ehouais/js1k "ehouais/js1k")). I put some work into it, and since there were some appreciative comments [here](http://www.europapress.es/portaltic/videojuegos/noticia-crean-clon-minecraft-solo-pesa-kilobyte-20120322083005.html "Crean un clon de Minecraft que solo pesa 1 kilobyte") and [there](http://www.faseextra.com/pc/minecraft-minimalista "Minecraft minimalista"), I feel the need to keep track of what I've done here and give some implementation details.

About the "Mine[love]craft" name: this was a feeble pun trying to mix [this](http://www.minecraft.net "Minecraft") and [that](http://en.wikipedia.org/wiki/H._P._Lovecraft "H.P. Lovecraft"). I now would rather choose "Mine1Kraft", or "CraftyLove", whatever.

<a class="illustration" href="https://en.wikipedia.org/wiki/Oric">
    <img src="http://upload.wikimedia.org/wikipedia/commons/thumb/4/41/Oric_Atmos_01a.jpg/300px-Oric_Atmos_01a.jpg" title="Oric Atmos" />
</a>

I had no plan to participate in this contest, though I had already stumbled upon contributions to previous editions. The magic of hyperlinks brought me recently to the home page of the 2012 edition, and this time it clicked. There were still a few weeks left before the end of submissions, and I couldn't resist the challenge. I find javascript both fun and powerful, and the 1K constraint reminded me of the programs I created on my [Oric Atmos](http://en.wikipedia.org/wiki/Oric_series_of_computers#Oric_Atmos "Oric Atmos") back in the days (yeah I'm that old, but at least I know why [this](http://cheezburger.com/4443671040 "Hammerzeit") is funny). So I decided to give it a try, and began to look for ideas.

<a class="illustration" href="https://en.wikipedia.org/wiki/Zaxxon">
    <img src="http://upload.wikimedia.org/wikipedia/en/thumb/4/45/Zaxxon.png/220px-Zaxxon.png" title="Zaxxon" />
</a>

My first idea was to implement a remake of the old [Zaxxon](http://en.wikipedia.org/wiki/Zaxxon "Zaxxon") game. I don't remember how this idea came to me, but it seemed pertinent since the isometric projection is both a satisfying 3D simulation and easy to compute. My first prototype was going well, and I began to work on a randomly generated terrain, to diminish the cost of storing it into the 1K. But the algorithm result looked more like a real landscape, and with a few modifications, I had snow, grassy slopes and stretches of water. I'm a big fan of [Notch](http://notch.tumblr.com "Notch"), I have Minecraft on my Mac, though I don't play it much since the 3D gives me nausea in 5 minutes (am I the only one ?), so it was not long before I decided to work on a minimalist version of this simple, yet incredibly addictive game.
