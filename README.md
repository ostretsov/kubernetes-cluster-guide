Kubernetes and all mentioned software are evolving, fast paced environment, which means this guide will probably be outdated at times.

Be aware, that the following sections might be opinionated.

- Why Hetzner?
- Ascetic cluster setup.
- Master & worker nodes.
- kubectl + zsh & Web UI (Dashboard).
- Monitoring with Prometheus & Grafana.
- Logging with fluent-bit & Graylog.


Why Hetzner?
============

- Cheap.
- Reliable.
- Company's track record. 

Doesn't have data centers in USA/Canada. 

Other cloud providers: https://kubernetes.io/docs/setup/#production-environment

Buying nodes
============

Bying master node:
![Master node creation on Hetzner GIF](resources/gif/master_node_creation.gif)

- The `private` network we created makes intercommunication of nodes of the cluster secure. Otherwise, a VPN must be manually set up.
- Using SSH key is the most secure way of getting access to a node.

Following the same procedure we need to create at least two worker nodes in `private` network.

Initial node setup
=============

On each node there must be at least Docker engine and Kubernetes being installed. 

```console
$ ssh root@x.x.x.x
# timedatectl set-timezone America/New_York # sets node timezone if needed
#  
# ### Installing Docker
# # Up-to-date installation instructions are available at https://docs.docker.com/install/linux/docker-ce/ubuntu/
# apt-get install \
      apt-transport-https \
      ca-certificates \
      curl \
      gnupg-agent \
      software-properties-common
# curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
# add-apt-repository \
     "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
     $(lsb_release -cs) \
     stable"
# apt-get install docker-ce docker-ce-cli containerd.io
#
# ### Installing kubernetes
```
- route?
- etcd
- docker
- kubernetes

etcd
====

In a nutshell, etcd is a distributed database which stores actual and desired states of your Kubernetes cluster. 
For minimal durability there should be at least 3 etcd cluster members. 
It worth nothing to do such configuration:
