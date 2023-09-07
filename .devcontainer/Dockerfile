FROM nvidia/cuda:11.8.0-devel-ubuntu22.04
RUN apt-get -y update && apt-get upgrade -y 
RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install git \
    python3-pip \ 
    python3-dev \
    python3-wheel \
    python3-setuptools \
    python3-opencv \
    libglib2.0-0
RUN python3 -m pip install --upgrade pip
COPY requirements.txt requirements.txt
RUN pip3 install --user -r requirements.txt
RUN pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
