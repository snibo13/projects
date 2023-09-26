---
title: "Context-Aware Object Recognition"
draft: false
date: 2022-08-15T22:46:34-05:00
list: true
summary: "Using other objects in scene to discern location and adjust confidence"
color: "#5B8C5A"
---

# Problem:
I know very little about machine learning and artificial intelligence. In an effort to get my feet wet in a somewhat practical way (excluding the tutorials from pytorch, etc) I wanted to see if I could create a object recognition system that wasn't just a clone of an old paper.

Object recognition systems are already highly accurate, but one potential area for improvement could be the time it takes to recognize an object.

# Solution:
The idea functions on the basis that a system recognizing objects from a smaller subset would be more accurate than a more general system.

To that end, I was thinking about a three stage system:
Stage 1: A traditional CNN-based image recognition system
Stage 2: Evaluate the scene or situational context based on the items identified with the highest confidence level
Stage 3: Adjust the confidence of the detected objects using a probabalistic heuristic

One approach to the heuristic could be object coincidence probabilities, that is how often objects appear in the same scene or context.

An alternative approach would be to use a secondary classifier to identify a potential context and use that to adjust confidences based on what objects are likely to be in these contexts.


# Where I'm At:
This ended up being a larger time commitment than I originally anticipated. The course I was planning to take to get a better background in machine learning was also cancelled so I've been relying on self study and its a bit slow going.

I've selected CenterNet MobileNet v2 as the first stage, and I was planning to evaluate its performance in comparison to other methods that fall within the same time horizon but I have yet to implement the other two stages.