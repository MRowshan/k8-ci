# k8-ci
Run Jenkins on a kubernetes container with a GCP persistent disk attached to persist jobs.  

## kube-ctl script
installs kubectl to be able to run kubectl commands  

## create kubernetes cluster
`gcloud auth login`  
`gcloud container clusters create kubectl-cluster --zone europe-west2-c`  

## 
