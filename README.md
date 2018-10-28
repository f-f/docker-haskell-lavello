# docker-haskell-lavello

🚰 Kitchen-sink docker image for building (stack-based) Haskell projects in CI

IPA: *//laˈvɛllo/*

![lavello](http://img.archiexpo.it/images_ae/photo-g/134-6497057.jpg)

## Where to find this

Docker tags:
- lts-12: `nilrecurring/haskell-lavello:lts-12`

## FAQ

> Wait, don't we have `fpco/stack-build` already?

Yees, and in fact that's our base image.  
Additionally we also `stack build` a whole list of packages, so that when you get to build your project they don't have to be recompiled, dramatically cutting CI time.

> So why isn't this the standard?

The tradeoff here is the bandwidth: the image is quite big (> 1GB), so fetching it from your favorite CI might take some time (especially if you don't cache Docker images).  
Doing this with Haskell is convenient, because compiling things on free-CI CPUs usually takes more time than fetching the already compiled package (YMMV, you'll have to benchmark this with your setup)
