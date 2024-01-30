# helloWorldHelm
A basic go api server made into a helm chart to be deployed in a cluster and has few OpenTelemetry observability setup done.

# installation
- helm repo add `<repo name>` https://vijay-anantham.github.io/helloWorldHelm/charts
- helm install -n `<namespace>` `<release name>` `<repo name>`/hello_worldchart

# Running the application

1. It is assumed that you create a new namespace to install the helm chart

2. the otel traces are sent using otlp-http
    - default: `http://jaeger-collector.opentelemetry.svc.cluster.local:4318`
3. if no namespace was selected when installing the chart then,
    - Run 'kubectl get all -n `<namespace>`'

4. if no namespace was selected when installing the chart then,
    - Run 'kubectl get all'

5. The following are should be found.
    - one pod in 'running' status
    - one deployment with name 'rolldice'
    - one service with name 'rolldice'

6. To run the application
    - If installed in a nampspace
        - Run 'kubectl port-forward -n `<namespace>` svc/rolldice 8080:8080'

7. You can get the dice roll value by accessing
    - `http://localhost:8080/rolldice`
    
