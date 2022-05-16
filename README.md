# knutamregistry

Registry of my ongoing projects for simplified management.

## Add this registry
```julia
] registry add git@github.com:KnutAM/knutamregistry.git
```

## Add a package
After having added this registry with name `knutamregistry`, 
do the following in a temporary environment (`] activate --temp`)
```julia
using Pkg
Pkg.add("LocalRegistry")
Pkg.develop(url="https://github.com/<user>/MyPackage.jl")
using LocalRegistry, MyPackage
register(MyPackage, registry="knutamregistry")
```
