FROM cssinsurance/jupyter-gpu-base@sha256:9e769d1d5d7a37c0160deab5b62a8d9993cb129e3cd202ecda837694333331ed

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
RUN pip install jupyterlab-code-formatter==1.2.* autopep8==1.5.* isort==4.3.* nbdime==2.0.*

USER root
RUN jupyter labextension install @ryantam626/jupyterlab_code_formatter@^v1.2.4 --no-build && \
    jupyter labextension install @jupyterlab/toc@^v3.0.0 --no-build && \
    jupyter labextension install jupyterlab-python-file@^v0.4.0 --no-build && \
    jupyter lab build -y && jupyter lab clean -y && \
    jupyter serverextension enable --py jupyterlab_code_formatter --sys-prefix
USER $NB_UID
