FROM rapidsai/rapidsai:cuda10.0-devel-ubuntu18.04

#USER root

# create user with a home directory
#ARG CONDA_ENV=rapids
ARG NB_USER
ARG NB_UID
#ENV CONDA_DEFAULT_ENV ${CONDA_ENV}
ENV PATH /conda/envs/rapids/bin/:$PATH
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

#RUN source activate rapids && conda install -y -c conda-forge nodejs \
#    && jupyter labextension install jupyterlab_vim

#RUN conda install -y -c conda-forge nodejs \
#    && jupyter labextension install jupyterlab_vim

#RUN echo "source activate rapids" > ~/.bashrc
#WORKDIR /
#WORKDIR ${HOME}

#USER ${USER}

# Make sure the contents of our repo are in ${HOME}
COPY . ${HOME}
USER root
RUN chown -R ${NB_UID} ${HOME}
USER ${NB_USER}
