# knutamregistry

Registry of my ongoing projects for simplified management.

## Add this registry
```julia
] registry add git@github.com:KnutAM/knutamregistry.git
```

## Add a package
After having added this registry with name `knutamregistry` 
```julia
using LocalRegistry
register(package, registry=knutamregistry)
```
