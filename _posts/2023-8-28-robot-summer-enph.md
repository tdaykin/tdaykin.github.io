---
layout: post
title: ROBOT SUMMER
categories: [ENPH, SUMMER, ROBOT]
header_image: /assets/image/tmoneyZoomZoomy.gif
---
ROBOTS WERE MADE... 

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
  
  Construction + Redesign + Maybe a whole new idea
  
</details>

<details>
  <summary>Final Build</summary>
  
  Final Build
  
</details>

Conclusion/what we learned... work in progress
UBC EngPhys Robot Summer 2023
