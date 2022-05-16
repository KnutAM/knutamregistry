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

## Update a package
The standard way to update a package, is to use the method described above when adding a package. 
However, this requires to increment the version number. If this is not desired (for some reason),
delete the entry under [packages] in `Registry.toml` along with the corresponding folder. Then add again
