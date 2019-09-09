**University of Pennsylvania, CIS 565: GPU Programming and Architecture,
Project 1 - Flocking**

* Nicholas Magarino
  * [https://www.linkedin.com/in/nicholasmagarino/](), [https://www.nickmagarino.com/]()
* Tested on: Windows 10 Home Version 1803, i5-8300H @ 2.30GHz 8GB, GeForce GTX 1050 8GB (MSI GL63 8RC Laptop)

### READ-ME

![](/images/boidsGif.gif)

Boids are particles that follow three rules: cohesion, separation, and alignment, and check their neighboring boids to compute their velocity on the next frame of the simulation.

**Performance Analysis**

![](/images/visual.png)

![](/images/novisual.png)

For each implementation, increasing the number of boids generally decreases the framerate as more neighbor boid data accesses are done per boid.

![](/images/blocksize.png)

Increasing the CUDA kernels' block size generally improved performance, as doing so allows more threads to run in parallel on the GPU.

In all, the coherent grid had greater performance than any other implementation, as expected, as this method allowed the most data to be continguous in memory, thus decreasing the time needed to access the next piece of data.

Decreasing cell width reduces performance, as it adds more overall cells to check.  In general, more cells results in more memory access that may not be contiguous, reducing performance.

