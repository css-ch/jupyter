FROM cschranz/gpu-jupyter:v1.5_cuda-11.6_ubuntu-20.04

USER root

RUN rm /etc/apt/sources.list.d/cuda.list || true && rm /etc/apt/sources.list.d/nvidia-ml.list && || true \
      apt-get update && \
      apt-get install -y --no-install-recommends \
      vim \
      ssh-client \
      libaio1 \
      libgit2-dev \
      htop \
      zip \
      openjdk-11-jdk \
      imagemagick imagemagick-doc \
      libgdal-dev libproj-dev gdal-bin \
      dstat \
      tesseract-ocr-all \
      libtesseract-dev \
      libhunspell-dev \
      g++ \
      swig \
      xvfb \
      unattended-upgrades \
    && \
    unattended-upgrade \
    && \
    rm -rf /var/lib/apt/lists/*

COPY image_magick_conf/policy.xml /etc/ImageMagick-6/policy.xml

USER $NB_UID
RUN pip install pystan==3.6.* prophet pytesseract opencv-contrib-python-headless jupyter-server-proxy>=3.2.1 lux-api \
    jupyter_bokeh==3.0.* jupyterlab-code-formatter==1.6.* autopep8==2.0.* isort==5.12.* nbdime==3.1.* jupyterlab-python-file==0.5.*  lux-widget>=0.1.11 && \
    jupyter lab build -y && jupyter lab clean -y

RUN mkdir /root/.ssh && echo -e "IdentityFile /home/jovyan/.ssh/id_rsa\nUserKnownHostsFile /home/jovyan/.ssh/known_hosts" > /root/.ssh/config

RUN conda install -y nb_conda_kernels
RUN conda install -y -c conda-forge r-rjava r-gert && conda clean -afy

COPY conda_config/.condarc /home/jovyan/.condarc
