## Magnetic-Spectrometer

A simulation based on the experiment AMS-02, made to study the bending power and efficiency of a spectrometer when hit with an isotropic beam of protons.

Two parameters can be tweaked to play with the resolution of the simulation:

- `N` (initialised in `main.cpp`) - the number of protons generated in the beam
- `h` (initialised in `header.h`) - the resolution used to solve the differential equation in `beam.cpp`

## The simulation

An extensive description of how the simulation works, and its results, can be found in [simulation.md](simulation.md). I used the ROOT library by CERN for random numbers generation and data analysis.

## How to run

This project was containerized, so you only need Docker to run it. To generate the results in `/output/graph.png`, run `build.sh`. Here's a rundown of what's inside the build file:

- Build and run the image

```
docker build -t redpulp/magnetic-spectrometer .
docker run -d --rm -it --name magnetic-spectrometer redpulp/magnetic-spectrometer
```

- Get the result of the simulation (change the destination path to `%cd%/output/graph.png` if you're using Command Prompt)

```
docker cp magnetic-spectrometer:/src/graph.png ${PWD}/output/graph.png
```

- Kill the container and delete the image

```
docker kill magnetic-spectrometer
docker image rm redpulp/magnetic-spectrometer
```

## Note of the author

Please note that this project was made in my Uni years, I code better these days, I promise.
