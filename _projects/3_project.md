---
layout: page
title: Dual Player Tetrix
description: A dual player Tetrix Cosole !
img: assets/img/3.jpg
# redirect: https://unsplash.com
importance: 3
category: work
---

Components of the project:
    ---
    controller
    front-end and back-end of Tetris
    background music
    ---

Design of the controller:
    ---
    2-axis joystick:
        upward: rotate clockwise
        downward: slow drop
    blue: rotate clockwise
    red: rotate anticlockwise
    black: hard drop
    yellow: hold
    ---

Design of the Front end:
    ---
    Since the refesh rate of the monitor is not very high,
    only the moving object is updated in each loop,
    this gives a much faster response time.
    ---

Design of the timer:
    ---
    set up an interrupt of 1ms delay,
    this interrupt act as the clock of the whole system,
    which allow us to regulate the game and music.
    ---

Design of the music generation:
    ---
    calculate the required frequency of each note,
    store the pre-scaler into a matrix,
    generate a sine wave to DAC analog output,
    connect to a speaker
    ---

Design of multi-player mode:
    ---
    By using USART protocol, we created a non-blocking, 
    asynchronous communication channel between the 2 machines,
    each player then send and receive messages by simply reading 8 bit,
    this is super fast and convenient to implement and use ! 
    ---

Gallery:
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/tetrix/tetrisnotes.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/tetrix/controller.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/tetrix/frontend.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    components
</div>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tetrix/icon.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    multiplayer!
</div>

You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, *bled* for your project, and then... you reveal its glory in the next row of images.


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>


The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}
```html
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
```
{% endraw %}
