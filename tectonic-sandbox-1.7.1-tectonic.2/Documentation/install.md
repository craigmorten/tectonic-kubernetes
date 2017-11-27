# Installing Tectonic Sandbox

Tectonic Sandbox provides a quick and easy demonstration of Tectonic clusters and Tectonic Console. Use the Sandbox to quickly spin up a cluster, then manage the demo using Tectonic Console.

CoreOS Tectonic Sandbox runs on your laptop without external dependencies.

Tectonic Sandbox is not meant for production use cases. It's designed to be a simple, lightweight installation, and is not meant to deploy production ready clusters.

## Installation Requirements

* [Vagrant by HashiCorp][vagrant] installed and enabled.
* [Oracle VM VirtualBox][virtualbox] installed and enabled.
* A current version of Google Chrome, Internet Explorer, or Mozilla Firefox installed and running.
* 8 GB of RAM

Ensure that the latest versions of Vagrant and VirtualBox are installed on your local machine.

Download Tectonic Sandbox from https://releases.tectonic.com/sandbox/tectonic-sandbox-1.7.0-tectonic.1.zip.

## Windows Installation

Hyper-V conflicts with VirtualBox, and must be disabled before launching Tectonic Sandbox.

**Docker for Windows** uses Hyper-V to run a Linux kernel. If Docker for Windows is installed, you must first disable Docker, then disable Hyper-V before launching Tectonic Sandbox. A reboot is required to enable or disable Hyper-V.

First, disable Docker.

Then, disable Hyper-V:

```
bcdedit /set hypervisorlaunchtype off
```

Download and unzip [Tectonic Sandbox][sandbox-download].

Open a powershell and run:

```
cd Downloads...
vagrant up --provider=virtualbox
```

To re-enable Hyper-V after exploring Tectonic Sandbox, run:

```
bcdedit /set hypervisorlaunchtype auto
```

## OSX Installation

Download and unzip [Tectonic Sandbox][sandbox-download].

Open a terminal and run:

```
cd Downloads...
vagrant up --provider=virtualbox
```

Watch Sandbox install, and spin up your cluster. This should take 20-40 minutes, depending on your connection. When complete, follow the instructions provided in the terminal to log in to the Console.
* Log in to your cluster using the Console URL displayed in the terminal. If you receive an error page saying that the connection is not private, click **Advanced**, then **Proceed** to log in.
* Enter the username and password provided, and click **Log In**.

## Linux Installation

Download and unzip [Tectonic Sandbox][sandbox-download].

Open a terminal and run:

```
cd Downloads...
vagrant up --provider=virtualbox
```

## Debugging

Q: My console doesn't work!

A: There are a few common problems that might prevent Tectonic Console from launching. Use these suggestions to try and resolve the issue.

First, confirm that you are using one of the supported browsers: Google Chrome, Mozilla Firefox, or Internet Explorer. Other browsers may not work with Tectonic Sandbox.

If you are using one of these browsers, try to resolve the Console on the local worker machine:

```
vagrant ssh w1
curl https://console.tectonicsandbox.com/
```

If that is failing, see if there is anything listening on that port

```
vagrant ssh w1
netstat -nl | grep 443
```

If this doesn’t work, please wait five minutes, then rerun the commands. It can take some time for Kubernetes to resolve the request. If the Console is still unavailable, file an issue in the [Tectonic Sandbox GitHub repo][sandbox-repo].

Q: It’s been 20 minutes and my cluster still isn't coming up!

A: We know it is annoying but please wait 10 more minutes to file an issue. The installation must download 2GB+ of data between CoreOS Container Linux images and the required container images for Tectonic. A download of this size may take quite some time.

Q: I got a configuration error regarding `VagrantPlugins::Ignition::Config:`

A: You are running an older version of the vagrant-ignition plugin. Update the plugin using this command:

```
vagrant plugin update vagrant-ignition
```

Q: I got this error: `==> c1: Failed to start tectonic.service: Unit tectonic.service not found.`

A: You may be running a version of the vagrant image which does not support Ignition.

To fix this, first, use `vagrant destroy` to remove the machines created during installation:

```
vagrant destroy -f
```

Then, remove the old boxes:

```
vagrant box remove coreos-beta --all --provider=virtualbox
```

Q: How do I view the Console?

A: Navigate to https://console.tectonicsandbox.com in your browser.

Q: How do I log in to the Console?

A: First, click through the "Your connection is not private" warning page. Click **Advanced**, and then **Proceed**. Then, enter user: “admin@example.com”, and password: “sandbox” to launch Tectonic Console.

Q: How do I use kubectl?

A: To use kubectl with the cluster, set the environment variable listed at the end of the `vagrant up` instructions.

On macOS or Linux, run:

```
export KUBECONFIG=$PWD/provisioning/etc/kubernetes/kubeconfig
```

On Windows, run:

```
$env:KUBECONFIG = "$PWD\provisioning\etc\kubernetes\kubeconfig"
```


[vagrant]: https://www.vagrantup.com/downloads.html
[virtualbox]: https://www.virtualbox.org/wiki/Downloads
[sandbox-download]: https://releases.tectonic.com/sandbox/tectonic-sandbox-1.7.0-tectonic.1.zip
[sandbox-repo]: https://github.com/coreos-inc/tectonic-sandbox
