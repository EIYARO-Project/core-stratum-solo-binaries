# Stratum Solo Binaries
Binaries for the stratum server for solo GPU mining

> **IMPORTANT**
> This is a stratum server for solo `GPU` mining.
>
> This needs to reside on the same machine as the node it is attaching.
>
> Since this is an alfa release, it will not take into account the address you put on `t-rex`.
> The account/address of the node, itself, will be the one getting the rewards.

## Installing

Download the binaries on the [releases](releases/latest).

Inside that arquive is the executable binary and a suggest `prod.yml` file that configures the stratum server.

## Running

```console
$ eiyarostratum -config prod.yml
```