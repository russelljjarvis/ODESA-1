# ODESA

![https://github.com/russelljjarvis/ODESA-1/actions](https://github.com/russelljjarvis/ODESA-1/actions/workflows/build.yml/badge.svg)

<p align="center">
  <a href="#Description">Description</a> •
  <a href="#Verification">Verification</a> •
  <a href="#TODO">TODO</a> •
</p>

## Description 
FPGA implementation of the Odesa algorithm: a supervised spiking and time surface learning algorithm.

## Verification

<p align="center">
	<img src="https://user-images.githubusercontent.com/53887767/174504252-cd42a9eb-fe8f-4900-8fdc-23cec215f9eb.png" width="350" height="300">
</p>

#### In order to run verilator (cloud simulation verification).

Steps:
understand that:
1. `src/odesa.v` was copied into `src/top.v`

2. The file .github/workflows/build.yml
contains the second from final line:
3. 
```bash
run: docker run -v ${PWD}/src:/work --user $(id -u):$(id -g) -e CCACHE_DIR=/work/.ccache --entrypoint make verilator/verilator:stable
```
This docker command calls make on `src/Makefile` which then compiles the `cpp` code:

4. `src/sim_main.cpp` calls `src/top.v` (formerly odesa.v)

5. To summarize the docker image of verilator contains an environment that is able to compile a simulation by applying sim_main.cpp to top.v


### TODO:  
- [x] Some Verilator Output
- [ ] CI verilator. Demonstrate that HDL engineers can automate and do code integration in the cloud just like the rest of the software world.
- [ ] verilator GTK wave verification of SNN signals
- [ ] Command line scripts lend themselves to automation, GUIs lend themselves to human intervention.
- [ ] Command line installation and execution of Lattice Ice Breaker for a relatively small network.

