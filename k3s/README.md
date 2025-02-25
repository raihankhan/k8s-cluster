### Install a k3s cluster

Install it as a service on systemd:
```bash
curl -sfL https://get.k3s.io | sh -
```

Get the kubeconfig:
`cat /etc/rancher/k3s/k3s.yaml`

#### Join an agent node from a different machine

```bash
curl -sfL https://get.k3s.io | K3S_URL=https://myserver:6443 K3S_TOKEN=mynodetoken sh -

```

Get the server node token from
`cat /var/lib/rancher/k3s/server/node-token`

#### [HA server nodes with embedded etcd](https://docs.k3s.io/datastore/ha-embedded)

#### [HA with external DB](https://docs.k3s.io/datastore/ha)

#### Uninstall k3s server
```bash
/usr/local/bin/k3s-uninstall.sh
```

#### [Architecture](https://docs.k3s.io/architecture)
- A server node is defined as a host running the k3s server command, with control-plane and datastore components managed by K3s.
- An agent node is defined as a host running the k3s agent command, without any datastore or control-plane components.
- Both servers and agents run the kubelet, container runtime, and CNI. See the Advanced Options documentation for more information on running agentless servers.

![img.png](https://docs.k3s.io/assets/images/how-it-works-k3s-revised-9c025ef482404bca2e53a89a0ba7a3c5.svg)