FROM python:3.6-slim

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -q update && \
    apt-get install -q -y --no-install-recommends \
    xorg \
      unzip \
      wget && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir /matlab-runtime-install && \
    cd /matlab-runtime-install && \
    wget -q https://ssd.mathworks.com/supportfiles/downloads/R2020a/Release/6/deployment_files/installer/complete/glnxa64/MATLAB_Runtime_R2020a_Update_6_glnxa64.zip && \
    unzip -q MATLAB_Runtime_R2020a_Update_6_glnxa64.zip && \
    rm -f MATLAB_Runtime_R2020a_Update_6_glnxa64.zip && \
    ./install -agreeToLicense yes -mode silent && \
    cd / && \
    rm -rf matlab-runtime-install

ENV LD_LIBRARY_PATH /usr/local/MATLAB/MATLAB_Runtime/v98/runtime/glnxa64:/usr/local/MATLAB/MATLAB_Runtime/v98/bin/glnxa64:/usr/local/MATLAB/MATLAB_Runtime/v98/sys/os/glnxa64:/usr/local/MATLAB/MATLAB_Runtime/v98/sys/opengl/lib/glnxa64

ENV XAPPLRESDIR /etc/X11/app-defaults
