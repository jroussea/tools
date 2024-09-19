# Worklow environment

This repository contains the environment and files needed to build Singularity and Docker containers for my various projects.

# Tools

| Tools         | Version       | Conda / Mamba | Singularity | Docker | Documentation | References |
| :-----------: | :-----------: | :-----------: | :---------: | :----: | :-----------: | :--------: |
| LAGOO-MCL     | x.x.x         | Yes           | Yes         | No     | No            | No         |
| CATH tools    | 0.16.5        | Yes           | Yes         | No     | [Link](https://cath-tools.readthedocs.io/en/latest/) | [Link](https://www.sciencedirect.com/science/article/pii/0022283689900843?via%3Dihub) |
| Diamond       | 2.1.8         | Yes           | Yes         | No     | [Link](https://github.com/bbuchfink/diamond/wiki) | [Link](https://www.nature.com/articles/s41592-021-01101-x) |                
| HMMER         | 3.4           | Yes           | Yes         | No     | [Link](http://eddylab.org/software/hmmer/Userguide.pdf) | [Link](http://eddylab.org/software/hmmer/Userguide.pdf) |
| MCL           | 22.282        | Yes           | Yes         | No     | [Link](https://micans.org/mcl/) | [Link-1](https://epubs.siam.org/doi/10.1137/040608635) - [Link-2](https://pubmed.ncbi.nlm.nih.gov/11917018/) - [Link-3](https://pubmed.ncbi.nlm.nih.gov/22144159/) |

# Use

```bash
git clone https://github.com/jroussea/tools.git
```

## Conda and Mamba environments

Change `tool/version/conda` to the path to the file. For example `diamond/2.1.8/conda/diamond.yml

```bash
conda create -f tool/version/conda/environment.yml

conda activate environment
```

Or

```bash
mamba create -f tool/version/conda/environment.yml

mamba activate environment
```

### Example of use

```bash
conda create -f diamond/2.1.8/conda/diamond.yml

conda activate diamond-2-1-8
```

## Singularity 

Change `container_name` by the name of the container. For example `diamond.sif`.

```bash
sudo singularity build container_name.sif tool/version/singularity/container_name.def

singularity run container_name.sif [option]
```

If you don't want to use the `sudo` command, you can add the `--fakeroot` option.

### Example of use

```bash
sudo singularity build diamond-2-1-8.sif diamond/2.1.8/singularity/diamond.def
or
singularity build --fakeroot diamond-2-1-8.sif diamond/2.1.8/singularity/diamond.def

singularity run diamond-2-1-8.sif diamond --help
```