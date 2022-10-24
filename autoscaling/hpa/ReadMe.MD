### Create a K8S cluster using minikube
```minikube start```

```minikube addons enable metrics-server```

### Run and expose php-apache server 
```kubectl apply -f https://k8s.io/examples/application/php-apache.yaml```

### Create a HorizontalPodAutoscaler 
```kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10```

### Increase the load 
```kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"```


### Resources:
1. [Horizontal Pod Autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)
2. [HorizontalPodAutoscaler Walkthrough](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/)
3. [Autoscaling in Kubernetes - Part 2 | Kubernetes Tutorial - Analytics Excellence](https://www.youtube.com/watch?v=qOeeWdavdA0)