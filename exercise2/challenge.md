# Quicklabs 2

## Issue

We have deployed a new pod called `secure-pod`, and a service called `secure-service`. 
Incoming or Outgoing connections to this pod are not working.
Troubleshoot why this is happening.

Make sure that incoming connection from the pod `webapp-color` are successful.

Important: Don't delete any current objects deployed.

## Solution

1. Assign containerPods in the pods and services
2. Create a network policy (file `net-policy.yaml`) to assign an ingress policy to connect the `webapp-color` to `secure-service`