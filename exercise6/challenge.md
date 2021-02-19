# Quicklabs 6

## Issue

We have deployed a few pods in this cluster in various namespaces. 
Inspect them and identify the pod which is not in a Ready state. Troubleshoot and fix the issue.

Next, add a check to restart the container on the same pod if the command ls /var/www/html/file_check fails. 
This check should start after a delay of 10 seconds and run every 60 seconds.

You may delete and recreate the object. Ignore the warnings from the probe.

## Solution

The `readinessProbe` port is different from `containerPort`. Change the port to `9080` solves the problem.

The check is a `livenessProbe`:

```yaml
livenessProbe:
  failureThreshold: 1
  periodSeconds: 60
  initialDelaySeconds: 10
  timeoutSeconds: 3
  exec:
    command:
      - ls
      - /var/www/html/file_check
```