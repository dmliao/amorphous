---
layout: post
title: Perlin Terrain
---

_Originally, this post was a series of links compiled in May 2015. However, as some of the links are no longer available, it was expanded into a full blog post in July 2016. I've kept the original date, since that was when I actually did all this work._

I found some success using Perlin noise to create realistic-looking terrain for natural worlds in JS. It does not do any physics or any other realistic simulation, nor does it account for natural effects, but I think it looks fairly decent.

This is what the results look like, generated as a heightmap in black and white:

![](/img/blog/perlin-terrain/image01.png)

# Heightmap Generation

The heightmap was generated from creating Perlin noise, which is then perturbed, eroded, and smoothed to create the final terrain. The original method was documented at http://www.float4x4.net/index.php/2010/06/generating-realistic-and-playable-terrain-height-maps/, but the link is no longer active.

Breaking it down into more detail:

## Perlin Noise

The first step is to create 2D perlin noise to form the base of the heightmap. I used [this code](https://gist.github.com/banksean/304522) as my Perlin noise generator, and the result looks like this:

![](/img/blog/perlin-terrain/perlin.png)

It's entirely okay to stop there and use that as the heightmap, in which case you'll get a series of very gradual hills. I was looking for something a bit rougher and more varied, so there were a few additional steps afterwards.

## Perturbing the Noise

To create imperfections and turbulence in the noise, the image from before was perturbed by using additional layers of 2D Perlin noise to modify XY coordinates of the input pixels.

The original method is cited from [here](http://members.gamedev.net/vertexnormal/turbulence_tutorial.html), which I sincerely hope does not go offline. In the case it does, I've quoted the explanation below:

---

> I iterated through the original image on X and Y coordinates, then used noise from the 2 layers of Perlin noise to perturb or modify these X and Y coordinates, extract the image pixel from the original buffer at the perturbed coordinate locations, and set that as the pixel for the final image.

> Here is the technique in simple pseudo-code:

    for x=0 to ImageWidth step 1
      for y=0 to ImageHeight step 1
       noisex = PerlinNoiseMap1[x][y]
       noisey = PerlinNoiseMap2[x][y]
       
       // Perturb our coordinates
       px = x + noisex*turbulence
       py = y + noisey*turbulence

       MapOut[x][y] = MapIn[px][py]
      endfor
    endfor

> In the above pseudo-code, we assume the existence of 2 distinct noise maps, one to modify X and one to modify Y. turbulence is simply a factor used to specify the strength of the turbulence; the higher it is, the more the noise map will perturb the coordinates, and the greater the turbulence will be.

---

The results are as follows:

![](/img/blog/perlin-terrain/perturbed.png)   

## Erosion

Perturbing the terrain creates much more variety, but also made the terrain very irregular for my purposes. Thre are very few flat surfaces, and hills and peaks became very thin. Simulating a little erosion can help make the terrain look more realistic, or at least more playable.

Generally, erosion is the process by which soil from cliffs is loosened and eroded to become hills, usually from running water or melting ice. In image terms, erosion reduces the height difference between two neighboring pixels, where height difference is the lightness of a greyscale pixel.

To perform this erosion, each pixel is iterated through and eroded if the height difference between it and its neighbors are within a range `T`. This encourages the creation of flatter surfaces, as smaller hills will be eroded away, but also preserves sharp cliffs (since the height difference will exceed the range `T`). After the erosion step, the image also went through a smooth filter to even out some of the smaller hills, and the erosion step iterated multiple times to achieve the final result:

![](/img/blog/perlin-terrain/eroded.png)

# Final Thoughts

The terrain was created in THREE.JS by using the resulting image as a heightmap for a plane; the plane had a vertex corresponding to each pixel of the heightmap, whose Y value was set based on the red channel of that pixel. (G and B could also be used interchangeably, since this is a greyscale image.)

The end result in THREE.JS looked like this:

![](/img/blog/perlin-terrain/final.png)

This image has some extras, such as the tree models, floating berries, and water plane, but shows off how the terrain looks.

Is this the best method out there? Probably not. A lot of design decisions are arbitrary, and not at all based on realism. It plays fairly nicely though, and the heightmap looks reasonable, so I consider it useful on those terms alone.