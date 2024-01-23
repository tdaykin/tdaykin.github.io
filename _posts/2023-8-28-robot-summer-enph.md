---
layout: post
title: AUTONOMOUS DRIVING ROBOT
categories: [ENPH, SUMMER, ROBOT]
header_image: /assets/image/tmoneyZoomZoomy.gif
thumbnail: /assets/image/lookinSexy.png
---
<style>
    /* Other styles remain unchanged */

    /* Adjust the top margin of the posts container to push it down */
    .posts {
        margin-top: 35px; /* Add more space at the top of the posts container */
        width: 100%; /* Full width of the parent container */
        position: relative;
        z-index: 3; /* Above the background section but below the navigation and header */
    }

    /* Rest of your styles */
</style>

<!--ROBOTS WERE MADE... -->

<!--more-->

**Practicing:**

- Project Management and Advanced Problem Solving
- Rapid Prototyping, Manufacturing (machine shop) and CAD
- Soldering, Electronics and PCB Design
- Troubleshooting (noise issues, signal integrity, software and hardware)

**Pictures:**

![lookinSexy]({{ site.baseurl }}/assets/image/lookinSexy.png)

**Some History and Outline:**

Over the 2023 Summer Term from July 4 to August 10, myself, Ebrahim Hussain, Amr Sherif, and Dhruv Arun came together in a team of 4 for the annual ENPH 253 robot competition. The final robot photos above represent all of our unique contributions and our less than straightforward path which led us to our final design. This post highlights our conceptual ideas, decisions, and the manufacturing of our robot. We concluded the term with a 2nd-place finish.

- The full race can be watched [here](https://www.youtube.com/live/gXMnazr8vEo?si=DzM_r1Ch8ZJGJhDZ).

**The Track:**

![253 Track 2023]({{ site.baseurl }}/assets/image/253track.png)

**Summary of Rules:**

- Heats are 2 minutes long.
- Robots score points by picking up prize blocks (labelled “Bonus”) on the track, coins (labelled “Coin”) on the zipline, or by completing a lap. Blocks and coins are worth 1 point each, while a lap is worth 3.
- Regardless of START(1) or START(2), a lap is counted when a robot completes the following in order:
  1. Crosses over the finish line.
  2. Goes up the ramp (blue, top right) and either jumps down on the left side of Rainbow Road or loops around to START(2).
  3. Travels under Rainbow Road from the left and crosses the finish line again.
- A magnetic “bomb” is placed on the track, which has the same footprint as a regular Bonus/prize block. Each robot is also allowed to drop one extra bomb on the track at any time throughout the heat.
  - Any robot that picks up a bomb or tips it on its side has “detonated” the bomb, and they must restart, and also lose -3 points from any existing block/coin points.

The rules and course webpage can be found [here](https://docs.google.com/document/d/e/2PACX-1vS4bQXNVCvEt-UMX50Rsar0Wds5AqRDQToN8ABxkS7ocnluPU8JlCNRYIkiXptbHYsrAI_WKzwC9IwO/pub).

<!--
**Late Night CAD Session**:

![Probably an Industry Standard]({{ site.baseurl }}/assets/image/lateNight.png)
-->

<style>
details {
    border: 1px solid #aaa;
    border-radius: 4px;
    padding: .5em .5em .5em 1.5em;
    margin-bottom: 1em;
}
summary {
    font-weight: bold;
    cursor: pointer;
}
details[open] {
    padding: .5em;
}
details[open] summary {
    border-bottom: 1px solid #aaa;
    margin-bottom: .5em;
}

  .centered-image {
    text-align: center; /* Center the content (image) inside the div */
    margin: 0 auto;     /* Ensures the div itself is centered if it has a width less than its container */
}

.centered-image img {
    width: 120%;   /* Increase the image size by 20% */
    margin: 0 auto; /* Ensures the image is centered */
    display: block; /* Makes the image a block element to accept the margin */
}

</style>

# TIMELINE:

<details>
  <summary>Brainstorming/Designing</summary>

  <strong>Brainstorming:</strong>
  <p>Teams were allowed to do almost anything they wanted, including jumping off the ramps, using the zipline, or traveling over the rocks to gain a shortcut to the finish line. However, before talking to each other as a team, we all decided that we would follow tape and dedicate our focus on trying to pick up blocks/avoid them passively.</p>
  
<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/steering253.png" alt="Ack vs Diff Steering">
</div>  

  <strong>Firstly, we needed to choose our steering system.</strong>
  <p>This is important as it will determine where many elements of the robot will go, such as motors, electronics, and our pickup mechanism. The two types of steering we considered were either Ackermann or Differential. Ackermann is familiar to us as we see it in cars, where the back wheels stay at a certain speed and the front wheels can turn. Whereas in differential steering, the back wheels turn at different speeds to turn (i.e., if the left wheel is spinning slower than the right, the robot will turn left).</p>

  <p>However, from our understanding and research, Ackermann steering, provided the right geometry and tuning can be much faster than differential steering. With this in mind, we chose differential, while every other team chose Ackermann. This fact definitely made us think about our choice, but those thoughts did not last for long, as we were certain our choice took into consideration that this whole competition was something new to us and we wanted a steering mechanism that we could easily deploy and redeploy. Another observation that pushed us towards this steering mechanism was that the course has some very sharp turns, which in differential steering are easier to control, in just software, rather than in Ackermann steering where you would need to consider the whole chassis layout in order to accomplish those turns.</p>

  <p>So initially with our constraints, we wanted to design a robot that looked something like this:</p>
  
<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/initialpresentation253.png" alt="Initial CAD pic 1">
</div> 

  <p>Where we drive around the track, the wings would fold inwards to collect a block and outward to avoid bombs like below:</p>
  
<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/initialpresentation2532.png" alt="Initial CAD pic 2">
  <img src="{{ site.baseurl }}/assets/image/initialpresentation2533.png" alt="Initial CAD pic 3">
  <img src="{{ site.baseurl }}/assets/image/initialpresentation2534.png" alt="Initial CAD pic 4">
</div> 

</details>

<details>
  <summary>Construction + Redesign + Maybe a whole new idea</summary>
  
<strong>Electronics:</strong>

<p>To start we built a simple line follower, something we could adjust later on. Ebi owned build the motor drivers, tape sensors and microcontroller boards.</p> 

<strong>1. H-Bridge Motor Drivers:</strong>

<p>The H-Bridge is a relatively simple circuit used to control the **polarity** of the voltage across a load, in our case, a motor. Alongside having control over the speed by PWM, the H-bridge gives us control over the motor’s rotation direction. This is especially important in differential-steering, where in some cases one wheel must spin backward and the other forward to complete a sharp turn. Here is a simple **dual H-bridge** schematic of the motor boards on the robot.</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/dual-hbridge.png" alt="dual-hbridge.png1">
</div> 

<p>Attached is a step through guide made by Ebi: <a href="/assets/image/H-Bridge Step-Through.pdf" download="H-Bridge Step-Through.pdf">H-Bridge Step-Through PDF</a>
</p>

<p>This resulted in:</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/H-bridge layout.jpeg" alt="H-bridge layout.jpeg">
  <img src="{{ site.baseurl }}/assets/image/H-bridge final.png" alt="H-bridge final.png">
  <img src="{{ site.baseurl }}/assets/image/initialpresentation2534.png" alt="Initial CAD pic 4">
</div>

<strong>2. Control Boards and Tape Following Sensors:</strong>
<p>Here’s the unpopulated Blue-Pill/microcontroller board, and the tape sensor board:</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/sc1.png" alt="Screenshot 2024-01-22 at 3.50.09 PM.png">
</div>

<p>BP Board PCB Layout:</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/sc2.png" alt="Screenshot 2024-01-22 at 3.51.03 PM.png">
</div>

<p>This is somewhat overkill and wasn’t really required in the end, but I designed this board pretty early on before any other sensor / peripheral decisions were made. So it just made sense to be safe and provide the possibility to house two microcontrollers. It has:</p>

<ul>
    <li>x3 SONAR ports</li>
    <li>x4 I2C ports (two of them tied together <em>if</em> the microcontrollers need to talk to each other)</li>
    <li>x6 AIO available for tape sensors</li>
    <li>x3 servo ports</li>
    <li>a UART port for serial monitor, power selection</li>
    <li>2 2-wide PWM ports for two H-Bridges</li>
    <li>voltage level selectors for I2C, Sonar, and Tape Sensors</li>
</ul>

<p>and leaves the remainder of the pins free for switches, LEDS, hall-sensors, and anything else.</p>

<p>For the tape-sensor board, Dhruv made the schematic and Ebi made the PCB layout and soldered it together. It uses surface-mount resistors which was needed since the tape sensors sit very low to the ground. Here’s a video of it on a servo mount which I made:</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/servermount.gif" alt="servermount.gif">
</div>

<strong>3. PID Algorithm:</strong>

<p>The PID is probably the simplest part of code of the entire robot, but I wanted to share how I thought about converting tape-sensor data to an error function.</p>

<p>Instead of computing each sensor value and referencing a lookup table, I decided to treat each sensor value as a **force** on a seesaw. Then, simply let the displacement be the net torque on it! Of course, if the robot is completely off the line, then just reference the magnitude of the previous displacement to know whether you are too left, or too right.</p>

<p>That’s basically what I’m doing here — writing it in code is much simpler than doing it mathematically though. The key part is the (∑S[n]N[n]∑S[n]∑S[n]∑S[n]N[n] - fix latex)​﻿ which is simply the average. N is the location of each sensor and S is the associated sensor values.</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/sc3.png" alt="Screenshot 2024-01-22 at 4.03.32 PM.png">
</div>

<p>You can find the <a href="https://www.desmos.com/calculator/4zlgnq8wji">Desmos here</a>, and play around with the ϕϕ﻿, which is the displacement of the sensor array off the line. The purple line represents the error function value, and the dots are the sensor locations</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/image/PIDs23.gif" alt="PIDs23.gif">
</div>

<p>One interesting way of doing it like this is it becomes convenient to introduce nonlinearities into the transfer function through the R[n] array. Ebi and I played around with this a little and found that a non-linear transfer function for differential steering can often result in smoother and more responsive driving than a linear one.</p>

<p>This makes intuitive sense for tape-following, because you don’t really care about minor deviations off the line, but once your tape sensors are close to leaving the line entirely, you now have a higher error to correct yourself quickly, or to take a sharp turn.</p>

<p>The final “non-traditional” part Ebi and I implemented was **filtering** the derivative of our error function, so that the PID equation is out = Kpe(t)+Ki∫e(t)+Kdlowpass(ddte(t))out=Kp​e(t)+Ki​∫e(t)+Kd​lowpass(dtd​e(t))﻿. To understand why, consider the following error function e(t), in red:</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/sc4.png" alt="Screenshot 2024-01-22 at 4.05.56 PM.png">
</div>

<p>This error function simply means the robot’s displacement off the line has changed. It looks like a step rather than a smooth change because these signals are being processed inside the microcontroller, in thee **discrete* time domain.</p>

<p>If we then compute the almost-discrete-derivative as error - prevErrorerror﻿, we’d get an impulse, as shown in blue. This isn’t that useful because it means the derivative term in the PID equation only lasts for one loop iteration, which is on the order of μμ﻿s — that’s not nearly enough time for it to do much useful work. A solution to this is to **low-pass filter (LPF)** the differentiated error signal, shown in green. In an electrical context, this green signal represents the discharging of a capacitor, but instead we’re doing it in software using a first-order IIR filter:</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/sc5.png" alt="Screenshot 2024-01-22 at 4.07.27 PM.png">
</div>

<p>Of course there are other ways to do this, and I guess you could choose any decaying function (maybe an average?). All that I’m trying to do is keep the effect of the derivative for longer, so that the KdKd​﻿ term comes into play.</p>

<p>The motivation to try something like this is somewhat arbitrary, but we gave it a shot and it had a **significant positive impact on the smoothness of the robot’s tape following at high speeds**.</p>

<strong>Final run:</strong>

<p>With all the basics sorted, we put the motors, H-bridges, microcontrollers, tape-sensors, and PID code together for the first prototype. Here you can see one of the populated BP boards as well.</p>

<p>I’m really proud of the pace we were able to do this at, since we were the first team to get on the track and tape follow in the first week of the course.</p>

<div class="centered-image">
  <img src="{{ site.baseurl }}/assets/topOfOG.jpeg" alt="topOfOG.jpeg">
    <img src="{{ site.baseurl }}/assets/finalrunOGgif.gif" alt="finalrunOGgif.gif">
</div>

<p>We fail on rainbow road since this was our first time testing, and the colors interfered with the tape sensor, but we all start somewhere!</p>

<strong>Block Pickup:</strong>
  
</details>

<details>
  <summary>Final Build</summary>
  
  Final Build
  
</details>

Conclusion/what we learned... work in progress
UBC EngPhys Robot Summer 2023
