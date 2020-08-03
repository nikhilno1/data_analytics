# Data Analytics
A collection of data analytics tools that can be deployed on Kubernetes using Helm charts

## Recipe 1: Deploy a 6-node Elasticsearch cluster with Kibana running version 7.8.0

Step 1: Create a 6-node cluster on AWS EKS:  
`eksctl create cluster -f eks/config/elasticsearch-cluster.yaml`

Step 2: Add Elastic Helm repo  
`helm repo add elastic https://helm.elastic.co`

Step 3: Deploy Elasticsearch master nodes  
`helm install es-master --values elk/elasticsearch/values-master.yml --version 7.8.0 elastic/elasticsearch`

Step 4: Deploy Elasticsearch data nodes  
`helm install es-data --values elk/elasticsearch/values-data.yml --version 7.8.0 elastic/elasticsearch`

Step 5: Deploy Elasticsearch client node  
`helm install es-client --values elk/elasticsearch/values-client.yml --version 7.8.0 elastic/elasticsearch`

Step 6: Deploy Kibana node  
`helm install kibana --values elk/kibana/values-kibana.yml --version 7.8.0 elastic/kibana`

To uninstall:  
`helm delete kibana`  
`helm delete es-client`  
`helm delete es-data`  
`helm delete es-master`  
