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
] add FerriteProblems
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
