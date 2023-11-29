Stworzenie podstawowego pliku yaml i jego edycja w edytorze:

```sh
kubectl create deploy labx --image=nginx:1.9 --replicas=5  --dry-run=client -o yaml > deploy.yaml
```

Stworzenie deploymentu zgodnego z zadaniem:
```sh
kubectl apply -f deploy.yaml
```

Sprawdzenie poprawności stworzenia deploymentu:

```sh
kubectl get deployments
```

Wynik operacji:
```sh
$ kubectl get deployments
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
labx               5/5     5            5           13s
```


Kolejne polecenie:

```sh
$ kubectl describe deploy labx
```

Wynik:

```sh
Name:                   labx
Namespace:              default
CreationTimestamp:      Wed, 29 Nov 2023 10:55:24 +0100
Labels:                 app=labx
                        type=proxy
Annotations:            deployment.kubernetes.io/revision: 1
Selector:               app=labx,type=proxy
Replicas:               5 desired | 5 updated | 5 total | 5 available | 0 unavailable
StrategyType:           RollingUpdate
MinReadySeconds:        0
RollingUpdateStrategy:  2 max unavailable, 25% max surge
Pod Template:
  Labels:  app=labx
           type=proxy
  Containers:
   nginx:
    Image:        nginx:1.9
    Port:         <none>
    Host Port:    <none>
    Environment:  <none>
    Mounts:       <none>
  Volumes:        <none>
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Available      True    MinimumReplicasAvailable
  Progressing    True    NewReplicaSetAvailable
OldReplicaSets:  <none>
NewReplicaSet:   labx-5dcb74f88b (5/5 replicas created)
Events:
  Type    Reason             Age   From                   Message
  ----    ------             ----  ----                   -------
  Normal  ScalingReplicaSet  2m1s  deployment-controller  Scaled up replica set labx-5dcb74f88b to 5
```