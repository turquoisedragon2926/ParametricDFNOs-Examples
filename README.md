# ParametricDFNOs-Examples

This is a copy of the [`examples`](https://github.com/slimgroup/ParametricOperators.jl/tree/master/examples) directory of [`ParametricOperators.jl`](https://slimgroup.github.io/ParametricOperators.jl) to facilitate frictionless reproducibility.

To get started:

```shell
git clone https://github.com/turquoisedragon2926/ParametricOperators-Examples.git
cd ParametricOperators-Examples
```

Initialize by running the following in a julia REPL:

```julia
julia> ]
(v1.9) activate .
(ParametricOperators-Examples) instantiate
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

> [!WARNING]  
> Your `salloc` might look different based on your HPC cluster.

Now run any of the distributed examples:

### Distributed FFT of a 3D Tensor
```shell
julia --project=./ 3D_DFFT.jl
```

### Distributed Parametrized Convolution of a 3D Tensor
```shell
julia --project=./ 3D_DConv.jl
```