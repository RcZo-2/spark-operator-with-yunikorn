# spark-operator-with-yunikorn

## yunikorn 部分
### online 安裝: ###
```shell
helm install yunikorn yunikorn/yunikorn -n yunikorn --version 1.5.1 --set embedAdmissionController=false --set enableSchedulerPlugin=true 
```
### air-gap 安裝: ###
```shell
helm install yunikorn yunikorn-1.5.1.tgz -n yunikorn --set embedAdmissionController=false --set enableSchedulerPlugin=true
```

#### 項目repo: ####
<https://github.com/apache/yunikorn-core>

## Spark-Operator 部分
### online 安裝: ###
```shell
helm install spark-operator spark-operator/spark-operator \
    --namespace spark-operator \
    --set webhook.enable=true
```

### air-gap 安裝: ###

#### 項目repo: #### 
<https://github.com/kubeflow/spark-operator/tree/v1beta2-1.6.1-3.5.0>
