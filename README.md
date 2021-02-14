# Udemy K8S CKAD quick labs

## Requirements:

- Minikube for local development or your K8S environment
- kubectl
- Optional: Helm

## Challenges

- [QuickLab 1](./exercise1/challenge.md)
- [QuickLab 2](./exercise2/challenge.md)

- [Visitors operators](./operators/visitors_dashboard/challenge.md)

---

Create a pod called time-check in the dvl1987 namespace. This pod should run a container called time-check that uses the busybox image.

   Create a config map called time-config with the data TIME_FREQ=10 in the same namespace.
   The time-check container should run the command: while true; do date; sleep $TIME_FREQ;done and write the result to the location /opt/time/time-check.log.
   The path /opt/time on the pod should mount a volume that lasts the lifetime of this pod.

---

Create a new deployment called nginx-deploy, with one signle container called nginx, image nginx:1.16 and 4 replicas. The deployment should use RollingUpdate strategy with maxSurge=1, and maxUnavailable=2.
Next upgrade the deployment to version 1.17 using rolling update.
Finally, once all pods are updated, undo the update and go back to the previous version

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