# knutamregistry

Registry of my ongoing projects for simplified management.

## Add this registry
Using `https` (if only public repos will be used)
```julia
] registry add https://github.com/KnutAM/knutamregistry.git
```
Using `ssh` (if also private repos are used)
```julia
] registry add git@github.com:KnutAM/knutamregistry.git
```

## Using this registry
After adding the registry as described above (once on your computer),
you can use the packages in this registry as if they were in the 
General registry. For example,
```julia
] add FerriteAssembly
```

## Add a package
### With `LocalRegistry.jl` in your global environment
Go to the folder where you are developing the package
```julia
] activate . # Activate the package
using LocalRegistry
register(; registry="knutamregistry") # kwarg only needed if you have multiple local regististries
```
### Without `LocalRegistry.jl` in global environment
After having added this registry with name `knutamregistry`, 
do the following in a temporary environment (`] activate --temp`)
```julia
using Pkg
Pkg.add("LocalRegistry")
Pkg.develop(url="https://github.com/<user>/MyPackage.jl")
using LocalRegistry, MyPackage
register(MyPackage, registry="knutamregistry")
```

## Update a package
The standard way to update a package, is to use the method described above when adding a package. 
However, this requires to increment the version number. If this is not desired (for some reason),
delete the entry under [packages] in `Registry.toml` along with the corresponding folder. Then add again

## SSH keys
Currently (2025-05-12), the best way to generate ssh keys that works with both julia and github seems to be
```
ssh-keygen -t ecdsa -C "<your email address>"
```
and adding `SSH_PUB_KEY_PATH` and `SSH_KEY_PATH` to the environment,
either in bashrc/zshrc, or via `startup.jl`.
Based on this [post](https://discourse.julialang.org/t/local-registry-rsa-key-problem/78188/5)
