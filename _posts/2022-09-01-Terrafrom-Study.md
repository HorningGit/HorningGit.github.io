---
layout: post
title: Kubernetes Env. Setup
subtitle: (Studying K8s in "A Cloud Guru" VMs)
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/k8s.png
share-img: /assets/img/path.jpg
tags: [kubernetes, cloud]
---

## Bootstrapping my Cluster (Master Node)
```bash
# Initialize the cluster on the Kube Master server
sudo kubeadm init --pod-network-cidr=10.244.0.0/16

# Set up the Local kubeconfig
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

## Bootstrapping my Cluster (Worker Nodes)
```bash
# kubeadm init command outputted a kubeadm join command with our token/hash
# We'll run this command on the worker nodesIt should look something like this:
sudo kubeadm join $some_ip:6443 --token $some_token --discovery-token-ca-cert-hash $some_hash

sudo kubeadm join <IP_ADDRESS> --token <TOKEN> \
    --discovery-token-ca-cert-hash sha256:<HASH>
```

