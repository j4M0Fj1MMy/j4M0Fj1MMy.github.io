---
layout: page
title: Gesture-To-Speech Gloves
description: A Smart gloves that translate sign language into voice.
img: assets/img/gloves/signal.png
importance: 2
category: project
---

{% include video.html path="https://cse.hkust.edu.hk/ug/fyp/posters/gallery/2022-2023/107_CSB2_Media.mp4" class="img-fluid rounded z-depth-1" controls=true %}

**Convolutional Neural Network with IMU-based Gesture-to-Speech Gloves**
[The academic paper is available here](/assets/pdf/fyp_finalreport.pdf)

- **Operating System:** Linux, Android
- **Development Environment:** Tensorflow, Numpy
- **Language:** Python, shell script
- **Database:** Flat folder containing csv data files

This project, which was my final year project in college, focused on utilizing a convolutional neural network in conjunction with IMU-based gesture-to-speech gloves for sign language classification. The gloves consisted of five sensors and a Raspberry Pi. We utilized Python, along with the TensorFlow and NumPy libraries, for coding on the Linux server and gloves. Additionally, I wrote shell scripts for hardware control, such as managing Bluetooth and sensors. We also developed a control panel
app using Flutter. Throughout the project, we experimented with various machine learning algorithms, including LSTM, RNN, and KNN, but ultimately chose a simple 1-D convolutional network due to its superior speed.


### **Introduction**
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

### **Multiplexing an I2C bus**
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

### **Segmentation of a sequence of gestures**
To break a sequence of gestures into separate gestures for our model to handle one by one, we 
applied a sliding window algorithm. Inside each window, the variance of each column of data 
is calculated. Then we produced a score based on the variance of the gyroscope columns and 
the variance of the accelerometer columns. If each of the scores is significantly below its 
neighbors, we define the window as a breakpoint of gestures. This is because, between each 
gesture, we observed that there tends to be a temporary pause. If the window contains a pause, 
the variance will be significantly lower. This idea comes from the skill of NLP. Below is an 
example of the figure of the sensor values of one finger with a red box indicating a 
breakpoint.

Gallery:

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/gloves/signal.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/gloves/gloves.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    signal of an accelerometer on the gloves, a picture of the prototype
</div>

