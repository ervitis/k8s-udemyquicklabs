# Quicklabs 5

## Issue

Create a redis deployment with the following parameters:
Name of the deployment should be redis using the redis:alpine image. It should have exactly 1 replica.
The container should request for .2 CPU. It should use the label app=redis.
It should mount exactly 2 volumes:
Make sure that the pod is scheduled on master/controlplane node.

- An Empty directory volume called data at path /redis-master-data.
- A configmap volume called redis-config at path /redis-master.
- The container should expose the port 6379.