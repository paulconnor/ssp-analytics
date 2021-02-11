# ssp-analytics

Usage:
- kubectl create ns \<ANALYTICS-NAMESPACE\>
- helm repo add ssp-analytics  "https://paulconnor.github.io/ssp-analytics/"
- helm repo update
- helm repo list
- helm install ssp-analytics ssp-analytics/ssp-analytics -n \<ANALYTICS-NAMESPACE\> --set sspReleaseName=\<YOUR-SSP-RELEASENAME\>

Test:
- kubectl get pods,svc,servicemonitor,endpoints -n analytics \<ANALYTICS-NAMESPACE\>
- Import dashboards into Grafana (13850 to 13854 inclusive)
  - Dashboards have a "Data Source" switch on the top left to select simulated data or live SSP usage data

Notes:
- \<YOUR-SSP-RELEASENAME\> will have been defined when you installed SSP
  - to retrieve use: 
    - kubectl get deployment -A | grep azserver | awk '{ print $2 }' | sed s/-azserver//
- It can take several minutes for the Prometheus ServiceMonitor to be in place and active
