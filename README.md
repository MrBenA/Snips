# Syntax and command line pick-n-mix

* [GCP gcloud](#gcloud)
* [SQL](#SQL)
* [Python](#python)
* [Pandas](#pandas)
<br>

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
Set default region and/or zone
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

##### :white_medium_small_square: Install an NGINX webserver via SSH

```shell
$ sudo su -                   /// Root Access
$ apt-get update              /// Update OS
$ apt-get install nginx -y    /// Install NGINX
$ ps auwx | grep nginx        /// Confirm NGINX is running
```
> Open VM external IP in a web browser.
> http://EXTERNAL_IP/






---

## SQL
*
---

## Python
*
---
## Pandas
*
---

> Written with [StackEdit](https://stackedit.io/).
