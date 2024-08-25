# DTOK8S-MIGRATION

## DOCKER TO K8S MIGRATION PROJECT STEPS

> * STEP 1

TAKE THE LINUX2 AMI EC2 WITH 20 GB AND T2.MEDIUM

> * STEP 2 

yum update -y

yum install docker -y

systemctl start docker

systemctl enable docker

yum install conntrack -y

yum install git -y

> * STEP 3 - Download Minikube 
 
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

> * STEP 4 - sudo install minikube-linux-amd64 /usr/local/bin/minikube 

/usr/local/bin/minikube start --force --driver=docker 

> * STEP 5 - cd /opt/ git clone https://github.com/Free-Bootcamp8/Kubernetes_Resources.git 

> * STEP 6 - Install kubectl
 
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.20.4/2021 -04-12/bin/linux/amd64/kubectl

chmod +x ./kubectl 

mkdir -p $HOME/bin 

cp ./kubectl $HOME/bin/kubectl 

export PATH=$HOME/bin:$PATH 

echo 'export PATH=$HOME/bin:$PATH' >> ~/.bashrc 

source $HOME/.bashrc 

kubectl version --short –client


> * STEP 7 - cd Kubernetes folder and create the namespace

kubectl apply -f namespace.yaml 
 
> * STEP 8 - Verify the namespace 

kubectl get ns 

> * STEP 9 - Create the configmap 

kubectl apply -f configmap.yaml 

> * STEP 10 - Create the Secrets

 kubectl apply -f secret.yam
 
> * STEP 11 - Create the Persistent volume

kubectl apply -f persistent-volume.yaml 

> * STEP 12 - Check for various API resources in kubernetes 

kubectl get api-resources 

> * STEP 13 - Create the Persistent volume claim 

kubectl apply -f persistent-volume-claim.yaml 

> * STEP 14 - Create the web deployment

kubectl apply -f web-deployment.yaml 

> * STEP 15 - kubectl apply -f db-deployment.yaml

> * STEP 16 - Create the service for web app DB

kubectl apply -f web-service.yaml 
kubectl apply -f db-service.yaml

> * STEP 17 - Check all the data

kubectl get cm 

kubectl get pods 

Kubectl get svc 

kubectl get pods -n my-app 

> * STEP 18 - Check logs

kubectl logs web-deployment-dc469f978-wcqqf -n my-app
