---
layout: page
title: Gesture-To-Speech Gloves
description: A Smart gloves that translate sign language into voice.
img: assets/img/3.jpg
importance: 2
category: work
giscus_comments: true
---

Communication plays an important role in society, however, communicating with the 
hearing-impaired community could be hard because people seldom have exposure to sign 
language. This project will work on classifying a sequence of gestures from IMU devices, with a proposed extensible
system that could be managed with an application.  

This project is separated into 3 parts, namely the data fusing pipeline, the classifying model, 
and the application. The data fusing pipeline is responsible for denoising and sending the data 
to the application. Then, the classifying model will locate meaningful gestures and turn them 
into human language. The application hooks everything into a user interface, allowing the 
user to control the system.  

This page will share the most important and perhaps the funniest part in the project. But if you are interested in details, feel free to send an email for further discussion !  

### Multiplexing an I2C bus
As there is only one I2C bus in raspberry pi zero, we did multiplexing ourselves to read from 
5 sensors consecutively. We connected all 5 sensors in parallel and connected the circuit to 
the I2C bus. In each loop, we output a HIGH voltage with a GPIO pin from the RSP to the 
AD0 pin in MPU6050. This switched the address of the AD0 pin from 0x69 to 0x68, in other 
words, ‘woke’ the sensor ‘up’. The data of that particular chip was output to the I2C channel 
to be further processed. In our implementation, the sampling rate of the data is approximately 
40Hz which is high enough to display details of each gesture.  

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gloves/multiplex.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    showcasing the multiplexing connection
</div>

### Segmentation of a sequence of gestures
To break a sequence of gestures into separate gestures for our model to handle one by one, we 
applied a sliding window algorithm. Inside each window, the variance of each column of data 
is calculated. Then we produced a score based on the variance of the gyroscope columns and 
the variance of the accelerometer columns. If each of the scores is significantly below its 
neighbors, we define the window as a breakpoint of gestures. This is because, between each 
gesture, we observed that there tends to be a temporary pause. If the window contains a pause, 
the variance will be significantly lower. This idea comes from the skill of NLP. Below is an 
example of the figure of the sensor values of one finger with a red box indicating a 
breakpoint.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gloves/signal.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    signal of an accelerometer on the gloves
</div>

To give your project a background in the portfolio page, just add the img tag to the front matter like so:

    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    ---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
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
