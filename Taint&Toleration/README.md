# TAINT AND TOLERATION

```
controlplane ~ ➜  k get nodes
NAME           STATUS   ROLES           AGE   VERSION
controlplane   Ready    control-plane   44m   v1.27.0
node01         Ready    <none>          43m   v1.27.0
```

```k taint nodes node01 storage=ssd:NoSchedule```

=> This will Create a tain on node01, and pods will not be scheduled on it

### Create a simple nginx pod

``kubectl run --image=nginx``

```controlplane ~ ➜  k get pods
NAME    READY   STATUS    RESTARTS   AGE
nginx   0/1     Pending   0          3s
```

### Create a deployment with toleration and see if it runs

As you can see in the manifest file in the container spec section:

```tolerations:
      - key: "storage"
        operator: "Equal"
        value: "ssd"
        effect: "NoSchedule"
```
And with thi toleration th deployment will run on node01

```controlplane ~ ➜  k get pods -w
NAME                                READY   STATUS    RESTARTS   AGE
nginx                               0/1     Pending   0          4m8s
taint-toleration-77d579fb4f-dk6f6   1/1     Running   0          7s
```

### Remove the taint from the node
Follow up the command with hypehn '-'

```controlplane ~ ➜  k taint nodes node01 storage=ssd:NoSchedule- node/node01 untainted```
