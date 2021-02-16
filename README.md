# Udemy K8S CKAD quick labs

## Requirements:

- Minikube for local development or your K8S environment
- kubectl
- Optional: Helm

## Challenges

- [QuickLab 1](./exercise1/challenge.md)
- [QuickLab 2](./exercise2/challenge.md)
- [QuickLab 3](./exercise3/challenge.md)
  
- [Visitors operators](./operators/visitors_dashboard/challenge.md)


---



---

Create a redis deployment with the following parameters:
Name of the deployment should be redis using the redis:alpine image. It should have exactly 1 replica.
The container should request for .2 CPU. It should use the label app=redis.
It should mount exactly 2 volumes:
Make sure that the pod is scheduled on master/controlplane node.

a. An Empty directory volume called data at path /redis-master-data.
b. A configmap volume called redis-config at path /redis-master.
c.The container should expose the port 6379.


The configmap has already been created.