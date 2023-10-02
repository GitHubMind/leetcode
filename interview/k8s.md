# k8s

__

base concept:

image:
+ pod
+ svc
+ ingress
+ pv
+ pvc
+ deployment

concept:
+ Cgroups
+ Namespace
+ Mount Namespace(Linux)






docker :
+ docker exec
+ docker container
+ docker volumes


Yaml Explain:
```yaml

  apiVersion: v1 //version
  kind: Pod      // type
  metadata:      //  store 
  annotations:
  scheduler.alpha.kubernetes.io/critical-pod: ""
  creationTimestamp: null
  labels:
  component: kube-apiserver
  tier: control-plane
  name: kube-apiserver
  namespace: kube-system
  spec:
  containers:
  - command:
  - kube-apiserver
  - --authorization-mode=Node,RBAC
  - --runtime-config=api/all=true
  - --advertise-address=10.168.0.2
  ...
  - --tls-cert-file=/etc/kubernetes/pki/apiserver.crt
  - --tls-private-key-file=/etc/kubernetes/pki/apiserver.key
  image: k8s.gcr.io/kube-apiserver-amd64:v1.11.1
  imagePullPolicy: IfNotPresent
  livenessProbe:
   ...
   name: kube-apiserver
   resources:
   requests:
   cpu: 250m
   volumeMounts:
   - mountPath: /usr/share/ca-certificates
   name: usr-share-ca-certificates
   readOnly: true
   ...t
   hostNetwork: true:
   priorityClassName: system-cluster-critical
   volumes:t
   - hostPath:c
   path: /etc/ca-certificates
   type: DirectoryOrCreatee
   name: etc-ca-certificates
   ...

```

