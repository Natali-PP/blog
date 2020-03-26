+++
title = "Curvas de Norton Starr en p5.js"
date = "2020-03-26"
author = "Natalí"
authorTwitter = "Envido3" #do not include @
cover = "img/curvas-norton-starr/norton.png"
tags = ["p5", "processing", "Norton Starr", "creative coding", "geometria", "creations", "javascript"]
keywords = ["p5", "Norton Starr", "processing", "creations"]
description = "Usando la familia de curvas de Norton Starr para generar formitas en p5.js"
showFullContent = false
isMath = true
+++

En un proyecto anterior estuve jugando con las rosas de Maurer, y buscando información en Wolfram MathWorld, vi en los relacionados [otra figura que se parecían](https://mathworld.wolfram.com/StarrRose.html), pero no estaban las ecuaciones.

<!-- {{< image src="https://mathworld.wolfram.com/images/eps-gif/StarrRose_1000.gif" alt="rosas Starr" position="center" style="background-color:rgb(200,200,200); max-width:350px; border-radius: 2px;" >}} -->

Buscando Starr Rose, no encontré tanta información como con las rosas de Maurer, sólo las encontre como ejercicio para dibujar en libros de cálculo matemático.

## Ecuaciones

*Sean a, b, c*

$$ 0 \leq t \leq 2\pi$$

$$x=(2+ \frac{1}{2} \sin at) \cos ( t + \frac {\sin bt}{c})$$

$$y=(2+ \frac{1}{2} \sin at) \sin ( t + \frac {\sin bt}{c})$$

Es decir, son [cordenadas polares](https://es.wikipedia.org/wiki/Coordenadas_polares)!!! El radio y angulo serían

$$ r = 2 + \frac{1}{2} \sin at$$
$$ \theta = t + \frac{\sin bt}{c} $$

Podemos transcribirlas a p5 así

## Código p5.js

```javascript
  // sketch.js dentro de function(draw)
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

Genera la siguiente figura

{{< image src="https://natali-pp.github.io/blog/img/curvas-norton-starr/norton-example1.png" alt="test 1" position="center" style="max-width:400px; padding-bottom:1rem" >}}

* *amp* es una variable para ampliar el dibujo y poder verlo, sino se ve un puñado de puntos que parece un sólo punto. 
* Con *i* voy definiendo la distancia entre los puntos, por eso en el loop voy de 0 a TWO_PI más el intervalo entre puntos 

No se ustedes, pero a mi esto ya me **empiezo a activar** 🤖 

Dentro de *Beginshape* podemos agregarle líneas que apunten al centro

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
Que genera

{{< image src="https://natali-pp.github.io/blog/img/curvas-norton-starr/norton-example2.png" alt="test 1" position="center" style="max-width:400px" >}}

Podés jugar mucho variando a, b y c, y por el comportamiento senoidal, es medio difícil de precedir la forma final; en cada prueba me sorprendían las figuras qu resultaban! ✨


  {{< image src="https://natali-pp.github.io/blog/img/curvas-norton-starr/norton-ex4.png" style="max-width:250px; display:inline-block; padding:1rem" >}}
  {{< image src="https://natali-pp.github.io/blog/img/curvas-norton-starr/norton-ex3.png" style="max-width:250px; display:inline-block ; padding:1rem" >}}
  {{< image src="https://natali-pp.github.io/blog/img/curvas-norton-starr/norton-ex5.png"  style="max-width:250px; display:inline-block ; padding:1rem">}} 
  {{< image src="https://natali-pp.github.io/blog/img/curvas-norton-starr/norton-ex6.png"  style="max-width:250px; display:inline-block ; padding:1rem">}} 
  {{< image src="https://natali-pp.github.io/blog/img/curvas-norton-starr/norton-ex7.png"  style="max-width:250px; display:inline-block ; padding:1rem">}} 
  {{< image src="https://natali-pp.github.io/blog/img/curvas-norton-starr/norton-ex8.png"  style="max-width:250px; display:inline-block ; padding:1rem">}} 

Espero que juegues con el código y los valores, si creaste algo lindo y/o bizarro [lo quiero ver!](https://twitter.com/Envido3) 🤩
