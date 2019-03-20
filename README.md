#### Exports
```bash
 export KUBE_NAMESPACE=monitoring
 export  GCP_PROJECT=academic-pier-217920
 export  GCP_REGION=us-central1
 export  KUBE_CLUSTER=standard-cluster-1
 export  SIDECAR_IMAGE_TAG=release-0.4.0
```
#### Install Prometheus
```bash
helm install --name prometheus --namespace monitoring stable/prometheus-operator -f values.yaml 
```
#### Patch Prometheus operator
!!! In patch-operator.sh   changed the data directory - \"--prometheus.wal-directory=/data\"
```bash
./patch-operated.sh prometheus-prometheus-oper-prometheus
```

#### Logs
```
level=info ts=2019-03-20T16:06:29.874378458Z caller=main.go:256 msg="Starting Stackdriver Prometheus sidecar" version="(version=0.4.0, branch=master, revision=e246041acf99c8487e1ac73552fb8625339c64a1)"
level=info ts=2019-03-20T16:06:29.8744722Z caller=main.go:257 build_context="(go=go1.11.4, user=kbuilder@kokoro-gcp-ubuntu-prod-217445279, date=20190221-15:24:24)"
level=info ts=2019-03-20T16:06:29.875574254Z caller=main.go:258 host_details="(Linux 4.14.91+ #1 SMP Wed Jan 23 21:34:58 PST 2019 x86_64 prometheus-prometheus-prometheus-oper-prometheus-0 (none))"
level=info ts=2019-03-20T16:06:29.87560813Z caller=main.go:259 fd_limits="(soft=1048576, hard=1048576)"
level=info ts=2019-03-20T16:06:29.883283206Z caller=main.go:463 msg="Web server started"
level=info ts=2019-03-20T16:06:29.88587058Z caller=main.go:444 msg="Stackdriver client started"
level=info ts=2019-03-20T16:07:32.922384142Z caller=manager.go:150 component="Prometheus reader" msg="Starting Prometheus reader..."
```