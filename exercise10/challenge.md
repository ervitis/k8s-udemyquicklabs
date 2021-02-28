# Challenge 10

## Issue

A pod called dev-pod-dind-878516 has been deployed in the challenge10 namespace. 
Inspect the logs for the container called log-x and redirect the warnings to /opt/dind-878516_logs.txt 
on the master node

## Solution

Use the following command:

```bash
kubectl -n quicklabs10 exec -ti dev-pod-dind-878516 -c log-x | grep WARNING > /opt/dind-878516_logs.txt
```