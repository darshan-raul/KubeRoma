
First do it
Then do it right
Then do it better

`Apollo 11`

11 stage plan to know end-to-end of k8s/cloudnative ecosystem

We will be creating a simple rest api in Golang and then extending it with a frontend and backend.
Along the way we will explore all the services and features in the k8s ecosystem to get a handson on how to create a Complete app architecture



--------------------------------
Pre-requisites
--------------------------------

[You need to be NASA before you can be in the apollo program ;) ]

Some basics have to be in place:

- Linux : 
	https://linuxjourney.com/
	https://developer.ibm.com/tutorials/linux-basics-and-commands/

- Vim: (Coz there will not always be ide) https://www.youtube.com/watch?v=ggSyF1SVFr4
- Yaml: ( k8s is all yaml) 
	https://www.youtube.com/watch?v=1uFVr15xDGg
	https://developer.ibm.com/tutorials/yaml-basics-and-usage-in-kubernetes/


Optional:
- 

--------------------------------
Stage 1: Basics + Local setup [ 2 weeks ]
--------------------------------

1. Go Lang basics

	https://www.youtube.com/watch?v=jpKysZwllVw&t=488s

	> Note: Go lang for rest api is optional. Python can work too.

2. Docker Basics:
	
	Because


	https://developer.ibm.com/blogs/what-are-containers-and-why-do-you-need-them/
	https://developer.ibm.com/tutorials/building-docker-images-locally-and-in-cloud/
	http://docker-saigon.github.io/post/Docker-Internals/


Optional:
	- https://developer.ibm.com/articles/true-benefits-of-moving-to-containers-1/
	- https://developer.ibm.com/articles/true-benefits-of-moving-to-containers-2/

3. Kubernetes basics
	
	Watch this video completely. Take notes.

	https://www.youtube.com/watch?v=X48VuDVv0do&t=6088s

	Get your hands dirty. This tutorial will give a good bootstrap on k8s operations

	https://kubernetes.io/docs/tutorials/kubernetes-basics/

	Brisk through https://kubernetes.io/docs/concepts.
	(Coz reading the documentation for 15 mins is better than spending 2 hours on stackoverflow) :D
	> The previous two tasks will make it pretty easy for you to understand the core concepts from the documentation. This will be just to consolidate those core concepts and collect more dots of k8s knowledge. In the later stages you will be able to connect those extra dots as well.
	[ ETA 2-3 days ]
	

	Optional:
	- https://developer.ibm.com/videos/learn-the-history-and-fundamentals-of-kubernetes/


4. Install minikube & understand the basics:
	https://kubernetes.io/docs/tutorials/hello-minikube/

	> Note: Minikube is the simplest way to start a local k8s cluster. There are many other ways like kind,k3s,microk8s amongst others.https://developer.ibm.com/blogs/options-to-run-kubernetes-locally/


5. Install and Get overview of kubectl


	https://kubernetes.io/docs/reference/kubectl/overview/



-- Actual project

Create namespace "application"
Create everything using configuration yaml


Extra reads:
- Check all the terms and glossary https://kubernetes.io/docs/reference/glossary/?all=true


Goal> good enough knowledge of k8s and golang to get started

--------------------------------
Stage 2: Rest api + backend in local k8s cluster [ 2 weeks ]
--------------------------------

Create a simple go rest API
Build docker image with it
Figure how to link local image repo in minikube 

Create a deployment and expose as external service
Should be able to access it from browser as <externalip>.port

Create namespace "nosql"
mongodb deployment
Expose mongodb as internal service
Mongodb credentials stored in secrets.
Then referenced from mongoexpress deployment
(Need to create secrets before you can use them)

Learn peristent volumes and stateful sets and change mongodb to that instead of deployment

Create a config map of non sensitive values if needed
Mongo express deployment
Expose mongodbexpress as external service

Change go code to interact with mongodb
Make the go service interact with mongodb service
Crud operation should work 


Create namespace front end
Add a small front end app to the make calls to go api

Create local image

Create it as deployment and load env variables from a config map
Expose it as external service


Goal> Rest api to interact with mongodb. mongoexpress to interact with mongodb. Frontend to interact with API

--------------------------------
Stage 3: Routing using ingress controller [ 1 week ]
--------------------------------

Create ingress rules for sample url ---> gobuydoge.com
/Frontend will take to frontend external service
/Backend will take to backeelnd external service


Create ingress controller to control all the routes
On local machine add entry for gobuydoge.com to the ingress controller ip

Gobuydoge.com/frontend should show frontend
Gobuydoge.com/backend should show backend


Extra:
	- Have a look at various other ingress controllers: https://docs.google.com/spreadsheets/d/191WWNpjJ2za6-nbG4ZoUMXMpUK8KlCIosvQB0f-oq3k/htmlview?pru=AAABdXUHlbs*g6XkyoZXhanlhRazst77Xw
	- Try Traefik v2 ingress controller


--------------------------------
Stage 4: Move on from Minikube/Docker
--------------------------------

Move to creating two virtual machines(vagrant)
One will be master
One will be worker


Learn kubernetes the hard way
Create control node components on master node
Install any other container runtime other than docker
Run the same workload that was run on minikube

Run the above setup in either of a cloud k8s platform (manually for now):
- EKS
- AKS
- GKE
- Linode


Extra: 
- Use buildah to build container images instead of 
- Try different local k8s platforms: k3s,kind,microk8s.
- Aws eks infra building with CDK

--------------------------------
Stage 5: Helm packaging
--------------------------------


- helm packages building

katakoda

--------------------------------
Stage 6: Service Mesh
--------------------------------
- Service mesh ISTIO

A service mesh, like the open source project Istio, is a way to control how different parts of an application share data with one another. Unlike other systems for managing this communication, a service mesh is a dedicated infrastructure layer built right into an app. This visible infrastructure layer can document how well (or not) different parts of an app interact, so it becomes easier to optimize communication and avoid downtime as an app grows.

--------------------------------
Stage 7: Monitoring + Observability + Tracing
--------------------------------

- K8s monitoring
	- EFK Logging
	- lens
	- prometheus
	- Tracing using opentelementry


--------------------------------
Stage 8: Deployment/Gitops + Autoscaling
--------------------------------

- K8s Deployment strategy
	- CICD using github actions
	- DevSecops
	- TestOps
	- k8s misconfiguration from reaching production- datree 

- Various deployment patterns in K8s
- gitops with flux v2

--------------------------------
Stage 8: Event driven architecture
--------------------------------

- Introduce a event bus or stream eg. Apache FLink and operate using same


--------------------------------
Stage 9: Testing + Chaos Engineering + Backup and Restore
-------------------------------- 

- DevSecOps
- inject failure into your Kubernetes clusters

--------------------------------
Stage 10: Security and Compliance
--------------------------------

https://kubernetes.io/docs/concepts/security/

- Secure the cluster based on the 4C’s of cloud native security
- kubehunter
- Gatekeeper

- Enforce good practices using datree

https://www.stackrox.com/post/2020/05/kubernetes-security-101/

--------------------------------
Stage 11: Go deeper
--------------------------------

- Admission controllers/webhooks https://www.youtube.com/watch?v=1mNYSn2KMZk
- Kubernetes Operator


-- Try new tools and features:
	https://github.com/grafana/tanka

https://ymmt2005.hatenablog.com/entry/k8s-things [47 Things To Become a Kubernetes Expert]
https://github.com/walidshaari/Kubernetes-Certified-Administrator
https://github.com/walidshaari/Certified-Kubernetes-Security-Specialist
https://github.com/ibrahimjelliti/CKSS-Certified-Kubernetes-Security-Specialist

Cheatsheets
https://kubernetes.io/docs/reference/kubectl/cheatsheet/


--------------------------------
References:
--------------------------------

	- https://github.com/tomhuang12/awesome-k8s-resources
	https://labs.play-with-k8s.com/#
	https://developer.ibm.com/components/kubernetes/series/kubernetes-learning-path/
