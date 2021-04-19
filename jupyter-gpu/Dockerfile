FROM cschranz/gpu-jupyter:1.4_cuda-11.0_ubuntu-20.04

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

RUN pip install pystan==2.19.1.1 fbprophet pytesseract opencv-contrib-python-headless jupyter-server-proxy==3.0.* \ 
    jupyter_bokeh==3.0.* jupyterlab-code-formatter==1.4.* autopep8==1.5.* isort==5.7.* nbdime==2.1.* jupyterlab-python-file==0.5.* && \
    jupyter lab build -y && jupyter lab clean -y
