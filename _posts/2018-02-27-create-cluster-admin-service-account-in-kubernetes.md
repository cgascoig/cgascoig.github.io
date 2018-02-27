---
layout: post
title: "TIL: How to create a cluster-admin service account in Kubernetes"
category: til
tags: [kubernetes]
---
Depending on how you deployed a Kubernetes cluster, you may or may not have a service account with cluster-admin rights. These steps will create one. (Note: this is not necessarily what you should do in a production deployment)

### Create the service account
```
kubectl create serviceaccount myroot
```
> output

```
serviceaccount "myroot" created
```

### Create the role binding
```
kubectl create clusterrolebinding myroot-cluster-admin --clusterrole=cluster-admin --serviceaccount=default:myroot
```

> output

```
clusterrolebinding "myroot-cluster-admin" created
```

### Describe the service account to find the token ID
```
kubectl describe serviceaccount myroot
```

> output

```
Name:                myroot
Namespace:           default
Labels:              <none>
Annotations:         <none>
Image pull secrets:  <none>
Mountable secrets:   myroot-token-dzqvn
Tokens:              myroot-token-dzqvn
Events:              <none>
```

### Get the token secret
```
kubectl describe secret myroot-token-dzqvn
```
> output

```
Name:         myroot-token-dzqvn
Namespace:    default
Labels:       <none>
Annotations:  kubernetes.io/service-account.name=myroot
              kubernetes.io/service-account.uid=37bd952c-1b8e-11e8-9faa-005056bf340f

Type:  kubernetes.io/service-account-token

Data
====
ca.crt:     1025 bytes
namespace:  7 bytes
token:      <TOKEN>
```