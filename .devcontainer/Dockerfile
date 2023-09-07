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
RUN apt-get -y install wget && apt-get -y install software-properties-common \
    && wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb \
    && dpkg -i cuda-keyring_1.1-1_all.deb \
    && rm cuda-keyring_1.1-1_all.deb 

RUN wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin \
    && mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600 \
    && apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/3bf863cc.pub \
    && add-apt-repository "deb https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/ /" -y \
    && apt-get install libcudnn8=8.9.4.*-1+cuda11.8 \
    && apt-get install libcudnn8-dev=8.9.4.*-1+cuda11.8 

RUN apt-get -y install zlib1g g++ freeglut3-dev \
    libx11-dev libxmu-dev libxi-dev libglu1-mesa libglu1-mesa-dev libfreeimage-dev -y \
    && pip3 cache purge \
    && apt-get autoremove -y \
    && apt-get clean