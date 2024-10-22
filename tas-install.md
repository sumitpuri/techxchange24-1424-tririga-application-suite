# TRIRIGA Application Suite (TAS) 11.5 Out of Box Installation

> TAS Installation script will always be `IDEMPOTENT`


### Step 1 - Prepare environment variables file

Prepare `env.list` file and update the below environment variables.

Navigate to Home > Documents

<img width="1151" alt="image" src="https://github.com/user-attachments/assets/202f1884-4457-483d-bdc3-628c8f120fa9">


`env.list` file is under `Documents`

<img width="1152" alt="image" src="https://github.com/sumitpuri/techxchange23-2064-tririga-application-suite/assets/6925028/7a394cb5-b986-4b27-9a99-eb515df4bfc4">


<br>

Sample `env.list`

```
OC_URL=https://c104-e.us-south.containers.cloud.ibm.com:32719
OC_TOKEN=sha256~h69AmaHb3LckBXWUzJk1iTKTOigyt19X36fDCg1JJlw
ENTITLEMENT_KEY=eyJhbGciOiJIUzI1NiJ9EO8WX4JTFQPCT1imFzl2Pgrhyrhfg
STORAGE_CLASS=ocs-storagecluster-cephfs
BLOCK_STORAGE_CLASS=ocs-storagecluster-cephfs
```

<br>
<details><summary><b>OC_URL</b></summary>
 
Login to OpenShift Cluster
 - Open `OpenShift Web Console`
 - Click `ocadmin` on top right.
 - Click `Copy Login Command`
 - Display Token
 - Copy the value after `--server=`
</details>

<br>
<details><summary><b>OC_TOKEN</b></summary>
 
Login to OpenShift Cluster
 - Open `OpenShift Web Console`
 - Click `ocadmin` on top right.
 - Click `Copy Login Command`
 - Display Token
 - Copy the value after `--token=`
</details>

<br>
<details><summary><b>ENTITLEMENT_KEY</b></summary>
 
Use Existing Entitlement Key present in the `env.list` file.

<br> 
Otherwise, check your entitlement using this [URL](https://myibm.ibm.com/products-services/containerlibrary)
</details>

<br>
<details><summary><b>STORAGE_CLASS</b></summary>
 
Navigate to Storage > StorageClasses in the OpenShift cluster to view available options. 

- OpenShift Data Foundation (ODF) uses `ocs-storagecluster-cephfs`
- IBM Cloud uses `ibmc-file-gold-gid`

Select  `ocs-storagecluster-cephfs`

</details>
 
<br>
<details><summary><b>BLOCK_STORAGE_CLASS</b></summary>
 
Navigate to Storage > StorageClasses in the OpenShift cluster to view available options. 

- OpenShift Data Foundation (ODF) uses `ocs-storagecluster-cephfs`
- IBM Cloud uses `ibmc-file-gold-gid`

Select  `ocs-storagecluster-cephfs`

</details>

 
### Step 2 - Install TRIRIGA Application Suite

Open the Linux terminal and navigate to Documents using:

```
cd Documents
```

```
podman run -ti --pull always --env-file env.list quay.io/sumitpuri0/tas11.5
```
> This process will take about 1.5 hrs to complete.

<img width="583" alt="image" src="https://github.com/user-attachments/assets/17460841-9582-4ae2-966c-0901e5444fc8">


TRIRIGA server details can be printed by running

```
podman run -ti --env-file env.list quay.io/sumitpuri0/tas11.5 ./tas-oob-status.sh
```
