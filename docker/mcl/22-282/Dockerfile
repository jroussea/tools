FROM continuumio/anaconda3

# updating and installing dependencies
RUN apt-get update && apt install -y procps g++

# seqkit download and creation of the /data directory which will contain the data for the analyzes
RUN conda install -c conda-forge -c bioconda mcl==22.282

RUN mkdir data

# set /data as working directory
WORKDIR /data