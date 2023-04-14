---
layout: default
title:  MicroK8s
parent: Kurulum
nav_order: 2
---

# microk8s

[Resmi Sitesi](https://microk8s.io/)

Canonical firmasının Kubernetes dağıtımıdır. 

##  linux için

```

 sudo snap install microk8s --classic
 
# kurulmasını bekliyoruz.
microk8s status --wait-ready

# normal kubectl kurulumu
snap install microk8s --classic

microk8s config > $HOME/.kube/config

kubectl get node

```

#### Kullanılabilir ek hizmetler.  (her sürümde değişiyor. )

```
microk8s status
microk8s is running
high-availability: no
  datastore master nodes: 127.0.0.1:19001
  datastore standby nodes: none
addons:
  enabled:
    dashboard            # (core) The Kubernetes dashboard
    dns                  # (core) CoreDNS
    ha-cluster           # (core) Configure high availability on the current node
    helm                 # (core) Helm - the package manager for Kubernetes
    helm3                # (core) Helm 3 - the package manager for Kubernetes
    hostpath-storage     # (core) Storage class; allocates storage from host directory
    metrics-server       # (core) K8s Metrics Server for API access to service metrics
    observability        # (core) A lightweight observability stack for logs, traces and metrics
    storage              # (core) Alias to hostpath-storage add-on, deprecated
  disabled:
    cert-manager         # (core) Cloud native certificate management
    community            # (core) The community addons repository
    gpu                  # (core) Automatic enablement of Nvidia CUDA
    host-access          # (core) Allow Pods connecting to Host services smoothly
    ingress              # (core) Ingress controller for external access
    kube-ovn             # (core) An advanced network fabric for Kubernetes
    mayastor             # (core) OpenEBS MayaStor
    metallb              # (core) Loadbalancer for your Kubernetes cluster
    minio                # (core) MinIO object storage
    prometheus           # (core) Prometheus operator for monitoring and logging
    rbac                 # (core) Role-Based Access Control for authorisation
    registry             # (core) Private image registry exposed on localhost:32000

```

####  komutlar

```
microk8s

Available subcommands are:
	add-node # 
	cilium # Another CNI
	config # kubeconfig'i ekrana basar. Alınıp dışarıdan kubectl ile bağlanmak için kullanılabilir.
	ctr # containerd client
	dashboard-proxy
	dbctl # backup and restore the Kubernetes datastore.
	disable 
	enable
	helm3
	helm
	istioctl # service mesh
	join
	juju
	kubectl
	leave # The node will depart from the cluster it is in.
	linkerd # service mesh
	refresh-certs #   Replace the CA certificates with the ca.crt and ca.key found in CA_DIR.
	remove-node
	reset
	start
	status
	stop 
	inspect # This script will inspect your microk8s installation. It will report any issue it finds,
and create a tarball of logs and traces which can be attached to an issue filed against
the microk8s project.


# istediğimiz servisleri etkinleştiriyoruz

# ideal ortamda çalışması gerekir 
microk8s enable dashboard dns 

# registry: kendi registryniz olsun isterseniz. 
microk8s enable registry


# dashboarda nodeport üzerinden erişmek için
kubectl -n kube-system patch svc kubernetes-dashboard --type='json' -p '[{"op":"replace","path":"/spec/type","value":"NodePort"}]'

# dashboard nodeportunu öğreniyoruz.

k describe svc kubernetes-dashboard -n kube-system | grep NodePort


# dashboarda erişim için aşağıdaki komuttan çıkan token'ı kullanıyoruz.
# supuruser token
kubectl -n kube-system describe secret microk8s-dashboard-token

```

#### yeni node eklemek

```

microk8s add-node

# çıkan komutu diğer nodlarda microk8s kurduktan sonra çalıştırın

```
