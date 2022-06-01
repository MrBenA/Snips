## :large_orange_diamond: gcloud

[gcloud CLI overview](https://cloud.google.com/sdk/gcloud)

### Account details and defaults
:small_orange_diamond:
List active acount name
```shell
$ gcloud auth list
```
<br>

:small_orange_diamond:
List project Id
```shell
$ gcloud config list project
```
<br>

:small_orange_diamond:
Identify your default region and zone
```shell
$ gcloud compute project-info describe --project <your_project_ID>
```
> If `google-compute-default-region` and `google-compute-default-zone` keys and values are missing from the output, no default zone or region is set.
<br>

:small_orange_diamond:
Set default compute region and/or zone
```shell
$ gcloud config set compute/region <region>
$ gcloud config set compute/zone <zone>
```
<br>

### Virtual Machines
:small_orange_diamond:
See new VM instance defaults
```shell
$ gcloud compute instances create --help
```
> To exit `help`, press **CTRL + C**
<br>

:small_orange_diamond:
Create new VM instance
```shell
$ gcloud compute instances create <instancename> --machine-type <n1-standard> --zone <us-central1-f>
```
<br>

:small_orange_diamond:
SSH to VM
```shell
$ gcloud compute ssh <instancename> --zone <zone>
```
> omit the `--zone` flag if option is set globally
<br>

#### :white_medium_small_square: Install an NGINX webserver via SSH

```shell
$ sudo su -                   /// Root Access
$ apt-get update              /// Update OS
$ apt-get install nginx -y    /// Install NGINX
$ ps auwx | grep nginx        /// Confirm NGINX is running
```
> Open VM external IP in a web browser.
> http://EXTERNAL_IP/
<br>

### Kubernetes

:small_orange_diamond:
Create a GKE cluster
```shell
$ gcloud container clusters create <cluster-name>
```
> Cluster names must start with a letter and end with an alphanumeric, and cannot be longer than 40 characters
<br>

:small_orange_diamond:
Get authentication credentials for GKE cluster
```shell
$ gcloud container clusters get-credentials <cluster-name>
```
<br>

#### :white_medium_small_square: Deploy containerised application to a GKE cluster

> Create a new Deployment `hello-server` from the `hello-app` container image
> `gcr.io/google-samples/hello-app:1.0` indicates the specific image version to pull. If a version is not specified, the latest version is used.

:white_medium_small_square:
Create a new deployment
```shell
$ kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:1.0
```
<br>

:white_medium_small_square:
Create a Kubernetes service
```shell
$ kubectl expose deployment hello-server --type=LoadBalancer --port 8080
```
> * `--port` specifies the port that the container exposes.<br>
> * `type="LoadBalancer"` creates a Compute Engine load balancer for the container.
<br>

:white_medium_small_square:
Inspect the `hello-server` service
```shell
$ kubectl get service
```
> It may take a minute for an external IP address to be generated. Run command again if the EXTERNAL-IP column status is pending. <br>
> View the application from a web browser at http://EXTERNAL_IP/:8080
<br>

:small_orange_diamond:
Delete GKE cluster
```shell
$ gcloud container clusters delete <CLUSTER-NAME>
```
<br>