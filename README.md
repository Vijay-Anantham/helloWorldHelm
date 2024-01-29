# helloWorldHelm
A basic go api server made into a helm chart to be deployed in a cluster and has few OpenTelemetry observability setup done.

# installation
- helm repo add `<repo name>` https://vijay-anantham.github.io/helloWorldHelm/charts
- helm install `<release name>` `<repo name>`/hello_worldchart