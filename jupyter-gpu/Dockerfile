FROM cschranz/gpu-jupyter:e5eb8f6

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
