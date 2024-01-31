# helloWorldHelm
A basic go api server made into a helm chart to be deployed in a cluster and has few OpenTelemetry observability setup done.

# installation
- Its a best practice to make a new namespace for an application
    - namespace can be created by running `kubectl create ns <namespace>`
- helm repo add `<repo name>` https://vijay-anantham.github.io/helloWorldHelm/charts
- helm install -n `<namespace>` `<release name>` `<repo name>`/hello_worldchart

# Running the application

1. It is assumed that you create a new namespace to install the helm chart

2. the otel traces are sent using otlp-http
    - default: "http://jaeger-collector.opentelemetry.svc.cluster.local:4318"

    - To set custom otlp collector it can be set by passing as an environment variable 'OTEL_EXPORTER_OTLP_ENDPOINT'

    - The environment variable can be passed via a config map

    - to pass custom configmap set the `customconfig.enable` to true in the values file.

    - pass the path to the custom config file into the `customconfig.name` variable.

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

## Application code
- You can find the code for the application rolldice in the repo
    - `https://github.com/Vijay-Anantham/roll-dice`
    
