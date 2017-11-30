# tectonic-kubernetes

Run a local instance of Kubernetes using CoreOS Tectonic, Vagrant and VirtualBox.

## Prequisites

- Docker [https://docs.docker.com/engine/installation/#supported-platforms](https://docs.docker.com/engine/installation/#supported-platforms)
- Vagrant [https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html)
- VirtualBox [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
- openssl
- At least 4GB of RAM

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

## Overview of start script

1. Install kubectl cli
1. Ensure Vagrant installed
1. Ensure openssl can be used by Vagrant
1. Ensure that VirtualBox is installed
1. Start Vagrant
1. Configure kubectl
1. Install helm (see [https://github.com/kubernetes/helm](https://github.com/kubernetes/helm))
1. Install helm charts (in this case, only prometheus)

## What can I do...?

1. Once up and running, you can view the Tectonic UI at [https://console.tectonicsandbox.com/](https://console.tectonicsandbox.com/). This shows all deployments, pods, secrets, services etc.
1. View the prometheus UI at [prometheus.ingress.tectonicsandbox.com](prometheus.ingress.tectonicsandbox.com). Prometheus is a metrics management, graphing and alerting tool, see the website [https://prometheus.io/](https://prometheus.io/).
1. Play with the `kubectl` cli, see the cheat sheet [https://kubernetes.io/docs/reference/kubectl/cheatsheet/](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
1. Develop your own application, write charts for it, and deploy with helm to your cluster!
