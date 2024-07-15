# spark-operator-with-yunikorn

## yunikorn 部分
### 準備 namespace: ###
```shell
kubectl create namespace yunikorn
```

### online 安裝: ###
```shell
helm install yunikorn yunikorn/yunikorn -n yunikorn --version 1.5.1 --set embedAdmissionController=false --set enableSchedulerPlugin=true 
```

### air-gap 安裝: ###
#### 準備 image: ####
```shell
docker pull apache/yunikorn:scheduler-1.5.1
docker pull apache/yunikorn:scheduler-plugin-1.5.1
docker pull apache/yunikorn:admission-1.5.1
docker pull apache/yunikorn:web-1.5.1
```
```shell
helm install yunikorn yunikorn-1.5.1.tgz -n yunikorn --set embedAdmissionController=false --set enableSchedulerPlugin=true
```

#### 項目repo: ####
<https://github.com/apache/yunikorn-core>


## Spark-Operator 部分
### 準備 namespace ###
有 gatekeeper 的話可以隔離 spark-run-namespace-1 到指定節點，沒有的話後續在 yunikorn 的 config 再做限制也可以
### 準備 namespace: ###
```shell
kubectl create namespace spark-operator
kubectl create namespace spark-run-namespace-1
```

### online 安裝: ###

```shell
helm install spark-operator spark-operator/spark-operator \
    --namespace spark-operator \
    --set podMonitor.enable=true \
    --set serviceAccounts.spark.name="spark-submit-sa" \
    --set sparkJobNamespaces=["spark-run-namespace-1"]\
    --set webhook.enable=true
```

### air-gap 安裝: ###
#### 準備 image: ####
```shell
docker pull apache/yunikorn:scheduler-1.5.1
docker pull apache/yunikorn:scheduler-plugin-1.5.1
docker pull apache/yunikorn:admission-1.5.1
docker pull apache/yunikorn:web-1.5.1
```

```shell
helm install spark-operator spark-operator-1.4.3.tgz \
    --namespace spark-operator \
    --set podMonitor.enable=true \
    --set serviceAccounts.spark.name="spark-submit-sa" \
    --set sparkJobNamespaces=["spark-run-namespace-1"]\
    --set webhook.enable=true
```
#### 項目repo: #### 
<https://github.com/kubeflow/spark-operator/tree/v1beta2-1.6.1-3.5.0>
