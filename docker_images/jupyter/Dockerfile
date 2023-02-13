FROM jupyter/datascience-notebook:ecabcb829fe0

USER root

# install required libraries

RUN apt-get update \
  && apt-get install -y \
    fonts-ipaexfont

RUN conda install -c conda-forge\
  numpy\
  lightgbm\
  ta-lib

RUN pip install --no-cache-dir \
  ccxt\
  "git+https://github.com/richmanbtc/crypto_data_fetcher.git@v0.0.15#egg=crypto_data_fetcher"

# matplotlibで日本語を使えるようにする
RUN sed -i '/font\.family/d' /opt/conda/lib/python3.9/site-packages/matplotlib/mpl-data/matplotlibrc
RUN echo "font.family: IPAexGothic" >> /opt/conda/lib/python3.9/site-packages/matplotlib/mpl-data/matplotlibrc
RUN rm -rf /home/jovyan/.cache

USER jovyan
