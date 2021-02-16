# Quicklabs 4

## Issue

Create a new deployment called nginx-deploy, with one signle container called nginx, image nginx:1.16 and 4 replicas. The deployment should use RollingUpdate strategy with maxSurge=1, and maxUnavailable=2.
Next upgrade the deployment to version 1.17 using rolling update.
Finally, once all pods are updated, undo the update and go back to the previous version

## Solution

Update the image to the desired and watch the pods scaling

```bash
kubectl -n quicklabs4 set image deployment.v1.apps/nginx-deploy nginx-deploy=nginx:1.17 --record=true 
```

See the history of the rollout

```bash
kubectl -n quicklabs4 rollout history deployment.v1.apps/nginx-deploy
```

Undo the last action

```bash
kubectl -n quicklabs4 rollout undo deployment.v1.apps/nginx-deploy
```
