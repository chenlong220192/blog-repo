## 使用`root`用户安装minikube
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
## 创建`minikube`账号(minikube进程无法使用`root`运行)
```
useradd minikube
```
## 将`minikube`账号赋予docker权限
```
sudo usermod -aG docker minikube
```
## 切换`minikube`账号(不要使用`sudo su minikube`)
```
su minikube
```
## 安装minikube
```
minikube start  \
  --driver=docker  \
  --container-runtime=containerd \
  --nodes=1 \
  --cpus=2 \
  --memory=2G \
  --disk-size=20G \
  --image-repository=auto \
  --image-mirror-country=cn \
  --registry-mirror='https://wivp6w5w.mirror.aliyuncs.com' \
  --listen-address='0.0.0.0' \
  --apiserver-ips="10.0.0.8" \
  --apiserver-port=8443 \
  --output=json \
  --kubernetes-version=v1.24.2
```
