1. kubectl create -f postgres-deployment.yml
   contains pvc, secret, deployment, service
   postgres deployment with password: "root", username: "root", database:"root"
2. helm install posexp prometheus-community/prometheus-postgres-exporter -f postgres_values.yaml

postgres_values.yaml contains custom values so prometheus-postgres-exporter can connect to our postgres using those variables such as username, password.

-   prometheus:

3. kubectl create -f prometheus-config2.yaml
   prometheus-config2.yaml contains jobs which prometheus will monitor
4. kubectl create -f prometheus-deployment.yaml

contains pvc, secret, deployment, service for prometheus

5.  kubectl create -f prometheus-nodeservice.yaml

    enter new job in prometheus-config2.yaml and user replce cmd

        # example:

        <!--
          - job_name: 'prometheus'
            static_configs:
            - targets: ['192.168.49.2:30510']

             -->


         here prometheus will monitor apllication running on 192.168.49.2:30510

6.  kubectl replace -f prometheus-config2.yaml

we can use replace cmd on prometheus-config2.yaml so prometheus will thake new configurations

kill the prometheus pod so new pod will start with new configurations
