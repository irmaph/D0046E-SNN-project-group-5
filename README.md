# Part 2 of SNN 3: Motion Detection Project

The SNN project focuses on creating a vision system based on a spiking neural network (SNN) that responds to specific visual motion. Study the examples and code provided below to develop an intuition for the problem and decide whether you want to focus on the SNN or ANN project.

## Project requirements

The minimum requirement is that you should design, train and evaluate a spiking neural network that responds to specific movements in a one-dimensional input space or manifold encoded by a set of receptor neurons (e.g. one output neuron population is activated for "left" and the other for "right" movement). You can consider linear or circular motion, as well as bio-inspiration if you are interested to learn more about visual systems of animals (retinas, compound eyes of insects, etc.).

## Motion patterns and data

The (simulated) input neurons can be stimulated with synthetic patterns, images, or live input from a web camera. The receptor neurons can for example be implemented with delta modulators, introduced in the first SNN exercise, or the methods introduced in the snnTorch tutorial above. Optionally, you can use a prerecorded dataset from a neuromorphic vision sensor ("event camera") which can be found online.

The following animation illustrates a motion detection task where a bright spot is moving across a one-dimensional array of virtual receptor neurons.

<center>
<img src='https://raw.githubusercontent.com/fresan/d7046e/main/SNN3/1d-motion.gif' width="600">
</center>

In this example the task is to determine whether the pattern is moving, and whether it is moving towards the left or right. The following code implements a basic spike data generator inspired by the animation above. For simplicity, it is assumed that a bright spot is moving at constant speed back and forth, and that one spike is generated when the bright spot is passing over a receptor neuron.
