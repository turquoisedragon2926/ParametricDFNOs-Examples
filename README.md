# ParametricOperators.jl-Examples

This is a copy of the [`examples`](https://github.com/slimgroup/ParametricOperators.jl/tree/master/examples) directory of [`ParametricOperators.jl`](https://slimgroup.github.io/ParametricOperators.jl) to facilitate frictionless reproducibility.

To get started:

```shell
git clone https://github.com/turquoisedragon2926/ParametricOperators.jl-Examples.git
cd ParametricOperators.jl-Examples
```

Initialize the dependencies by running the following in a julia REPL:

```julia
julia> ]
(v1.9) activate .
(ParametricOperators.jl-Examples) instantiate
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

## Distributed:

> [!WARNING]  
> Make sure to have a proper MPI distribution loaded.

If you have [`mpiexecjl`](https://juliaparallel.org/MPI.jl/stable/usage/#Installation) set up, you can do:

```shell
# To run the 3D FFT example
mpiexecjl --project=./ -n NTASKS julia 3D_DFFT.jl

# To run the 3D convolution example
mpiexecjl --project=./ -n NTASKS julia 3D_DConv.jl
```

OR if you have a HPC cluster with [`slurm`](https://slurm.schedmd.com/documentation.html) set up, you can do:

```shell
salloc --gpus=NTASKS --time=01:00:00 --ntasks=NTASKS --gpus-per-task=1 --gpu-bind=none
```

> [!WARNING]  
> Your `salloc` might look different based on your HPC cluster.

Now run any of the distributed examples:

### Distributed FFT of a 3D Tensor
```shell
srun julia --project=./ 3D_DFFT.jl
```

### Distributed Parametrized Convolution of a 3D Tensor
```shell
srun julia --project=./ 3D_DConv.jl
```
