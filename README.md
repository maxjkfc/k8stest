# k8stest

## 範例指令

### Pod

``` 
    kubectl get pods   #確認目前有沒有存在 pods

    kubectl create -f multiple-container.yaml #建立一個 多container的 pods

    kubectl get pods 

    kubectl describe pods redis-nginx #查看 redis-nginx pod 內的詳細資料

    kubectl port-forward pod/redis-nginx  80:8080 #將遠端 pod 的 port 映射至本地 port

    kubectl delete -f multiple-container.yaml #刪除 pods
```

### Deployments

```
    kubectl get deployments   #確認目前有沒有存在 deployments

    kubectl apply -f nginx-deployment.yaml #建立一個 deployment

    kubectl get deployments

    kubectl describe deployments nginx-deployment　#查看 deployments 內的詳細資料

    kubectl get pods 

    kubectl scale deployment nginx-deployment --replicas=3  #擴展 deployments數量為 3

    kubectl get deployments 

    kubectl set image deployment/nginx-deployment nginx=nginx:1.9.1 --record　#升級版本

    kubectl get pods -o json | jq '.items[].spec.containers[].image' #查看版本




```
### rollup 

```
    kubectl set image deployment/nginx-deployment nginx=nginx:1.9.1 --record　#升級版本

    kubectl get pods -o json | jq '.items[].spec.containers[].image' #查看版本

    kubectl rollout history deployment nginx-deployment #查看更新歷程

    kubectl rollout undo deployment  nginx-deployment #還原版本

    kubectl get pods -o json | jq '.items[].spec.containers[].image' #查看版本

```


### Service 

```
    # clusterip
    kubectl run -i --tty busybox --image=radial/busyboxplus:curl   # Run pod as interactive shell

    #另開一個畫面 取得IP
    kubectl get pods -o wide

    wget {ip} #取得網頁

    kubectl apply -f nginx-service-clusterip.yaml

    kubectl get svc

    kubectl describe svc test-nginx

    wget test-nginx

    # NodePort
    kubectl apply -f nginx-service-nodeport.yaml
    kubectl get svc
    kubectl describe svc
    kubectl get nodes -o wide 

    # LoadBalance
    kubectl apply -f nginx-service-loadbalance.yaml
    kubectl get svc
    kubectl describe svc

```

