# ngc-pytorch-cyverse
PyTorch deep learning Singularity container from NVIDIA NGC, with a few extra python libraries and Jupyter.

This repo contains the the instructions to build a Singularity container from NVIDIA NGC's deep learning pytorch docker container. In addition to the base contents, this container also includes the `fastai` package and runs jupyter notebook.

## Build and Use
To build, use Singularity's `build` command using the recipe file.

To run:

`singularity exec --nv --bind $PWD:/run/user ngc-pytorch-cyverse.sif jupyter notebook --ip=calliope.cyverse.org --allow-root --port=8888 --no-browser`

## Note

The build and instructions are designed for me and Tyson. Before use, inspect the recipe file and instructions and make changes to make your needs.
