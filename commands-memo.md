# Cloud Shell から OKE に接続

```
kubectl version

mkdir ~/kubectl
cd ~/kubectl
wget https://storage.googleapis.com/kubernetes-release/release/v1.16.8/bin/linux/amd64/kubectl
chmod +x ~/kubectl/kubectl
echo 'PATH=$HOME/kubectl:$PATH' >> $HOME/.bashrc

exit

kubectl version

kubectl get node -o wide
```

# Kubernetes ダッシュボード

```
kubectl apply -f https://raw.githubusercontent.com/Sugi275/oke-handson/master/dashboard-oke-admin-service-account.yaml

kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep oke-admin | awk '{print $1}')

kubectl proxy
```

http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/login



# Deployment (コンテナ) 作成

```
kubectl get namespace

kubectl create namespace <yourname>

kubectl config set-context $(kubectl config current-context) --namespace=<yourname>

kubens

kubectl get deployment

kubectl get pods

kubectl apply -f https://raw.githubusercontent.com/Sugi275/oke-handson/master/deployment-cowweb.yaml

kubectl get deployment -o wide

kubectl get pod -o wide

kubectl describe deployments/cowweb

curl "http://<LoadBalancer IP>/cowsay/say?say=HOSTNAME"

kubectl get pods -o wide
```



# Deployment の挙動確認

```
kubectl get pods -o wide

kubectl logs <Pod Name>

kubectl exec -it <Pod Name> /bin/sh

env

hostname

kubectl get pods -o wide

kubectl apply -f https://raw.githubusercontent.com/Sugi275/oke-handson/master/deployment-cowweb-pod3.yaml

kubectl get pods -o wide

curl "http://<LoadBalancer IP>/cowsay/say?say=HOSTNAME"

kubectl describe deployments/cowweb

kubectl apply -f https://raw.githubusercontent.com/Sugi275/oke-handson/master/deployment-cowweb.yaml

kubectl get pods -o wide

kubectl delete pod <Pod Name>

kubectl get pods -o wide

curl "http://<LoadBalancer IP>/cowsay/say?say=HOSTNAME"
```

