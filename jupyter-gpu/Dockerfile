FROM cschranz/gpu-jupyter@sha256:8ae66707ffd31351b04585e6a8508fd761a2f3cd9b7f5f0dca68980bd3d9b853

USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      vim \
      ssh-client \
      libaio1 \
      htop \
    && \
    rm -rf /var/lib/apt/lists/*

USER $NB_UID

RUN pip install jupyterlab-code-formatter==1.2.* autopep8==1.5.* isort==4.3.* nbdime==2.0.* && \
    jupyter labextension install @ryantam626/jupyterlab_code_formatter@^v1.2.4 --no-build && \
    jupyter labextension install @jupyterlab/toc@^v3.0.0 --no-build && \
    jupyter labextension install jupyterlab-python-file@^v0.4.0 --no-build && \
    jupyter lab build -y && jupyter lab clean -y && \
    jupyter serverextension enable --py jupyterlab_code_formatter --sys-prefix
