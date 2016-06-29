# JS1k 2012 (part 3) : time, colours & light

<section>

![Trigonometric functions](http://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Sine_cosine_one_period.svg/300px-Sine_cosine_one_period.svg.png "Trigonometric functions")

I needed to pour some life into this world, so I defined a global variable to keep track of passing time, and used [trigonometric functions](https://en.wikipedia.org/wiki/Trigonometric_functions "Trigonometric functions") to determine whether it was night or day, the position of the sun/moon in the sky, and the intensity of daylight. I also used them to add swell waves (which add a lot to realism, but nearly made me miss the deadline...). All of this had to mix with player orientation, to keep things realistic : sun and moon always rise in the east and set in the west, and the swell is always southbound. I also had gently drifting clouds at some point, but the benefit/cost ratio was a little too low.

</section>

<section>

![HSL cylinder](http://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/HSL_color_solid_cylinder_alpha_lowgamma.png/197px-HSL_color_solid_cylinder_alpha_lowgamma.png "HSL cylinder")

At first I used '#rgb' color codes in canvas `fillStyle`, as it seemed really compact, but I soon changed to 'rgb(r,g,b)', as it allowed easier processing of separate components without having to convert the result to hexa. I reencoded the colors I used on fewer bits (2 for each component), thus referring for instance to bright red as 110000=48 or dark grey as 010101=21. It also allowed easier light adjustment. But it was not the way to go, and the obvious solution later came to my mind. RGB was used historically because it represents the way the real pixels (on the screen) work, but  from the application perspective, it makes far more sense to use [HSL](http://en.wikipedia.org/wiki/HSL_and_HSV "HSL/HSV color schemes") (hue, saturation, lightness) description, and luckily the CSS3 'hsl(h,s,l)' color scheme is now widely implemented in canvas. So at this point I could designate a color with minimum information : a small float (0 to 9) to define hue (times 20), an optional flag when the saturation is not 100% (for grey scale), and apply fine light filtering on the L component. Later I added specular information, and improved the rendering, but only after the deadline had passed.

</section>

<section>

![Midnight bath in the Baltic sea](http://ehouais.net/blog/wp-content/uploads/2012/03/baltic-150x150.png "Midnight bath in the Baltic sea")

It was fine to have dark nights, as long as the player could see his immediate surroundings. So I added torch-like dynamic lighting with the help of my buddy function exp(-x²). Nothing complicated here since it played nicely with the L in HSL. But I also wanted to have reflection of the sun/moon upon the water, and that proved a bit trickier, with the result that the second and final delivered version is far from satisfactory to me, and even a little buggy. The solution mixes trigonometry, viewer orientation, and the ubiquitous "bell" function. Once again, I fixed it and got something satisfactory, but only after the deadline had passed.

</section>
