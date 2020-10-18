# Installing Minikube on macOS


Let's learn how to install the latest Minikube release on Mac OS X with VirtualBox v6.1 specifically.

NOTE: For other VirtualBox and Minikube versions the installation steps may vary! Check the Minikube installation!

Verify the virtualization support on your macOS (VMX in the output indicates enabled virtualization):

$ sysctl -a | grep -E --color 'machdep.cpu.features|VMX'

Although VirtualBox is the default hypervisor for Minikube, on Mac OS X we can configure Minikube at startup to use another hypervisor (downloaded separately), with the --driver=parallels or --driver=hyperkit start option.

Install the VirtualBox hypervisor for 'OS X hosts'
Download and install the .dmg package.

Install Minikube
We can download the latest release or a specific release from the Minikube release page. Once downloaded, we need to make it executable and add it to our PATH:

$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/

NOTE: Replacing /latest/ with a particular version, such as /v1.13.0/ will download that specified version.

Start Minikube
We can start Minikube with the minikube start command, that bootstraps a single-node cluster with the latest stable Kubernetes version release. For a specific Kubernetes version the --kubernetes-version option can be sued as such minikube start --kubernetes-version v1.19.0 (where latest is default and acceptable version value, and stable is also acceptable):

$ minikube start

😄  minikube v1.13.1 on Darwin 10.15.6
✨  Automatically selected the virtualbox driver
💿  Downloading VM boot image ...
👍  Starting control plane node minikube in cluster minikube
💾  Downloading Kubernetes v1.19.2 preload ...
🔥  Creating virtualbox VM (CPUs=2, Memory=3900MB, Disk=20000MB) ...
🐳  Preparing Kubernetes v1.19.2 on Docker 19.03.12 ...
🔎  Verifying Kubernetes components...
🌟  Enabled addons: default-storageclass, storage-provisioner
💡  kubectl not found. If you need it, try: 'minikube kubectl -- get pods -A'
🏄  Done! kubectl is now configured to use "minikube" by default

Check the status
With the minikube status command, we display the status of Minikube:

$ minikube status

minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured

Stop minikube
With the minikube stop command, we can stop Minikube:

$ minikube stop

Stopping node "minikube"  ...
1 nodes stopped.

