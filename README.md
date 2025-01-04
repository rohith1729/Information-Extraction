# Flask on Kubernetes

Read the deployment guide: [A Guide to Deploy Flask App on Google Kubernetes Engine](https://medium.com/@pyk/a-guide-to-deploy-flask-app-on-google-kubernetes-engine-bfbbee5c6fb)


gcloud builds --project adroit-flare-437719-d9     submit --tag gcr.io/adroit-flare-437719-d9/flask-app:latest .

gcloud container clusters create my-cluster   --zone us-central1-a   --num-nodes 2
gcloud container clusters get-credentials my-cluster --zone us-central1-a

kubectl create secret generic google-cloud-key-secret --from-file=key.json=flaskstoragekey.json

kubectl apply -f app.yaml
kubectl expose deployment flask-app-tutorial \
--type=LoadBalancer --port 80 --target-port 8080
kubectl get services -l name=flask-app-tutorial

gcloud container clusters delete my-cluster --zone us-central1-a


