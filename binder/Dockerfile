FROM rapidsai/rapidsai:cuda10.0-devel-ubuntu18.04

#USER root

# create user with a home directory
ARG NB_USER
ARG NB_UID
ENV USER ${NB_USER}
ENV HOME /home/${NB_USER}

RUN adduser --disabled-password \
--gecos "Default user" \
--uid ${NB_UID} \
${NB_USER}

WORKDIR ${HOME}


RUN apt-get update && apt-get install --no-install-recommends -y \
        git \
        vim \
        graphviz \
        && rm -rf /var/lib/apt/lists/*

RUN source activate rapids && conda install -y -c conda-forge nodejs \
    && jupyter labextension install jupyterlab_vim

#WORKDIR /
WORKDIR ${HOME}

USER ${USER}
