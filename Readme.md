# tectonic-kubernetes

Run a local instance of Kubernetes using CoreOS Tectonic, Vagrant and VirtualBox.

## Prequisites

- Docker
- Vagrant `https://www.vagrantup.com/downloads.html`
- VirtualBox `https://www.virtualbox.org/wiki/Downloads`

## Usage

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