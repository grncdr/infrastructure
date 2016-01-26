# Solarnet

This is the all-new code for provisioning of the ipfs.io infrastructure.
We abandoned the weight and complexity of Ansible,
and are now using plain shell scripts, with the help of [Provsn][provsn].

```sh
$ ./provsn build && ./provsn upload && ./provsn install
```



Dead-simple infrastructure provisioning in ~100 lines of bash.
`provsn` is a self-contained shell script which operates

Provsn uses plain shell scripts to:
- generate host and service configuration
- upload configuration to hosts
- install changes to hosts and services

An infrastructure project using Provsn comes with multiple units,
each consisting of:
- an `env.sh` file with variable (mandatory)
- executable scripts like `build.sh`, `install.sh`, `foobar.sh`
- arbitrary other files

Provsn operates on a project directory
which contains at the very least a `provsn.sh` file, the *root unit*.
Each subdirectory of arbitrary depth with a `provsn.sh` file is a *unit*.


TODO
- [x] multiplexing proxy / multireq
- [ ] ipfs.io wiring
- [x] run arbitrary scripts (build, install, foobar)
- [x] upload units and provsn itself
- [x] prepare a complete tree for upload (1 scp call per host)
- [x] proper commands
- [x] groups
- [ ] error handling
- [ ] multissh and screen
- [ ] maybe: json return values
- [x] handle secrets
- [ ] make sure hosts have up-to-date build tree


### Dependencies

On both local and remote machines:

- realpath git jq
