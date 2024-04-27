# Stratum Solo Binaries

[![Supports Windows](https://img.shields.io/badge/support-Windows-blue?logo=Windows)](https://github.com/EIYARO-Project/core-stratum-solo-binaries/releases/latest)
[![Supports Linux](https://img.shields.io/badge/support-Linux-yellow?logo=Linux)](https://github.com/EIYARO-Project/core-stratum-solo-binaries/releases/latest)
[![License](https://img.shields.io/github/license/EIYARO-Project/core)](https://github.com/EIYARO-Project/core-stratum-solo-binaries/blob/master/LICENSE)
[![Latest Release](https://img.shields.io/github/v/release/EIYARO-Project/core-stratum-solo-binaries?label=latest%20release)](https://github.com/EIYARO-Project/core-stratum-solo-binaries/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/EIYARO-Project/core-stratum-solo-binaries/total)](https://github.com/EIYARO-Project/core-stratum-solo-binaries/releases)


Binaries for the stratum server for solo GPU mining.

> **IMPORTANT**
> This is a stratum server for solo `GPU` mining.
>
> This needs to reside on the same machine as the node it is attaching.
>
> Since this is an alfa release, it will not take into account the address you put on `t-rex`.
> The account/address of the node, itself, will be the one getting the rewards.

## Installing the stratum server

Download the binaries on the [releases](https://github.com/EIYARO-Project/core-stratum-solo-binaries/releases).

Inside that arquive is the executable binary and a suggest `prod.yml` file that configures the stratum server.

`prod.yml` file:
```yaml
mode: prod

# server
stratum.id: 0
stratum.port: 9119
stratum.max_conn: 32768
stratum.default_ban_period: 20m # 0s means disable

# session
session_timeout: 5m
session.sched_interval: 0
session.diff: 1050000

# node
node.url: http://127.0.0.1:9888
node.name: eiayro_mainnet
node.sync_interval: 100ms

service.port: 11002
```

## Running the stratum server

```console
$ eiyarostratum -config prod.yml
```

## Miner

The only miner that supports our `tensority` algorithm is [t-rex](https://github.com/trexminer/T-Rex).

Suggested script:
```bash
#!/bin/bash

USER=SomeAddress-Doesnt_really_matter_for_now
URL=stratum+tcp://127.0.0.1:9119
ALGO=tensority
COIN=EIYARO
WORKSTATION=MyAwesomeWorkStation

t-rex -a ${ALGO} -o ${URL} -u ${USER} --coin ${COIN} -w ${WORKSTATION}
```