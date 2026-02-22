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

## Preparatory tasks: implement your first motion-detection SNN

There is a direction-selective network example in [Neuronify](https://ovilab.net/neuronify/), which is illustrated below. This network is designed so that the output neuron tends to fire a spike when the inputs are touched from right to left, but not when touched from left to right (with some limitations on the touching speed).

<center>
<img src='https://raw.githubusercontent.com/fresan/d7046e/main/SNN3/neuronify-net.png' width="500">
</center>

Can you simulate this network using the code from SNN Exercise 1 and the input spikes provided by the data generator above? Can you modify the parameters of the simulated network so that it becomes direction selective?

If you manage to succeed with this task you have designed your first SNN vision system capable of basic motion detection!

**Note:** You need to complete SNN Exercise 1 to acquire the necessary background knowledge for this task.

In the project you can optionally choose to track an object in circular motion, instead of linear motion, as illustrated in the following animation. The problem can be considered either as a classification task (clockwise- or counter-clockwise rotation), or a prediction task (position or velocity of the dot).
<center>
<img src='https://82magnolia.github.io/event_localization/img/events.gif' width="400">
</center>
## SNN project

The challenge for the **SNN project** is to develop a vision system for (1D) motion classification, which is not limited to one specific pattern/feature like the bright spot moving forth and back in the basic data generator above.

For example, you could consider using an open image dataset for training, validation and testing. For testing, the output of a webcam could optionally be considered. The delta modulator concept introduced in SNN Exercise 1 could potentially be used to convert pixel intensities to spikes. Or, you can consider implementing a data generation algorithm for the spinning disk illustrated in the animation above (1D motion in 2D input space).

Some inspiration for the SNN network architecture and training protocol can be obtained also from SNN Exercise 2 where you considered STDP based learning. The [Reichardt Detector](https://en.wikipedia.org/wiki/Motion_perception#The_Reichardt-Hassenstein_model) is one starting point. For biological inspiration, consider for example [motion detection in insects](https://link.springer.com/content/pdf/10.1007/s00359-019-01375-9.pdf). Alternatively, you can use snnTorch (introduced above) for gradient based training, or more advanced SNN simulators like [Brian2](https://brian2.readthedocs.io) where different STDP models are available.

The possibilities for exploration are endless! How you address this challenge is up to each team to decide as long as you strive to meet the minimum requirement outlined at the top of Part 2.

Use the SNN-Project discussion forum in Canvas and the scheduled live sessions to discuss with each other and the teachers.

## Remarks

There is ongoing work to define and compute exact gradients of SNNs that do not rely on surrogate gradients, see for example [DelGrad](https://www.nature.com/articles/s41467-025-63120-y), [EventProp](https://www.nature.com/articles/s41598-021-91786-z), and [From Silicon to Spikes](https://arxiv.org/abs/2507.10568v2). The topic of gradient based optimisation of SNNs is partially controversial because the brain functions in a different way, and is remarkably resource efficient in comparison to deep learning hardware. We should not naively think that gradient-based optimisation is optimal for processors and architectures incorporating brain-like, physically instantiated adaptive processes. Instead, we should maintain an open mindset and systematically develop and compare different alternatives in searching for more resource efficient approaches to design learning machines.
