# https://catalog.ngc.nvidia.com/orgs/nvidia/containers/pytorch/tags
# FROM nvcr.io/nvidia/pytorch:18.12-py3
FROM pytorch/pytorch:2.0.1-cuda11.7-cudnn8-runtime

WORKDIR /project

# this may take too long
# RUN apt update && apt upgrade -y
RUN pip install --upgrade pip

RUN pip install jupyterlab
