# README

This [Docker image](./Dockerfile) installs PyTorch and
a few more Python libraries for natural language processing (NLP), in addition to those included in the [jupyter/scipy-notebook](https://hub.docker.com/r/jupyter/scipy-notebook), which already includes many popular libraries for machine learning:

* [Documentation of jupyter/scipy-notebook](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook)
* [Dockerfile for jupyter/scipy-notebook](https://github.com/jupyter/docker-stacks/blob/master/scipy-notebook/Dockerfile)

## To Build:
From a shell in the directory that contains the `Dockerfile`:
```{bash}
docker build --rm -t more-nlppt-notebook .
```

That command creates a [Docker](https://www.docker.com/) image named `more-nlppt-notebook`, using the `Dockerfile` in the current working directory (thus, the `.` at the end of the command).

## To Run:
```{bash}
docker run -it --rm \
  --name more-nlppt \
  -p 8888:8888 \
  -v "$PWD":/home/jovyan/work more-nlppt-notebook
```

* Runs interactively (`-it`), logging to the shell window.
* The `--rm` option causes the container to be deleted when the container is stopped.
* The container is named, `more-nlppt`.
* The Jupyter server will be available at `localhost:8888` on your computer.
* Mapping `$PWD` to the container's `work` directory, enables files and directories in the current working directory (where you execute the `docker run` command) to appear in the `work` folder in the Jupyter server.
* When the container starts up, it will display a URL where you can connect to the Jupyter server. The URL will contain a security token, such as:  
    `http://127.0.0.1:8888/?token=df8967d5e976529b9fb387337c095545a6bd1ef5fbb86f24`
* To stop the container:
    * Type `<CTRL>c` in the shell window; _or_
    * Click on the `Quit` button in the upper right of the Jupyter file browser.

## LICENSE
Copyright (c) 2020 Jim Tyhurst

Distributed under the terms of the Modified BSD License (BSD-3-Clause).
