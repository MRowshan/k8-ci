# k8-ci
Run Jenkins on a kubernetes container with a GCP persistent disk attached to persist jobs.  

# steps to run jenkins and nginx on kubernetes
## kube-ctl script
installs kubectl to be able to run kubectl commands  

## Create kubernetes cluster
- click on link and copy code: `gcloud auth login`  
- enter cluster name and zone: `gcloud container clusters create [CLUSTER_NAME] --zone [ZONE]`  
e.g. `gcloud container clusters create kubectl-cluster --zone europe-west2-c`  

## If there is no persistent disk, create it
Adjust size of disk and zone to preference: `gcloud compute disks create --size=[SIZE] --zone=[ZONE] jenkins-jobs`  
e.g. `gcloud compute disks create --size=200GB --zone=europe-west2-c jenkins-jobs`

## Run .yml files
`kubectl create -f cluster-admin-role-binding.yml`
`kubectl create -f jenkins`
`kubectl create -f nginx`

## Edit nginx.conf to connect to jenkins
To get [NGINX_ID] use `kubectl get pods`  
`kubectl exec -it [NGINX_ID] bash`  
### Install vim to edit files (optional)
apt update
apt install vim
### Edit nginx.conf
cd /etc/nginx
vim nginx.conf 
    
