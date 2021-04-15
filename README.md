# RISC-V setup
Dockerfiles that contain configurations to set up containers with RISC-V tools.

To build (from scratch) a container from Dockerfile:
$ cd <path-to-dockerfile-folder>
$ sudo docker build .

Or just pull from jevsilv/riscv-setup:
$ sudo docker pull jevsilv/riscv-setup:<tag>

Running the container:
$ sudo docker run --name <name> -it <container> bash

Starting the container:
$ sudo docker start <container-id>

Attaching thec container:
$ sudo docker attach <container-id>
