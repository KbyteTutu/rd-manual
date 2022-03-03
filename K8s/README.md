# K8s

## 💔常见问题
###### 1.kubectl命令无权限问题
```
修改配置文件权限，例如： sudo chmod 666 /etc/rancher/k3s/k3s.yaml   # 此处为k3s配置，其它同理
```

## 💚常用命令
### 0.config
#### 0.1 获取kubeconfig
`kubectl config view`
#### 0.2 通用逻辑
- -A : 表示获取全部命名空间的对象

### 1.namespace
#### 1.1 获取所有工作空间
`kubectl get namespace  # namespace可简写为ns`
#### 1.2 创建命名空间
`kubectl create namespace <insert-namespace-name-here`
#### 1.3 删除命名空间
`kubectl delete namespaces <insert-some-namespace-name>`
#### 1.4 查看当前工作空间
`kubectl config view | grep namespace`
#### 1.5 切换命名空间
`kubectl config set-context --current --namespace=<insert-namespace-name-here>`

### 2.node
#### 2.1 查看集群所有节点的状态
`kubectl get nodes`
#### 2.2 查看指定节点详细信息
`kubectl describe node <节点名称>`
#### 2.3 给node加标签
`kubectl label nodes {节点名称} disktype={标签名}`

### 3.pod
#### 3.1 获取pods
```bash
kubectl get pods
kubectl get pods -A
```
### 3.2 获取指定工作空间的所有
`kubectl get pods -n <namespace>`
### 3.3 重启pod
```bash
kubectl replace --force -f {yaml文件}
kubectl get pod {podname} -n {namespace} -o yaml | kubectl replace --force -f -
```
### 3.4 删除pod
`kubectl delete pod {podname}`

### 4.secret
#### 4.1 获取secrets
```bash
kubectl get secrets        
kubectl get secrets -A
```
#### 4.2 创建secrets
[Secret | Kubernetes](https://kubernetes.io/zh/docs/concepts/configuration/secret/)
#### 4.3 查看secret信息
`kubectl get secret {secret name} -o yaml`

### 5.configmap
#### 5.1 获取configmap
`kubectl get cm -A`
#### 5.2 获取指定configmap的详情
`kubectl get cm <configmap> -o yaml`

### 6.describe
输出指定的一个/多个资源的详细信息
```bash
kubectl describe pod {podname}       # 描述指定pod
kubectl desctibe pods                # 描述所有pod
```

### 7.api
获取所有可用API版本
`kubectl api-versions`
