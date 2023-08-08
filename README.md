# docker-dsml
Run Jupyter notebooks with Tensorflow Pytorch GPU support for NVIDIA

### Prerequisites
Host machine needs to have the following installed. 
  - [Docker](https://docs.docker.com/get-docker/)
  - [NVIDIA® driver](https://github.com/NVIDIA/nvidia-docker/wiki/Frequently-Asked-Questions#how-do-i-install-the-nvidia-driver) (the NVIDIA® CUDA® Toolkit is not required)
  - [Nvidia Container Toolkit](https://github.com/NVIDIA/nvidia-docker/blob/master/README.md#quickstart)

  Additional resources and installation guides can be found in:
  - Tensoflow [documentation](https://www.tensorflow.org/install/docker#gpu_support)
  - Docker hub images used for [Tensorflow](https://hub.docker.com/r/tensorflow/tensorflow/)
  - Docker hub images used for [Pytorch](https://hub.docker.com/r/pytorch/pytorch/tags)

### How to use
Your notebooks and any other files needed, should go to the project directory. This directory will be mounted on the container on start up. Any additional dependencies, needed by you project, should go to the additional-requirements.txt. Note that you don't need numpy, tensorflow or torch, because they are already provided by the container.

To start the container, pick the docker-compose.yml and run the command. This will pip install your dependencies, specified in the additional-requirements.txt, and start a Jupyter lab server. 
```
docker compose up -d
```
The Jupyter lab server will run on http://localhost:8899. You can change that in docker-compose.yml. 

To access the Jupyter lab server you need to get the token required. To do that, run 
```
docker container logs --follow name_of_container
```
where name_of_container should be replaced by the name of the container. By default, it's something like project-tensorflow-gpu-container, depending on the docker-compose.yml.

At the end of the logs, there should be text like the following:

```
    To access the server, open this file in a browser:
        file:///root/.local/share/jupyter/runtime/jpserver-1-open.html
    Or copy and paste one of these URLs:
        http://e1d8a869b7a8:8888/lab?token=bca8ca8854018e14c505399f340061df6d9b29bb902fdd02
        http://127.0.0.1:8888/lab?token=bca8ca8854018e14c505399f340061df6d9b29bb902fdd02
```
Copy the URL and change the port to 9988. For the example above the URL to visit is http://localhost:8899/lab?token=bca8ca8854018e14c505399f340061df6d9b29bb902fdd02
