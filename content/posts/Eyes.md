---
title: "Eye-Lid Software"
summary: "Software to track the position of an individuals eyelids"
list: true
draft: true
---

For the past few years, I've been working on and off again with various researchers at Johns Hopkins and other institutions to write software that can accurately track the position of an eyelid.

The idea is to put this software to use in

The first iteration of this software used OpenCV and a tuned edge detection nd filtration program to select just the rim of the eye. From there, the distance between the uppermost and lowermost pixels was computed. Without specific inputs, it isn't possible to scale the pixels to an inch measurement, but it would still function in a way that allowed comparison to select the optimal eye weights.

The current approach is using a Keypoint detection algorithm based on .

Additional work could be done to integrate optical flow techniques to get a better estimation of the position of the eye ridge. The system could also be trained with more keypoints along the eye lid.

A simpler approach could use a coloured dot or mascara to assist the computer in finding the eyelid accurately.