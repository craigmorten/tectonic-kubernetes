# tectonic-kubernetes

Run a local instance of Kubernetes using CoreOS Tectonic, Vagrant and VirtualBox.

## Prequisites

- Docker [https://docs.docker.com/engine/installation/#supported-platforms](https://docs.docker.com/engine/installation/#supported-platforms)
- Vagrant [https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html)
- VirtualBox [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

## Usage

Ensure you have execute permissions:

```sh
chmod +x tectonic
```

Use the command as so:

```sh
tectonic [subcommand]
```

List of optional subcommands:

- start
- destroy
- pause
- kick
- config

If no subcommand is provided, the start subcommand will be implemented
by default.
