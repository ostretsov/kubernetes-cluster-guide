Kubernetes and all mentioned software are evolving, fast paced environment, which means this guide will probably be outdated at times.

Be aware, that the following sections might be opinionated.

- Why Hetzner? Will this guide work for other providers?
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

Cloud providers: https://kubernetes.io/docs/setup/#production-environment

Buying nodes
============

Bying master node:
![Master node creation on Hetzner GIF](resources/gif/master_node_creation.gif)

- The `private` network we created makes intercommunication of nodes of the cluster secure. Otherwise, a VPN must be manually set up.
- Using SSH key is the most secure way of getting access to a node.

Following the same procedure we need to create at least two worker nodes in `private` network.

Initial node setup
=============

- timezone
- route?
- etcd
- docker
- kubernetes