MiniKube Installation : Virtual Box
=======================================

Let's learn how to install the latest Minikube release on Ubuntu Linux 18.04 LTS with VirtualBox v6.1 specifically.

- NOTE: For other Linux OS distributions or releases, VirtualBox and Minikube versions the installation steps may vary! Check the Minikube installation!


### Verify the virtualization support on your Linux OS (a non-empty output indicates supported virtualization):

```bash
$ grep -E --color 'vmx|svm' /proc/cpuinfo
```
### Install the VirtualBox hypervisor

Add the source repository for the bionic distribution (Ubuntu 18.04), download and register the public key, update and install:

```bash
$ sudo bash -c 'echo "deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian bionic contrib" >> /etc/apt/sources.list'

$ wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -

$ sudo apt update

$ sudo apt install -y virtualbox-6.1
```

### Install Minikube

We can download the latest release or a specific release from the Minikube release page. Once downloaded, we need to make it executable and add it to our PATH:

```bash
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```

- NOTE: Replacing /latest/ with a particular version, such as /v1.13.0/ will download that specified version. 

### Start Minikube
We can start Minikube with the minikube start command, that bootstraps a single-node cluster with the latest stable Kubernetes version release. For a specific Kubernetes version the --kubernetes-version option can be sued as such minikube start --kubernetes-version v1.19.0 (where latest is default and acceptable version value, and stable is also acceptable):

```Bash
$ minikube start

😄  minikube v1.13.1 on Ubuntu 18.04
✨  Automatically selected the virtualbox driver
💿  Downloading VM boot image ...
    > minikube-v1.13.1.iso.sha256: 65 B / 65 B [-------------] 100.00% ? p/s 0s
    > minikube-v1.13.1.iso: 173.91 MiB / 173.91 MiB [] 100.00% 26.59 MiB p/s 6s
👍  Starting control plane node minikube in cluster minikube
💾  Downloading Kubernetes v1.19.2 preload ...
    > preloaded-images-k8s-v6-v1.19.2-docker-overlay2-amd64.tar.lz4: 486.36 MiB
🔥  Creating virtualbox VM (CPUs=2, Memory=3900MB, Disk=20000MB) ...
🐳  Preparing Kubernetes v1.19.2 on Docker 19.03.12 ...
🔎  Verifying Kubernetes components...
🌟  Enabled addons: default-storageclass, storage-provisioner
💡  kubectl not found. If you need it, try: 'minikube kubectl -- get pods -A'
🏄  Done! kubectl is now configured to use "minikube" by default
```

### Check the status

With the minikube status command, we display the status of Minikube:

```bash
$ minikube status

minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

### Stop minikube

With the minikube stop command, we can stop Minikube:

```bash
$ minikube stop

Stopping node "minikube"  ...
1 nodes stopped.

```
