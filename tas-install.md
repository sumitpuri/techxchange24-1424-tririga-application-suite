# TRIRIGA Application Suite (TAS) 11.4 Out of Box Installation

### Step 1 - Prepare environment variables file

Prepare `env.list` file and update the below environment variables.

<br>

Sample `env.list`

```
OC_URL=https://c104-e.us-south.containers.cloud.ibm.com:32719
OC_TOKEN=sha256~h69AmaHb3LckBXWUzJk1iTKTOigyt19X36fDCg1JJlw
ENTITLEMENT_KEY=eyJhbGciOiJIUzI1NiJ9EO8WX4JTFQPCT1imFzl2Pgrhyrhfg
STORAGE_CLASS=ibmc-file-gold-gid
WML_INSTALL=false
```

<br>
<details><summary><b>OC_URL</b></summary>
 
Login to OpenShift Cluster
 - Open `OpenShift Web Console`
 - Click `IAM#<your_email_id>` on top right.
 - Click `Copy Login Command`
 - Display Token
 - Copy the value after `--server=`
</details>

<br>
<details><summary><b>OC_TOKEN</b></summary>
 
Login to OpenShift Cluster
 - Open `OpenShift Web Console`
 - Click `IAM#<your_email_id>` on top right.
 - Click `Copy Login Command`
 - Display Token
 - Copy the value after `--token=`
</details>

<br>
<details><summary><b>ENTITLEMENT_KEY</b></summary>
 
Obtain Entitlement Key from this [URL](https://myibm.ibm.com/products-services/containerlibrary)
</details>

<br>
<details><summary><b>STORAGE_CLASS</b></summary>
 
Navigate to Storage > StorageClasses in the OpenShift cluster to view available options. 

- IBM Cloud uses `ibmc-file-gold-gid` 
- OpenShift Data Foundation (ODF) uses `ocs-storagecluster-cephfs` 

</details>
 
<br>
<details><summary><b>WML_INSTALL</b></summary>
 
`WML_INSTALL=true` -> Installs Watson Machine Learning Service
 
`WML_INSTALL=false` -> Does not install Watson Machine Learning Service
</details>

### Step 2 - Install TRIRIGA Application Suite

```
docker run -ti --pull always --env-file env.list quay.io/sumitpuri0/tas11.4
```
> This process will take about 1.5 hrs to complete.

TRIRIGA server details can be printed by running

```
docker run -ti --env-file env.list quay.io/sumitpuri0/tas11.4 ./tas-oob-status.sh
```
