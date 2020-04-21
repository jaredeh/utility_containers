FROM jupyter/r-notebook

USER root

RUN apt-get update && apt-get install -y python-apt && rm -rf /var/lib/apt/lists/*

USER $NB_UID

RUN conda install --quiet --yes \
    'plotly' \
    'ipywidgets' \
    && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR

RUN jupyter labextension install @jupyter-widgets/jupyterlab-manager --no-build
RUN jupyter labextension install jupyterlab-plotly --no-build
RUN jupyter labextension install plotlywidget --no-build
RUN jupyter lab build
