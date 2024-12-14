---
layout: page
title: "Spiking Neural Network Simulatation: Modeling and Synchronization Analysis"
description: A Python-based simulator exploring spiking neural networks and synchronization properties in neuronal systems.
img: assets/img/snn/snn_title.png
importance: 1
category: research
related_publications: false
---

## Introduction

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include video.liquid path="assets/video/simulation.mp4" class="img-fluid rounded z-depth-1" controls=true %}
    </div>
</div>

This project was my final year research project for the Department of Computer Science at the University of Manchester. It involved implementing a Python-based GUI neuronal network simulator to analyze various dynamical behaviors in single neurons and neuronal networks. The study explored firing patterns, synchronization properties, and other nonlinear dynamics, providing insights into the computational and mathematical modeling of neuronal systems.

The primary aim of the project was to develop biologically realistic models of neurons and their networks while keeping computational costs feasible. The simulations examined key electrophysiological behaviors, such as spiking patterns and synchronization, with and without background stimuli.

---

## Methodology

### 1. Implementation and Tools

The neuronal network simulator was implemented using Python3, with the following software tools:

- **[Brian2](https://brian2.readthedocs.io/en/stable/):** Open-source Python simulator for spiking neural networks.
- **[Neurodynex](https://github.com/EPFL-LCN/neuronaldynamics-exercises):** Python exercises for the book [Neuronal Dynamics](https://neuronaldynamics.epfl.ch/index.html).
- **[PyDSTool](https://pypi.org/project/PyDSTool/):** Simulation and analysis toolkit for dynamical systems (ODEs, DAEs, maps, and hybrid systems).
- **[PyQt5](https://pypi.org/project/PyQt5/):** GUI toolkit for creating interactive widgets.

The simulator allowed users to interactively explore the properties of spiking neural networks, visualize different firing behaviors, and analyze synchronization phenomena.

### 2. Simulation and Analysis

Simulations focused on the following:

- **Single neuron dynamics:** Analyzed regular, bursting, and fast firing patterns using spiking neural models.
- **Network behavior:** Explored synchronization in neuronal networks with and without background stimuli, measuring the degree of synchronicity across various configurations.

<div class="row">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/snn/GUI.png" title="Figure 1: GUI Interface for Neuronal Network Simulator" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

---

## Results

### Firing Patterns

The simulator successfully reproduced various firing patterns observed in spiking neurons, as shown below:

### Firing Patterns

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/snn/adex_regular.png" title="Regular Firing Pattern" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/snn/adex_bursting.png" title="Bursting Firing Pattern" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/snn/adex_fast.png" title="Fast Firing Pattern" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Synchronization Analysis

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/snn/simulation_randomvinit.jpeg" title="Random Initial Conditions" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/snn/simulation_regular.jpeg" title="Regular Synchronization" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/snn/simulation_bursting3.jpeg" title="Bursting Synchronization (3 Neurons)" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/snn/simulation_busting8.jpeg" title="Multi-Neuron Bursting (8 Neurons)" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/snn/simulation_fastg.jpeg" title="Fast Synchronization" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Findings

The project highlighted several key findings:

1. Regular, bursting, and fast firing patterns were reproduced accurately using established spiking neuron models.
2. Synchronization analysis revealed that external stimuli significantly influence the synchronicity of neuronal networks.
3. The simulator provides a valuable platform for exploring dynamical systems in computational neuroscience.

The project was recognized as one of the best papers in 2018 by the University of Manchester's Department of Computer Science and featured on the department website.

---

## Future Work

Future work could involve extending the simulator to include:

- **Plasticity mechanisms:** Implementing models of synaptic plasticity to study learning and memory in networks.
- **Advanced network topologies:** Exploring more complex and biologically accurate network structures.
- **Larger-scale simulations:** Leveraging high-performance computing (HPC) to simulate larger neuronal networks.

For further details, refer to the [project report](/assets/pdf/models-of-neurons-and-neuronal-network.pdf) or explore the [repository](https://github.com/wonkwonlee/neurons-and-neuronal-networks) for source code and additional resources.