---
title:  Kısayollar
layout: default
parent: Ek Araçlar
---

# Kısa yollar

.bashrc yada eğer kullanıyorsanpız .zshrc içine aşağıdakiler eklenir. 

```
alias a='alias'
alias k='kubectl '
alias ka='kubectl apply -f '
alias kg='kubectl get '
alias kgn='kubectl get nodes'
alias kgnw='kubectl get nodes -o wide'
alias kgnl='kubectl get nodes --show-labels'
alias kgp='kubectl get pods'
alias kgs='kubectl get svc'
alias kgd='kubectl get deployments'
alias kcf='kubectl create -f '
alias kd='kubectl delete '
alias kdf='kubectl delete -f '
alias kaf='kubectl apply -f '
alias kgpa='kubectl get pods --all-namespaces'
alias kubens='function __kubens() { kubectl config set-context --current --namespace="$1"; }; __kubens'
```


Kaynaklar
* https://www.sfgroups.com/kubernetes/cluster_install/kubectl_bash_alias/
