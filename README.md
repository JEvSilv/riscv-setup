# RISC-V setup
Dockerfiles that contain configurations to set up containers with RISC-V tools.

To build (from scratch) a container from Dockerfile:

    $ cd <path-to-dockerfile-folder>
    $ sudo docker build .

Or just pull from jevsilv/riscv-setup:

    $ sudo docker pull jevsilv/riscv-setup:<tag>

Run the container:

    $ sudo docker run --name <container-name> -it <container> bash

Start the container:

    $ sudo docker start <container-name>

Attach the container:

    $ sudo docker attach <container-name>
    
[CTRL + P and Q]: To exit of the container without turn off it.
