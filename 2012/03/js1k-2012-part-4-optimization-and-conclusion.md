<div class="series">JS1k 2012</div>
<div class="title">Part 4 : optimization & conclusion</div>
<div class="pubdate">2012-03-29</div>
<div class="lastmodifdate">2016-07-06</div>

<a class="illustration" href="http://www.imdb.com/title/tt0088286">
    <img src="http://ehouais.net/blog/wp-content/uploads/2012/03/Top_Secret-150x150.png" title="&quot;Compressed&quot; Omar Sharif in &quot;Top Secret!&quot;"/>
</a>

At first, I tried to optimize code while adding functionalities to it. There were all kind of tricks and the code soon became a real mess, responding quasi-chaotically to modifications. I had started exploring "JS crushing", converting sequences of code into strings, then applying [entropic compression](http://en.wikipedia.org/wiki/Data_compression#Lossless "Lossless compression") to them, before expanding and evaluating them at run-time. But many had done this before, and I soon used [Aivo Paas](http://twitter.com/aivopaas "Aivo Paas")' crusher, which happens to be [another entry](http://js1k.com/1127 "Aivo Paas' JS crusher") to the 2012 JS1k. I didn't have time to benchmark the crushers, so I stuck to this one, and I'm pretty sure it does a very good job. I realized almost too late that such crushers are not harmless if you apply them directly on your source code: this produced numerous syntax errors 1h before deadline (due to not-so-optional semicolons), and a stressful debugging frenzy.

<a class="illustration" href="http://knowyourmeme.com/memes/wat">
    <img src="http://i3.kym-cdn.com/photos/images/newsfeed/000/173/575/25810.jpg" title="The WAT meme illustrated by Florentijn Hofman's giant Rubber Duck" />
</a>

So JS crushing allowed me to work on readable code, but I still had to work on 3 different kinds of optimization:
  - **Soul**: find the optimal paradigms for your own little universe. This requires imagination, rigorous maths, attention to details, sometimes a sharp sense of humour (a mix which can be [so f*ing close to genious](http://www.xkcd.com "XKCD")), and in my opinion represents the real value of it all.
  - **Language**: exploit javascript specificities (not to say [oddities](https://www.destroyallsoftware.com/talks/wat "WAT")), by using implicit casting, optional arguments, global variables, ~~`with` statement~~ (nope: it's incredibly slow, it's redundant with entropic optimization, and above all it's [bad](http://www.imdb.com/title/tt0087332/quotes?qt0475898 "Total protonic reversal")), bitwise operators, etc.
  - **Entropy**: "please the crusher" in every possible way (and this includes very nasty ways), by refactoring code to induce redundant patterns (rename variables, add unused arguments to duplicate function signature, etc.). This sometimes paradoxically requires you to bloat your code.

<a class="illustration" href="/2013/04/js1k-2013-part-1-introduction">
    <img src="http://ehouais.net/blog/wp-content/uploads/2012/03/js1k-2013-150x150.png" title="See you in JS1k 2013 !" />
</a>

I realize there are many things I didn't explain (ephemeris calculation, lightness management, isometric projection specificities, hue optimization, etc.). Let's say we'll keep some mystery here, but if you want to know, just ask. And surely there are also many ways to improve the demo, while staying below the 1K limit. And may be I should start thinking about my entry for next year's JS1k (what about Angry Birds 1K ?).

But for now it's spring in the northern hemisphere, and I must cultivate my garden.
