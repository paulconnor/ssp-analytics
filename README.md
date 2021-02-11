# ssp-analytics

Usage:
- kubectl create ns \<ANALYTICS-NAMESPACE\>
- helm repo add ssp-analytics  "https://paulconnor.github.io/ssp-analytic/"
- helm repo update
- helm repo list
- helm install ssp-analytics ssp-analytics/ssp-analytics -n \<ANALYTICS-NAMESPACE\> --set sspReleaseName=\<YOUR-SSP-RELEASENAME\>

Test:
- kubectl get pods,svc,servicemonitor,endpoints -n analytics \<ANALYTICS-NAMESPACE\>
