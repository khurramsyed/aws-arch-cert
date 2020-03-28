

#Getting Started With Kubernetes (Minikube) on Mac

## Installing Minikube

### Check that Virtualization is Supported
sysctl -a | grep -E --color 'machdep.cpu.features|VMX'

### Ensure kubectl is installed

Make sure you have kubectl installed. You can install kubectl according to the instructions in Install and [Set Up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-macos), but I am putting it here as well.

- Download kubectl
~~~
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl"
~~~
- Make the binary executable
~~~
chmod +x ./kubectl
~~~
- Move the binary in to your PATH.
~~~
sudo mv ./kubectl /usr/local/bin/kubectl
~~~
- Start Minikube
~~~
minikube start
~~~
This will create following out as driver is not specified.
~~~
😄  minikube v1.5.2 on Darwin 10.15.1
✨  Automatically selected the '' driver
💣  Unable to determine a default driver to use. Try specifying --vm-driver, or see https://minikube.sigs.k8s.io/docs/start/
~~~
You can check the list of drivers that you can use from [here](https://minikube.sigs.k8s.io/docs/reference/drivers/). I had docker installed on my machine which comes with hyperkit so used hyperkit driver.
~~~
minikube start --vm-driver=hyperkit
~~~
You can start minikube using following command now.

- To make hyperkit the default driver:
~~~
minikube config set vm-driver hyperkit
~~~
You should see followng output.
~~~
😄  minikube v1.5.2 on Darwin 10.15.1
💾  Downloading driver docker-machine-driver-hyperkit:
    > docker-machine-driver-hyperkit.sha256: 65 B / 65 B [---] 100.00% ? p/s 0s
    > docker-machine-driver-hyperkit: 10.79 MiB / 10.79 MiB  100.00% 2.61 MiB p
🔑  The 'hyperkit' driver requires elevated permissions. The following commands will be executed:

    $ sudo chown root:wheel /Users/khurram/.minikube/bin/docker-machine-driver-hyperkit
    $ sudo chmod u+s /Users/khurram/.minikube/bin/docker-machine-driver-hyperkit
Password:
🔥  Creating hyperkit VM (CPUs=2, Memory=2000MB, Disk=20000MB) ...
🐳  Preparing Kubernetes v1.16.2 on Docker '18.09.9' ...
💾  Downloading kubeadm v1.16.2
💾  Downloading kubelet v1.16.2
🚜  Pulling images ...
🚀  Launching Kubernetes ...
⌛  Waiting for: apiserver
🏄  Done! kubectl is now configured to use "minikube"
~~~
