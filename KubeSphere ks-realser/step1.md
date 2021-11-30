## Prerequisites
1.Check if there is a default Storage Class in your cluster.`kubectl get sc`{{execute}} 

> No storage Class found in the cluster

```bash
controlplane $ kubectl get sc 
No resources found in default namespace.
```

2.Install openebs storage Class in the cluster  
```
kubectl create namespace openebs
helm repo add openebs https://openebs.github.io/charts
helm repo update
helm install openebs --namespace openebs openebs/openebs --wait 
```{{execute}}

3.Set  openebs as  a default storage Class for the cluster
`kubectl patch storageclasses.storage.k8s.io openebs-hostpath -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'`{{execute}}

4.Check if there is a default Storage Class in your cluster.`kubectl get sc`{{execute}} 

## Installing ks-releaser with ServiceMonitor
1.First,install ks-releaser with kubectl :
`kubectl apply -f https://github.com/kubesphere-sigs/ks-releaser/releases/latest/download/install.yaml`{{execute}}


## Install CLI ks via hd
[hd](https://github.com/linuxsuren/http-downloader) is a HTTP download tool.
1.install hd
```
curl -L https://github.com/linuxsuren/http-downloader/releases/latest/download/hd-linux-amd64.tar.gz | tar xzv
mv hd /usr/bin/hd
```{{execute}}

2.Install it via 
`hd install kubesphere-sigs/ks`{{execute}}