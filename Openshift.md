# Openshift Hints

## CLI Commands

* Change Project: ```oc project [project name]``` (list projects with with ```oc project```)
* Get Pods: ```oc get pods```
  * to just get names: ```oc get pods -o custom-columns=POD:.metadata.name --no-headers```
  * filter it with **grep**: ```oc get pods -o custom-columns=POD:.metadata.name --no-headers | grep [deployment name]```
  * use it greped: ```oc port-forward $(oc get pod -o custom-columns=POD:.metadata.name --no-headers | grep [deployment name]) 5432:5432```
* Cleanup whole namespace: ```oc delete all --all``` - **!Make sure u are in the correct Namespace!**
* tail log of pods: ```oc logs --follow [pod name]```
* remote shell: `oc rsh [pod name]`
