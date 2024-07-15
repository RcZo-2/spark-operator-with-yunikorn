# spark-operator-with-yunikorn

## yunikorn 部分
### online 安裝: ###
helm install yunikorn yunikorn/yunikorn -n yunikorn --version 1.5.1 --set embedAdmissionController=false --set enableSchedulerPlugin=true 

### air-gap 安裝: ###
helm install yunikorn yunikorn-1.5.1.tgz -n yunikorn --set embedAdmissionController=false --set enableSchedulerPlugin=true


## Spark-Operator 部分
### online 安裝: ###

### air-gap 安裝: ###
