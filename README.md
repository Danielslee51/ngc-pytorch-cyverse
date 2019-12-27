# ngc-pytorch-cyverse
PyTorch deep learning Singularity container from NVIDIA NGC, with a few extra python libraries and Jupyter.

This repo contains the the instructions to build a Singularity container from NVIDIA NGC's deep learning pytorch docker container. In addition to the base contents, this container also includes the `fastai` package and runs jupyter notebook.

## Build and Use
To build, use Singularity's `build` command using the recipe file.

To run:

`singularity exec --nv --bind $PWD:/run/user ngc-pytorch-cyverse.sif jupyter notebook --ip=<your-public-ip> --allow-root --port=8888 --no-browser`

## To run in the UA HPC

To run in the University of Arizona's [HPC](https://it.arizona.edu/service/high-performance-computing) center, begin my logging in to ocelote and running an interactive job:

`qsub -I -N example_job -m bea -W group_list=group -q standard -l select=1:ncpus=28:mem=224gb:np100s=1 -l cput=28:0:0 -l walltime=1:0:0`

Here, we have selected one node, which includes 28 cpus and 1 gpu (`np100s=1`). We have asked for one hour of real time (`walltime=1:0:0`), which account for 28 hours of cpu time (`cput=28:0:0`), since there are 28 cpus.

To use the singularity container with GPUs, load singularity and cuda:

`module load singularity`

`module load cuda80/gdk/352.79`

Then, run  `jupyter on the container`.

`singularity exec --nv --bind $PWD:/run/user ngc-pytorch-cyverse.sif jupyter notebook --ip=0.0.0.0 --allow-root --port=8888 --no-browser`

(note to self: write about how to access it using VPN)

## Note

The build and instructions are designed for me and Tyson. Before use, inspect the recipe file and instructions and make changes to make your needs.
