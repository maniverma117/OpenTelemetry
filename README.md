# Monitoring Microservices application using OpenTelemetry 
Reference Documentation: https://opentelemetry.io/docs/

# 1. Install and Configure Microservices Application:  

    cd opentelemetry-app
    kubectl create namespace otel-demo
    kubectl apply -f .

# 2. Install and Configure Open Telemetry Collector:  

This will collect traces from application and captures at the collector port.

    cd opentelemetry-collector
    kubectl apply -f .

# 3. Install and Configure Jaeger:  

    cd jaeger
    kubectl apply -f .

# 4. Install and Configure Prometheus:  

    cd prometheus
    kubectl apply -f .

# 5. Install and Configure Grafana:  

    cd grafana
    kubectl apply -f .


Expose services using kubectl port-forward
To expose the frontendproxy service use the following command (replace my-otel-demo with your Helm chart release name accordingly):

kubectl port-forward svc/opentelemetry-demo-frontendproxy 8080:8080 -n otel-demo 

Note: kubectl port-forward will proxy the port until the process terminates. You may need to create separate terminal sessions for each use of kubectl port-forward, and use Ctrl-C to terminate the process when done.

With the frontendproxy port-forward set up, you can access:

Web store: http://localhost:8080/
Grafana: http://localhost:8080/grafana/
Feature Flags UI: http://localhost:8080/feature/
Load Generator UI: http://localhost:8080/loadgen/
Jaeger UI: http://localhost:8080/jaeger/ui/
