FROM quay.io/jupyter/all-spark-notebook:2024-11-11
USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      vim \
      ssh-client \
      libaio1t64 \
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
      unattended-upgrades \
      swig \
      xvfb \
    && \
    unattended-upgrade \
    && \
    rm -rf /var/lib/apt/lists/*

COPY image_magick_conf/policy.xml /etc/ImageMagick-6/policy.xml

USER $NB_UID
RUN conda install -y conda-forge::nodejs
RUN pip install jupyter-server==2.* pystan==3.10.* prophet pytesseract opencv-contrib-python-headless jupyter-server-proxy>=4.4.0 lux-api \
    jupyter_bokeh==4.0.* jupyterlab-code-formatter==3.0.* autopep8==2.0.* isort==5.12.* nbdime==4.0.* jupyterlab-python-file==0.5.*  lux-widget>=0.1.11 && \
    jupyter lab build -y && jupyter lab clean -y

RUN conda install -y nb_conda_kernels
RUN conda install -y -c conda-forge r-rjava r-gert && conda clean -afy

COPY conda_config/.condarc /home/jovyan/.condarc
