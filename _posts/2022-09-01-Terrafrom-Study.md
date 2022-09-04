---
layout: post
title: Kubernetes Env. Setup
subtitle: (Studying K8s in "A Cloud Guru" VMs)
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/k8s.png
share-img: /assets/img/path.jpg
tags: [kubernetes, cloud]
---

```bash
# Add the K8s Repo GPG Key
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -

# Add K8s Repo
cat << EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF

# Update apt sources list
sudo apt-get update

# Install our Packages
sudo apt-get install -y kubelet=1.15.7-00 kubeadm=1.15.7-00 kubectl=1.15.7-00

# Prevent Auto-Updates for Kube Packages
sudo apt-mark hold kubelet kubeadm kubectl

# Verify Installation
kubeadm version
```

```bash
# Initialize the cluster on the Kube Master server
sudo kubeadm init --pod-network-cidr=10.244.0.0/16

# Set up the Local kubeconfig
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```
