+++
title = "Norton curves in p5.js"
date = "2020-03-26"
author = "Natalí"
authorTwitter = "Envido3" #do not include @
cover = "img/curvas-norton-starr/norton.png"
tags = ["p5", "processing", "Norton Starr", "creative coding", "geometria", "creations", "javascript"]
keywords = ["p5", "Norton Starr", "processing", "creations"]
description = "Using Norton Starr's family of curves to generate fun shapes with p5.js"
showFullContent = false
isMath = true
+++

In a previous proyect, I was playing with Maurer roses, and while searching for info in Wolfram MathWorld, saw in the recomended section [another cool figure](https://mathworld.wolfram.com/StarrRose.html), but there's no equations.  


<!-- {{< image src="https://mathworld.wolfram.com/images/eps-gif/StarrRose_1000.gif" alt="rosas Starr" position="center" style="background-color:rgb(200,200,200); max-width:350px; border-radius: 2px;" >}} -->

Googling Starr Rose, I couldn't find as much info as Maurer roses, only as an exercise to draw in calculus and geometry books.

## Equations

*Let a, b, c*

$$ 0 \leq t \leq 2\pi$$

$$x=(2+ \frac{1}{2} \sin at) \cos ( t + \frac {\sin bt}{c})$$

$$y=(2+ \frac{1}{2} \sin at) \sin ( t + \frac {\sin bt}{c})$$

So these are [polar coordinates](https://en.wikipedia.org/wiki/Polar_coordinate_system)!!! The radius and angle would be

$$ r = 2 + \frac{1}{2} \sin at$$
$$ \theta = t + \frac{\sin bt}{c} $$

We can write these in p5 

## p5.js code

```javascript
  // sketch.js inside function(draw)
  const a = 9
  const b = 16
  const c = 4
  const amp = 120
  beginShape()
  strokeWeight(2);
  for (let i = 0; i <= TWO_PI + 0.001  ; i+=0.001) {
    let theta = i + (sin(b * i) / c)
    let r = amp * ( 2 + 0.5 * sin( a * i))
    let x = r * cos(theta);
    let y = r * sin(theta);
    vertex(x,y)  
  }
  endShape();
```

Generates this figure

{{< image src="/img/curvas-norton-starr/norton-example1.png" alt="test 1" position="center" style="max-width:400px; padding-bottom:1rem" >}}

* *amp* is variable that amplifies the drawing, otherwise we could only see something that looks like a single point.
* With *i* I define the distance between the points, so in the loop I go from 0 to TWO_PI plus the interval between points

I don know about you, but this shape already makes my **gears activate** 🤖 

Inside *Beginshape* we can add lines that point to the center

```javascript
  // sketch.js dentro de function(draw)
  for (let i = 0; i <= TWO_PI ; i+=0.009) {
    let theta = i + (sin(b * i) / c)
    let r = amp * ( 2 + 0.5 * sin( a * i))
    let x = r * cos(theta);
    let y = r * sin(theta);
    vertex(x,y)
    line(x*0.2, y * 0.2, x, y) 
  }
```
That generates

{{< image src="/img/curvas-norton-starr/norton-example2.png" alt="test 1" position="center" style="max-width:400px" >}}

You can play a lot changing a, b and c, and because the sinodal behavior, it's kind of difficult to predict the final shape; with every test I was surprised by the final shapes! ✨


  {{< image src="/img/curvas-norton-starr/norton-ex4.png" style="max-width:250px; display:inline-block; padding:1rem" >}}
  {{< image src="/img/curvas-norton-starr/norton-ex3.png" style="max-width:250px; display:inline-block ; padding:1rem" >}}
  {{< image src="/img/curvas-norton-starr/norton-ex5.png"  style="max-width:250px; display:inline-block ; padding:1rem">}} 
  {{< image src="/img/curvas-norton-starr/norton-ex6.png"  style="max-width:250px; display:inline-block ; padding:1rem">}} 
  {{< image src="/img/curvas-norton-starr/norton-ex7.png"  style="max-width:250px; display:inline-block ; padding:1rem">}} 
  {{< image src="/img/curvas-norton-starr/norton-ex8.png"  style="max-width:250px; display:inline-block ; padding:1rem">}} 

I hope you play with the code, if you created something cute and / or bizarre [I want to see it!](https://twitter.com/Envido3) 🤩
