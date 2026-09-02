# EHARG-HRC:A Comprehensive Benchmark Suite for Event Camera-Based Human Action Recognition and Gaze Estimation in Human-Robot Collaboration
## Overview
 
Event cameras report per-pixel brightness changes asynchronously rather than
capturing full frames at a fixed rate, which gives them microsecond temporal
resolution, high dynamic range, and low power draw — properties that suit
human–robot collaboration, where a perception system must track a moving
operator continuously under variable lighting and often on embedded hardware.
Progress in this direction has been limited by data: almost every human–robot
interaction dataset is RGB, and the few event-domain datasets that exist target
other tasks. This repository accompanies our paper and releases the resources
built to close that gap. It contains six existing human–robot interaction and
head detection datasets converted to the event domain through a uniform
pipeline, one dataset recorded natively with a Prophesee EVK4 event camera, and
the full benchmarking code — data loaders, model implementations, training
configurations, and evaluation scripts — used to produce every result reported
in the paper. Together these allow event-domain action recognition, head
detection, and attention estimation to be studied under a single consistent
protocol, and allow new models to be dropped into that protocol with everything
else held fixed.
 
## Datasets
 
### EHARG
 
EHARG is our own dataset and the only one in the suite recorded natively with an
event camera rather than converted from video. It captures physical human–robot
collaboration at a shared workstation, with participants manually guiding a
robot manipulator by grasping and controlling its end effector. Recording uses a
Prophesee EVK4 (IMX636 sensor, 1280×720) mounted at workstation height and
positioned diagonally to the workspace, so that the participant's upper body,
head, and the interaction area all fall within one field of view. Annotation
covers three entities per frame — the human head, the robot end effector, and
the attention target — alongside eight mutually exclusive action classes that
segment a complete collaboration cycle: IDLE, robot operating autonomously,
human entering the workspace, human sitting, human approaching the robot, human
interacting with the robot, human disengaging, and human leaving. Because the
classes are consecutive rather than independent, every frame carries exactly one
label. Evaluation uses a subject-independent split, with no participant
appearing in both the training and test partitions.
 
### HRI30
 
HRI30 is an industrial human–robot interaction dataset covering thirty
fine-grained action categories performed in a collaborative assembly setting. It
is the largest and most class-rich of the converted datasets, which makes it the
most demanding test of whether RGB-to-event conversion preserves discriminative
content, and it is the dataset on which we run our RGB-versus-event control
comparison. We release both the original thirty-class labelling and a
consolidated twelve-class variant that merges categories separated by fine
manipulation detail not recoverable from motion alone; comparing results across
the two granularities isolates the effect of label granularity from that of
architecture.
 
### CoAx
 
CoAx captures collaborative assembly between a human and a robot, with actions
annotated over the course of a shared task. Its interactions are longer and more
loosely structured than in scripted datasets, so the converted event streams
contain extended periods of sustained activity interleaved with quieter
intervals — a distribution that tests whether models depend on activity density
rather than on the structure of the motion itself.
 
### Electronic Assembley
 
EDA provides annotated human activity in a workspace setting, contributing
another view of collaborative task execution to the suite. Its inclusion
broadens the range of recording conditions, viewpoints, and action vocabularies
represented, which matters for a benchmark intended to show that conclusions
hold across sources rather than on any single corpus.
 
### QUB-PHEO
 
QUB-PHEO is a large-scale human–robot interaction dataset built around
multi-view recordings of assembly tasks with a substantial number of
participants. Its scale and subject diversity make it the strongest available
test of whether event-domain models generalise across people, and its
multi-view structure allows viewpoint sensitivity to be examined separately from
subject variation.
 
### SHAD
 
SHAD contributes human action recordings in a setting distinct from the
industrial assembly scenarios that dominate the rest of the suite. Including a
dataset with different action semantics and recording conditions guards against
overfitting the benchmark to one style of interaction, and gives a reference
point for how transferable event-domain action models are across domains.
 
### HollywoodHeads
 
HollywoodHeads is a head detection dataset drawn from film footage, comprising
369,846 annotated heads across 224,740 frames. It serves a different purpose
from the action recognition datasets: our attention estimation pipeline takes a
cropped head region as one of its two input streams, so a head detector operating
in the event domain is a prerequisite for deployment without ground-truth
annotation. Converting HollywoodHeads to events provides training and evaluation
data for that detector at a scale unavailable in any purpose-built event dataset,
and its diversity of pose, scale, and scene composition makes it a demanding
benchmark in its own right.

### NOTE

Due to large size of dataset, it is taking longer than usual to properly upload all datasets. As soon as we upload the datasets, we will update the links in each dataset section.

### Website

If you are interested in other works done by our group, please visit our website.

https://neuro.humanrobot.team/
