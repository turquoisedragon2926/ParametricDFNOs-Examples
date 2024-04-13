# ParametricDFNOs-Examples

This is a simple copy of `https://github.com/slimgroup/ParametericDFNOs.jl/tree/master/examples` to facilitate frictionless reproducibility.

To get started:

```shell
git clone https://github.com/turquoisedragon2926/ParametricDFNOs-Examples.git
cd ParametricDFNOs-Examples
```

Initialize by running the following in a julia REPL:

```julia
julia> ]
(v1.9) activate .
(ParametricDFNOs-Examples) instantiate
```

## Non distributed:

You can run the serial programs by doing:

### FFT of 3D Tensor
```shell
julia --project=./ 3D_FFT.jl
```

### Parametrized Convolution on 3D Tensor
```shell
julia --project=./ 3D_Conv.jl
```

Assuming you have a HPC cluster with [slurm](https://slurm.schedmd.com/documentation.html) set up, allocate some GPUs:

```shell
salloc --gpus=NTASKS --time=01:00:00 --ntasks=NTASKS --gpus-per-task=1 --gpu-bind=none
```

Now run any of the distributed examples:


### Distributed FFT of a 3D Tensor
```shell
julia --project=./ 3D_DFFT.jl
```

### Distributed Parametrized Convolution of a 3D Tensor
```shell
julia --project=./ 3D_DConv.jl
```