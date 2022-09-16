# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.245.2/containers/ubuntu/.devcontainer/base.Dockerfile

FROM osrf/ros:noetic-desktop-full

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends ros-noetic-libfranka ros-noetic-franka-ros

RUN echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc