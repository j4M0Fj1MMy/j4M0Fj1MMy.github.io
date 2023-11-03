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
        {% include figure.html path="assets/img/tetrix/tetrisnotes.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tetrix/controller.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tetrix/frontend.png" title="example image" class="img-fluid rounded z-depth-1" %}
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


**Watch a presentation [here](https://drive.google.com/file/d/1a-XYjCfz_WJGprS4lfjAZl6kcqQxQYRz/view?usp=sharing)**