+++
title = "Installing Bionic"
weight = 30
sort_by = "weight"
+++

## Step 0: Setup

Before anything else, we need to ensure you have access to modern Kubernetes cluster and a functioning kubectl command on your local machine. (If you don’t already have a Kubernetes cluster, one easy option is to run one on your local machine. There are many ways to do this, including kind, k3d, Docker for Desktop, and more.)

Validate your Kubernetes setup by running:

```sh
kubectl version
```
The bionic installer is a bash script that simplifies a lot of the setup. To install it run the following.

## Step 1: Install the CLI

```sh
curl -OL https://github.com/bionic-gpt/bionic-gpt/releases/latest/download/bionic-linux-amd64 && mkdir -p $HOME/.bionic && mv ./bionic-linux-amd64 $HOME/.bionic/bionic && chmod +x $HOME/.bionic/bionic
```

Be sure to follow the instructions to add it to your path:

```sh
export PATH=$HOME/.bionic:$PATH
```

Check the installation

```sh
bionic -V
# k8s-operator 1.6.26
```

## Step 2: Run the Install

The following will install `k3s` as our kubernetes engine and then install bionic into the cluster. It will also install `k9s` which is a terminal UI for Kubernetes.

```sh
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
bionic install
```

## Step 3: The Finished Result

```sh
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
k9s
```

After a while of container creation you should see all the pods running and then be able to access Bionic.


![Alt text](../bionic-startup-k9s.png "Bionic K9s")

## Step 4: Run the User Interface

You can then access the front end from `http://localhost` and you'll be redirected to a registration screen.

## Step 5: Registration

The first user to register with **BionicGPT** will become the system administrator. The information is kept local to your machine and your data is not sent anywhere.

![Alt text](../initial-screen.png "Start Screen")