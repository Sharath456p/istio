## Canary Release - Introduction
Deploy a new version of a software component (for us, new image)
But only make that new image "live" for a percentage of the time
Most of the time, the old (definitely working) version is the one being used

## Canaries with Replicas (or staged release)
1.created new deployment for staff service with risky new versioon docker image with same label. "app: staff-service"
2.refer that to the same service (staff servces) 
3.keep older deployment with 2 replicas and newer deployment with one replicas.
4.Now traffic is shifting 1/3rd to newer risky version
This is native way to do canary deployment using kubernetes.

## Version Grouping
1.Add a new label to both the deployment "version:safe" and "version:risky"
2.This helps to distinguish between two releases in kiali dashboard.
3.Using kiali dashboard we can do weighted routed traffic management by applying virtual service and Destination rules.
4.Example 10% traffic to risky version and 90%  to safe version.
5.The disadvantage is that every time we cannot use kiali to create virtial service and Destination rules

## Virtual Service
A Virtual Service enables us to configure custom routing rules to the service mesh. (Custom routing configuration)
when we apply VS istio-pilot is responsible in congfiguing all of the proxies in the mesh

