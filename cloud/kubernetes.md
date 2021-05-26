# Kubernetes
## concept
PaaS kind providing cluster management, A&A, mutlti-tenant, service registration/discovery, load balance, self-monitoring/healing, rolling upgrade and scalling out, scheduling.
```
Management Concept
*Service(label, cluster ip)
*pod(pause container and business container, sharing volume and network) 
*node(control node, edge node, worker node, carrying different kind of role and pods)
	* control node : apiserver, controller-manager, scheduler 
	* worker node: kubectl, kube-proxy
	
Deployment Conencept
	*RC
	*Deployment
	*service
```
### kubernete yaml development e.g. writing service, pod, deployments
```
1. kubectl api-resources
2. kubectl explain deployments or kubectl explain deployments.metadata or kubectl explain deployments --recursive
eg.  kubectl get replicasets <name> -n <namespace> -o yaml 
```
### Concept:Node
```
* This is coming from e.g. OpenStack or other VIM managed resource, registered to Kubernetes node controller by telling trhough kubectl. 
* kubectl, kube-proxy, docerk-daemon running on top. 
* Status: Pending, Running, Terminated
```
### Concept: Pod
```
1. container insider pod share IPC, Volumes, PID, Network, UTS
```
### Concept: Labels
link things. used internally by kubernetes to link service to pod, affinity rule. node selector etc. 
### Concept: Service
service cluster IP is not changed but only for internal use. 
service provides external access thorugh NodePort or LoadBalancer
### Volume 
```
lifecycle is with pod.
* EmptyDir
* hostPath (in host machine)
* gcePersistentDisk
* awsElasticBlockStore
* nfs
* iscsi
* glusterfs
* rdb
* gitRepo
* secret
* persistentVolumeClaim (PV) 
```
## architecture
![image](../img/KA.jpg)
```
Example of creating service/pod 
1. develop replicaset and apply kubectl create -f <rc.yaml> 
	2.1 API Server create record to ETCD 
	2.2 controler manager monitor this change thorugh API server, find out there is no pod for that then create pod object according to RC template 
	2.3 scheduler find this pod object creation activity. schdule it to right node per algorithm, writing record to etcd through API server 
	2.4 kubelet on target Node get this order and create pod as well as taking care of its lifecycle.
3. develop service and apply kubectl create -f <svc.yaml>
	4.1 API server receive service to POD link request
	4.2 Controller manager query and generate service endpoint, write to etcd through API server 
	4.3 Proxy on Node get this change and create mapping/routing through lb.
```
```
component role: 
* API Server: CRUD and change notice
* Controller manager: workhourse and controller 
* Scheduler: as it is 
* kubelet: taking care of POD LCM
* Proxy: service proxy and request routing 
* etcd: service registry/discovery/other usrage e.g. subscribe&notice 
```

## network

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
24. kubectl scale rc <name> --replicas=3 
```
