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

- [Visitors operators](./operators/visitors_dashboard/challenge.md)


---

We have deployed a few pods in this cluster in various namespaces. Inspect them and identify the pod which is not in a Ready state. Troubleshoot and fix the issue.

Next, add a check to restart the container on the same pod if the command ls /var/www/html/file_check fails. This check should start after a delay of 10 seconds and run every 60 seconds.

You may delete and recreate the object. Ignore the warnings from the probe.

---

Create a cronjob called dice that runs every one minute. Use the Pod template located at /root/throw-a-dice. The image throw-dice randomly returns a value between 1 and 6. The result of 6 is considered success and all others are failure.
The job should be non-parallel and complete the task once. Use a backoffLimit of 25.
If the task is not completed within 20 seconds the job should fail and pods should be terminated.

---

Create a pod called my-busybox in the dev2406 namespace using the busybox image. The container should be called secret and should sleep for 3600 seconds.

The container should mount a read-only secret volume called secret-volume at the path /etc/secret-volume. The secret being mounted has already been created for you and is called dotfile-secret.

Make sure that the pod is scheduled on master/controlplane and no other node in the cluster.

---

Create a single ingress resource called ingress-vh-routing. The resource should route HTTP traffic to multiple hostnames as specified below:

The service video-service should be accessible on http://watch.ecom-store.com:30093/video

The service apparels-service should be accessible on http://apparels.ecom-store.com:30093/wear

Here 30093 is the port used by the Ingress Controller

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

