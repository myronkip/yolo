# Step 1: Initialize Google Cloud SDK
gcloud init

# Step 2: Create a GKE Cluster
gcloud container clusters create my-gke-cluster --num-nodes=2 --zone=us-central1-a

# Step 3: Get cluster credentials
gcloud container clusters get-credentials my-gke-cluster --zone us-central1-a

# Step 4: Create k8s-manifest files
1.mongo-statefulset.yaml
2.mongo-service.yaml
3.backend-deployment.yaml
4.backend-service.yaml
5.frontend-deployment.yaml
6.frontend-service.yaml

# Step 5: Deploy MongoDB StatefulSet
kubectl apply -f mongo-statefulset.yaml

# Step 6: Deploy front-end application
kubectl apply -f frontend-deployment.yaml

# Step 7: Expose front-end using LoadBalancer
kubectl apply -f frontend-service.yaml

# Step 8: Get external IP
kubectl get services

# Step 8: Verify pods,services &deployment are running
kubectl get all

# Application URL
http://34.55.81.102:80

