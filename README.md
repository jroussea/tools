# Worklow environment

This repository contains the environment and files needed to build Singularity and Docker containers for my various projects.

# Tools

| Tools         | Version       | Conda / Mamba | Singularity | Docker | Documentation | References |
| :-----------: | :-----------: | :-----------: | :---------: | :----: | :-----------: | :--------: |
| LAGOON-MCL     | x.x.x         | [Yes](lagoon-mcl/x.x.x/conda/lagoon-mcl.yml) | [Yes](lagoon-mcl/x.x.x/singularity/lagoon-mcl.def) | No     | No            | No         |
| CATH tools    | 0.16.5        | [Yes](cath-tools/0.16.5/conda/cath-tools.yml) | [Yes](cath-tools/0.16.5/singularity/cath-tools.def) | No     | [Yes](https://cath-tools.readthedocs.io/en/latest/) | [Yes](#cath-tools) |
| Diamond       | 2.1.8         | [Yes](diamond/2.1.8/conda/diamond.yml) | [Yes](diamond/2.1.8/singularity/diamond.def) | No     | [Yes](https://github.com/bbuchfink/diamond/wiki) | [Yes](#diamond) |                
| HMMER         | 3.4           | [Yes](hmmer/3.4/conda/hmmer.yml) | [Yes](hmmer/3.4/singularity/hmmer.def) | No     | [Yes](http://eddylab.org/software/hmmer/Userguide.pdf) | [Yes](#hmmer) |
| MCL           | 22.282        | [Yes](mcl/22.282/conda/mcl.yml) | [Yes](mcl/22.282/singularity/mcl.def) | No     | [Yes](https://micans.org/mcl/) | [Yes](#mcl) |

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

# Reference

## CATH-tools

1. W. R. Taylor et C. A. Orengo, « Protein structure alignment », Journal of Molecular Biology, vol. 208, no 1, p. 1‑22, juill. 1989, doi: [10.1016/0022-2836(89)90084-3](https://doi.org/10.1016/0022-2836(89)90084-3).

## Diamond

1. B. Buchfink, K. Reuter, et H.-G. Drost, « Sensitive protein alignments at tree-of-life scale using DIAMOND », Nat Methods, vol. 18, no 4, Art. no 4, avr. 2021, doi: [10.1038/s41592-021-01101-x](https://doi.org/10.1038/s41592-021-01101-x).

## HMMER

1. S. R. Eddy et HMMER development team, « HMMER User’s Guide », 2020.

## MCL

1. S. Van Dongen, « Graph Clustering Via a Discrete Uncoupling Process », SIAM J. Matrix Anal. Appl., vol. 30, no 1, p. 121‑141, janv. 2008, doi: [10.1137/040608635](https://doi.org/10.1137/040608635).

2. A. J. Enright, S. Van Dongen, et C. A. Ouzounis, « An efficient algorithm for large-scale detection of protein families », Nucleic Acids Research, vol. 30, no 7, p. 1575‑1584, avr. 2002, doi: [10.1093/nar/30.7.1575](https://doi.org/10.1093/nar/30.7.1575).

3.	S. van Dongen et C. Abreu-Goodger, « Using MCL to Extract Clusters from Networks », in Bacterial Molecular Networks: Methods and Protocols, J. van Helden, A. Toussaint, et D. Thieffry, Éd., New York, NY: Springer, 2012, p. 281‑295. doi: [10.1007/978-1-61779-361-5_15](https://doi.org/10.1007/978-1-61779-361-5_15).