# ssp-analytics

Usage:
- export ANALYTICS-NAMESPACE=analytics
- export SSP-RELEASENAME=`kubectl get deployment -A | grep azserver | awk '{ print $2 }' | sed s/-azserver//`
- kubectl create ns $ANALYTICS-NAMESPACE
- helm repo add ssp-analytics  "https://paulconnor.github.io/ssp-analytics/"
- helm repo update
- helm repo list
- helm install ssp-analytics ssp-analytics/ssp-analytics -n $ANALYTICS-NAMESPACE --set sspReleaseName=$SSP-RELEASENAME

Test:
- kubectl get pods,svc,servicemonitor,endpoints -n analytics $ANALYTICS-NAMESPACE
- Import dashboards into Grafana (13850 to 13854 inclusive)
  - Dashboards have a "Data Source" switch on the top left to select simulated data or live SSP usage data
  - SSP Data is scraped every 20 seconds by default so there will be a delay in it appearing in the dashboard.

Uninstall:
- helm uninstall ssp-analytics -n $ANALYTICS-NAMESPACE

Notes:
- It can take several minutes for the Prometheus ServiceMonitor to be in place and active
- The live/SSP metric scraping is a work in progress. Not all dashboards receive live data yet.
