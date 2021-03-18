FROM jupyter/all-spark-notebook:d990a62010ae
USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      vim \
      ssh-client \
      libaio1 \
      htop \
      zip \
      openjdk-11-jdk \
      imagemagick imagemagick-doc \
      libgdal-dev libproj-dev gdal-bin \
      dstat \
	  r-cran-rjava \
	  tesseract-ocr-all \
	  libtesseract-dev \
    && \
    rm -rf /var/lib/apt/lists/*

USER $NB_UID
RUN pip install fbprophet pytesseract opencv-contrib-python-headless jupyterlab-code-formatter==1.4.* autopep8==1.5.* isort==5.7.* nbdime==2.1.* jupyterlab-python-file==0.5.* && \
    jupyter labextension install @ryantam626/jupyterlab_code_formatter@^v1.4.4 --no-build && \
    jupyter lab build -y && jupyter lab clean -y && \
    jupyter serverextension enable --py jupyterlab_code_formatter --sys-prefix
