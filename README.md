# Multi body pendulum



[![Build Status][build-image]][build-url]
[![Code Coverage][coverage-image]][coverage-url]

<!-- Badges: -->

[build-image]: https://github.com/mathspp/extendedjson/actions/workflows/build.yaml/badge.svg
[build-url]: https://github.com/mathspp/extendedjson/actions/workflows/build.yaml
[coverage-image]: https://codecov.io/gh/mathspp/extendedjson/branch/main/graph/badge.svg
[coverage-url]: https://codecov.io/gh/mathspp/extendedjson/

Simulation software for multi-body pendulums using Runge-Kutta 4, and with vizualization of the pendulum:

![5-body pendulum animation](https://github.com/tueboesen/multi-body-pendulum/blob/master/docs/multibodypendulum.gif)

and the energy:

![Energy](https://github.com/tueboesen/multi-body-pendulum/blob/master/docs/energy.png)

## Installation
    pip install multibodypendulum

## Quick start
A quick usecase to simulate a 5 pendulum system could look like this

    n = 5
    dt = 0.001
    g = 9.82
    mbp = MultiBodyPendulum(n, dt,g=g)
    theta0 = 0.5*math.pi*torch.ones(n)
    dtheta0 = 0.0*torch.ones(n)
    nsteps = 100
    times, thetas, dthetas = mbp.simulate(nsteps,theta0,dtheta0)
    mbp.plot_energy()
    mbp.animate_pendulum()

## Limitations
The code has some limitations:
- The simulation uses pytorch. The code could easily be ported to numpy as well, but for now it uses pytorch.
- The simulation assumes pendulums of mass 1 kg, and length between pendulums of 1 m. These assumptions significantly speeds up the simulation and was all I needed for my usecase.
