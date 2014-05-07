# docker-augustus Docker image

#### Maintainer - Timothy Laurent

#Intro
This allows the use of the [Augustus gene modelling suite ](http://bioinf.uni-greifswald.de/augustus/) with Docker through a simple CLI command.

#How to use

1. First clone the github repo in your working dirctory: `git clone https://github.com/timothyjlaurent/docker-augustus.git`
2. The git clone will pull the Augustus config folder to your machine. The image is configured so that the `AUGUSTUS_CONFIG_PATH` environment variable is set to `/config`. There is also a volume `/data` that can be used to mount your data directories. The default command will be this :

    ```
    docker run -v <path to data>:/data:rw -v <path to config e.g.'`pwd`/config' >:/config  tlaurent/docker-augustus     <augustus command> [options]
    ```
3. You can also just enter the container's shell like so:
    ```
    docker run -i -t -v <path to data>:/data:rw -v <path to config e.g.'`pwd`/config' >:/config  tlaurent/docker-augustus bash
    ```

- all data input and output should happen in the mounted volumes and remember that as far as the container is concerned your directories are mounted at the mount points.
    
- for example:
        if you mount `/data/genemodels` at `/data` on the container and there is a directory `input` and `output` in the host `genemodels` directory you would refer to these locatations as `/data/input` and `/data/output` in the docker command.


Note that there is also a ssh daemon that runs with this container, and an init and logging system. For details on how to use this functionality please see the documentation for the [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker) that was used as the baseimage for this image.

