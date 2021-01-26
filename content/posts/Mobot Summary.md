---
title: "Mobot Summary"
date: 2021-01-01T21:18:31-06:00
tags: ["Freshman Year", "Fundamentals of Mechanical Engineering"]
draft: false
---


![Mobot](static/imgs/Mobot1.jpeg)

The third project we completed for my freshman introductory mechanical engineering course was a line following robot. Modelled after the Mobot races that are traditionally part of CMU's "Carnival" (https://www.cs.cmu.edu/mobot/).

The playlist below contains some of the tests while developing the controls for the bot. The objective was to complete the about 7 ft track autonomously and stop 15cm from the box at the end. We managed to do both, completing the task in the fastest recorded time of about 7 seconds. We built the chassis as a team from a kit and I wrote the code for the controls and line detection using a standard PID controller.

{{< raw >}}
<iframe width="1000" height="700" src="https://www.youtube.com/embed/osZakGMkFQ4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
{{</ raw >}}

First Successful Test

{{< raw >}}
<iframe width="1000" height="700" src="https://www.youtube.com/embed/Lt6a51pSibA?list=PLHdvgIthuYahr6zz2Gn5ZU_BojIdQtrPz" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
{{</ raw >}}

Subsequent Tests and PID Tuning

Our mobot completed the track successfully without the need for resets or multiple trials with a run time of 7.05 seconds and a stopping distance of 14.5 centimeters. While the stopping distance was slightly short of the intended 15 centimeters it was a rather negligible 3% difference from the goal.

The robot followed the line using a PID controller receiving inputs from several line sensors. The sensors detected whether the lightness value was above an experimentally determined threshold. Based on these flags were set for three locations: left, center and right. The distance sensing mechanic was based on a mathematical function run on the values from an ultrasonic range finder. The function converted the value from the ultrasonic to centimeter values.

Our final PID values were the result of numerous tests and recalibrations of the values. Tuning of the PID coefficients to appropriate values is a delicate and important process. If all the values are not balanced appropriately the results will be substantially different than what is desired. My process for filtering the values of the PID coefficients was applying a pseudo-binary search process. I would have the values to reach an optimal point as quickly as possible.

It was interesting to see how the different values of the PID controller impacted the vehicle's trajectory. Within this context, exceptionally large proportional constants can result in one bad reading throwing the path off. Integral values caused what we referred to as the “windshield wiper” effect. The bot would oscillate over the line often causing errors once a turn occurred.