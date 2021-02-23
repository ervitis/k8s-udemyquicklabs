# Udemy K8S CKAD quick labs

## Requirements:

- Minikube for local development or your K8S environment
- kubectl
- Optional: Helm

## Challenges

- [QuickLab 1](./exercise1/challenge.md)
- [QuickLab 2](./exercise2/challenge.md)
- [QuickLab 3](./exercise3/challenge.md)
- [QuickLab 4](./exercise4/challenge.md)
- [QuickLab 5](./exercise5/challenge.md)
- [QuickLab 6](./exercise6/challenge.md)
- [QuickLab 7](./exercise7/challenge.md)
- [QuickLab 8](./exercise8/challenge.md)
- [QuickLab 9](./exercise9/challenge.md)

- [Visitors operators](./operators/visitors_dashboard/challenge.md)


---

A pod called dev-pod-dind-878516 has been deployed in the default namespace. 
Inspect the logs for the container called log-x and redirect the warnings to /opt/dind-878516_logs.txt on the master node


apiVersion: v1
kind: Pod
metadata:
  annotations:
  labels:
    run: dev-pod-dind-878516
  name: dev-pod-dind-878516
  namespace: default
spec:
  containers:
  - image: nginx
    imagePullPolicy: Always
    name: engine-x
    resources: {}
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: default-token-fsl9n
      readOnly: true
  - command:
    - sleep
    - "3600"
    image: ubuntu
    imagePullPolicy: Always
    name: agent-x
    resources: {}
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: default-token-fsl9n
      readOnly: true
  - image: kodekloud/event-simulator
    imagePullPolicy: Always
    name: log-x
    resources: {}
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: default-token-fsl9n
      readOnly: true
  dnsPolicy: ClusterFirst
  enableServiceLinks: true
  nodeName: node01
  restartPolicy: Always
  schedulerName: default-scheduler
  securityContext: {}
  serviceAccount: default
  serviceAccountName: default
  terminationGracePeriodSeconds: 30

