# agones
It is not full solution(game server works, as I see from logs of pods, but I don't understand how to connect client. I read documentation but it still not clear for me. Anyway thanks )
## Install and start Minikube (just want to avoid of using my work GCP or AWS accounts, that is why minikube)
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start
## Install Agones using Helm Chart
helm repo add agones https://agones.dev/chart/stable
helm repo update
helm install my-release --namespace agones-system --create-namespace agones/agones
## Create a GameServer in Kubernetes using Agones custom resource.
kubectl create -f https://raw.githubusercontent.com/googleforgames/agones/release-1.18.0/examples/xonotic/gameserver.yaml
```$ kubectl get gameservers
NAME                       STATE       ADDRESS        PORT   NODE       AGE
xonotic   Ready   192.168.49.2   7496   minikube   4s```
