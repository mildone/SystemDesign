# Kubernetes
## concept
PaaS kind providing cluster management, A&A, mutlti-tenant, service registration/discovery, load balance, self-monitoring/healing, rolling upgrade and scalling out, scheduling.
```
*Service(label, cluster ip)
*pod(pause container and business container, sharing volume and network) 
*node(control node, edge node, worker node, carrying different kind of role and pods)
	* control node : apiserver, controller-manager, scheduler 
	* worker node: kubectl, kube-proxy
```

## network
## architecture
## command & Tips

1. kubectl apply -f **.yaml
2. kubectl expose pod green -port 8080 --name blue-green  (service to outside)
3. kubect get service -n **
4. Ingress to config proxy 
	- routing on path pattern
	- kubectl apply -f ingress.yaml 
5. kubectl get pod ** -o yaml (to export spec of that pod)
6. kubectl explain pod 
7. kubectl port-forward <pod name> 8080:8081
8. kubectl logs pod
9. kubectl top pods  <check the status like top in linux> 
10. kubectl diff -f *.yaml 
11. kubectl api-resources |grep batch 
12. kubectl delete -f *.yaml <to delete that pod>
13. job run onetime e.g. restartPolicy is never 
14. kubectl logs <job name>
15. cronjob as one of kube resources or type
16. kubectl get endpoints  (service expose endpoint to outside world and enpoint only expose when it's ready for outside invocation) 
17. core numer * 1000 is the limite, e.g. 2 Core then the limit is 2000m
	if in one Container the limite is set as 2000m then that means it will require all 2 cores. 	
18. DRY-Don't Repeat yourself
19. helm template -f value.yaml .
20. helm history <** name>
21. kubectl debug <pod name> --attach
22. kubectl run -ti net-debug --image=nixery.dev/shell/curl/wget/htop /bin/bash
23. kubectl sniff <pod name>  (wireshark traffic of that pod) 
```
