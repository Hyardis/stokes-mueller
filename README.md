# Stokes-Mueller Simulations of Polarization State

## Overview
This package enables physics simulations of light polarization. It treats the information about the polarization state as a vector (Stokes vector) and each change of the polarization state is represented as an algebraic transformation of this vector (Mueller matrix). These changes of polarization state are achieved by an appropriate positioning of different optical elements in the beam's path, where the crucial factor on the resulting polarization effect is their orientation. These simulations predict the evolution of the polarization state as the beam passes through an experimental setup consisting of multiple optical elements, parametrized by the elements' orientations. The results obtained by scanning over different positions of the elements then enable finding the optimal settings of the setup for the desired polarization state. 

The main motivation for the development of this model was its utilization in time-resolved photoelectron circular dichroism (TR-PECD) spectroscopy as an experimental setup optimization tool. Therefore, it focuses on the use of reflective optics, namely metallic mirrors, in achieving a high degree of circular polarization of high-energy light, especially in the EUV and XUV spectral range. It is mainly intended for use by experimentalists, researchers and students in the area of optics, ellipsometry, and physical and analytical chemistry.

## Installation

You can install `stokes_mueller` directly from the main GitHub repository using `pip`:

```bash
pip install git+https://github.com/Hyardis/stokes-mueller.git
```

## Quick Start

Below is an example of how to run a simple simulation using the `stokes_mueller` package:

```python
import numpy as np
import stokes_mueller as sm

# 1. Define the experimental setup to be simulated.
# 'qwp' denotes a quarter-wave plate.
# 'Au' denotes a golden mirror.
elements = ('qwp', 'Au')

# 2. Define the setup geometry.
# Orientations of both elements are parametrized.
incidence = (0, 62.5)
orientations = (np.arange(-90, 90), np.arange(-90, 90))

# 3. Define the incident beam by its Stokes vector and energy.
# This beam is horizontally linearly polarized.
Stokes_vector = (1, 1, 0, 0)
beam_energy_eV = 1.55

# 4. Run the simulation itself, the results are plotted automatically. 
# The 'show' option specifies to plot the degree of circular polarization. 
sm.plot_setup(
    Stokes_vector,
    beam_energy_eV,
    elements,
    incidence,
    orientations,
    show = 'PC'
)
```