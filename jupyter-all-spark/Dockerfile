FROM jupyter/all-spark-notebook:2021-09-27
USER root

RUN apt-get update && \
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
      g++ \
    && \
    rm -rf /var/lib/apt/lists/*

COPY image_magick_conf/policy.xml /etc/ImageMagick-6/policy.xml

USER $NB_UID
RUN pip install pystan==2.19.1.1 fbprophet pytesseract opencv-contrib-python-headless jupyter-server-proxy==3.0.* \ 
    jupyter_bokeh==3.0.* jupyterlab-code-formatter==1.4.* autopep8==1.5.* isort==5.7.* nbdime==3.1.* jupyterlab-python-file==0.5.* && \
    jupyter lab build -y && jupyter lab clean -y

RUN conda install -y -c conda-forge r-rjava r-gert && conda clean -afy
