# ssp-analytics

Usage:
- export ANALYTICSNAMESPACE=analytics
- export SSPRELEASENAME=\<your SSP Release name\>
- kubectl create ns $ANALYTICSNAMESPACE
- helm repo add ssp-analytics  "https://paulconnor.github.io/ssp-analytics/"
- helm repo update
- helm repo list
- helm install ssp-analytics ssp-analytics/ssp-analytics -n $ANALYTICSNAMESPACE --set sspReleaseName=$SSPRELEASENAME

Test:
- kubectl get pods,svc,servicemonitor,endpoints -n $ANALYTICSNAMESPACE
- Import dashboards into Grafana (16044)
  - Dashboards have a "Data Source" switch on the top left to select simulated data or live SSP usage data
  - SSP Data is scraped every 20 seconds by default so there will be a delay in it appearing in the dashboard.

Uninstall:
- helm uninstall ssp-analytics -n $ANALYTICSNAMESPACE

Notes:
- It can take several minutes for the Prometheus ServiceMonitor to be in place and active
- The live/SSP metric scraping is a work in progress. Not all dashboards receive live data yet.
