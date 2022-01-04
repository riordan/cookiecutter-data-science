# See here for image contents: https://hub.docker.com/r/jupyter/datascience-notebook/

FROM jupyter/scipy-notebook:ubuntu-20.04

# install gcloud
USER root
RUN apt-get update && apt-get install -y apt-transport-https ca-certificates gnupg curl &&\
    echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg  add - && apt-get update -y && apt-get install google-cloud-sdk -y &&\
    rm -rf /var/lib/apt/lists/*
USER ${NB_UID}

# We want to run common-debian.sh from here:
# https://github.com/microsoft/vscode-dev-containers/tree/main/script-library#development-container-scripts
# But that script assumes that the main non-root user (in this case jovyan)
# is in a group with the same name (in this case jovyan).  So we must first make that so.
ADD https://raw.githubusercontent.com/microsoft/vscode-dev-containers/v0.209.6/script-library/common-debian.sh /tmp/library-scripts/
USER root
RUN apt-get update \
 && groupadd jovyan \
 && usermod -a -G jovyan jovyan \
 && bash /tmp/library-scripts/common-debian.sh \
 && apt-get clean -y && rm -rf /var/lib/apt/lists/* /tmp/library-scripts
 USER ${NB_UID}

 RUN pip install --quiet --no-cache-dir && \
     pyarrow && \
     google-cloud-bigquery && \
     google-cloud-bigquery-storage && \
     google-cloud-storage && \
     pandas-gbq && \
     pydata-google-auth && \
     black && \
     flake8 && \
     pandas-profiling && \
     pytest && \
     fix-permissions "${CONDA_DIR}" && \
     fix-permissions "/home/${NB_USER}"


COPY --chown=${NB_UID}:${NB_GID} requirements.txt /tmp/
RUN pip install --quiet --no-cache-dir --requirement /tmp/requirements.txt && \
#    pip install --quiet --no-cache-dir pystan<3.0 && pip install --quiet --no-cache-dir prophet && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"
