# Managing Kubernetes applications

Command line syntax to manage your Kubernetes applications:

wordslab *app* : Manage kubernetes applications in your virtual machines

## Download applications

wordslab **app info** [url] : Show detailed information about a kubernetes app from its URL
- [url] : Kubernetes app URL

Example application URL for the "notebooks" built-in app : 
- https://raw.githubusercontent.com/wordslab-org/wordslab/main/wordslab.manager/apps/notebooks/wordslab-notebooks-gpu-app.yaml

wordslab **app download** [vm] [url] : Download a new kubernetes app in a running virtual machine
- [vm] : Virtual machine name
- [url] : Kubernetes app URL

wordslab **app list** [vm] : List all kubernetes apps downloaded in a running virtual machine
- [vm] : Virtual machine name

wordslab **app remove** [vm] [ID] : Remove all files previously downloaded for a kubernetes app in a vm
- [vm] : Virtual machine name
- [ID] : Kubernetes app ID (selected in the output of the app list command)

## Deploy applications

wordslab *app deployment* : Manage kubernetes app deployments in your virtual machines

wordslab **app deployment list** [vm] : List all kubernetes app deployments in a running virtual machine
- [vm] : Virtual machine name

wordslab **app deployment create** [vm] [ID] : Deploy a previoulsy downloaded kubernetes app in a running virtual machine
- [vm] : Virtual machine name
- [ID] : Kubernetes app ID (selected in the output of the app list command)

wordslab **app deployment stop** [vm] [namespace] : Temporarily free CPU and memory resources allocated to a kubernetes app deployment
- [vm] : Virtual machine name
- [namespace] : Kubernetes app deployment namespace

wordslab **app deployment start** [vm] [namespace] : Restart a previously stopped kubernetes app deployment in a running virtual machine
- [vm] : Virtual machine name
- [namespace] : Kubernetes app deployment namespace

wordslab **app deployment delete** [vm] [namespace] : Delete a kubernetes app deployment in a running virtual machine
- [vm] : Virtual machine name
- [namespace] : Kubernetes app deployment namespace

## Example wordslab Kubernetes app syntax :

Extract of a valid yaml file for a wordslab Kubernetes app:

```
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: wordslab-notebooks-ingressroute
  labels:
    wordslab.org/app: wordslab-notebooks
    wordslab.org/component: jupyterlab
  annotations:
    wordslab.org/namespace-default: "notebooks"
    wordslab.org/title: "Jupyterlab notebooks (GPU)"
    wordslab.org/description: "Ubuntu 22.04, Cuda 12.2, Python 3.10, Pytorch 2.0 / Tensorflow 2.13 / JAX 0.4 / scikit-learn 0.23, Jupyterlab 3.6"
    wordslab.org/version: "jupyterlab-3.6.5-lambda-0.1.14-22.04.1_2"
    wordslab.org/date: "09/17/2023"
    wordslab.org/homepage: "https://www.wordslab.org/"
    wordslab.org/source: "https://github.com/wordslab-org/wordslab/tree/main/wordslab.manager/apps/notebooks/wordslab-notebooks-gpu-app.yaml"
    wordslab.org/author: "https://github.com/wordslab-org"
    wordslab.org/license: "Apache License Version 2.0"
    wordslab.org/ingressroute-path: "/lab | Jupyterlab"
    wordslab.org/ingressroute-path1: "/gradio | Web interface (port 7860)"
    wordslab.org/ingressroute-path2: "/fastapi | API endpoint (port 8000)"
spec:
  entryPoints:
    - web
  routes:
  - match: PathPrefix(`/$$namespace$$`)
    kind: Rule
    services:
    - name: wordslab-notebooks-service
      port: 8888
  - match: PathPrefix(`/$$namespace$$/gradio`)
    kind: Rule
    services:
    - name: wordslab-gradio-service
      port: 7860
  - match: PathPrefix(`/$$namespace$$/fastapi`)
    kind: Rule
    services:
    - name: wordslab-fastapi-service
      port: 8000
---
apiVersion: v1
kind: Service
metadata:
  name: wordslab-notebooks-service
  labels:
    wordslab.org/app: wordslab-notebooks
    wordslab.org/component: jupyterlab
spec:
  type: ClusterIP
  ports:
    - port: 8888
      targetPort: http
      protocol: TCP
      name: http
  selector:
    wordslab.org/app: wordslab-notebooks
    wordslab.org/component: jupyterlab
---
kind: "PersistentVolumeClaim"
apiVersion: "v1"
metadata:
  name: wordslab-notebooks-workspace-volume
  labels:
    wordslab.org/app: wordslab-notebooks
    wordslab.org/component: workspace-volume
  annotations:
    wordslab.org/title: "User projects files and data"
    wordslab.org/description: "Volume where the user projects repositories are stored"
spec:
  accessModes:
    - "ReadWriteOnce"
  storageClassName: local-path
  resources:
    requests:
      storage: 5Gi
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: wordslab-notebooks-deployment
  labels:
    wordslab.org/app: wordslab-notebooks
    wordslab.org/component: jupyterlab
spec:
  replicas: 1
  selector:
    matchLabels:
      wordslab.org/app: wordslab-notebooks
      wordslab.org/component: jupyterlab
  template:
    metadata:
      labels:
        wordslab.org/app: wordslab-notebooks
        wordslab.org/component: jupyterlab
    spec:
      containers:
      - name: wordslab-jupyter-stack-container
        image: ghcr.io/wordslab-org/jupyter-stack-cuda:jupyterlab-3.6.5-lambda-0.1.14-22.04.1_2
        ports:
        - name: http
          containerPort: 8888
          protocol: TCP
```