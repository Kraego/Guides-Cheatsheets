# Openshift Hints

## CLI Commands

* Change Project: ```oc project [project name]``` (list with ```òc project list```
* Get Pods: ```oc get pods```
  * to just get names: ```oc get pods -o custom-columns=POD:.metadata.name --no-headers```
  * filter it with **grep**: ```oc get pods -o custom-columns=POD:.metadata.name --no-headers | grep [deployment name]```
* Cleanup whole namespace: ```oc delete all --all``` - **!Make sure u are in the correct Namespace!**
* tail log of pods: ```oc logs --follow [pod name]```
