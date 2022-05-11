1. kubectl create -f postgres-deployment.yml
2. helm install posexp prometheus-community/prometheus-postgres-exporter -f postgres_values.yaml

-   prometheus:

3. kubectl create -f prometheus-config2.yaml
4. kubectl create -f prometheus-deployment.yaml
5. kubectl create -f prometheus-nodeservice.yaml

-

6. kubectl replace -f prometheus-config2.yaml
