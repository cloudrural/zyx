# INC-KN-00001

**Name**</br>
etcdInsufficientMembers

**Description**</br>
> an especially critical scenario. For instance, if there is a cluster of 5 etcd nodes, this would imply that less than 3 nodes are up. As soon as this expression evaluates true, Prometheus will mark this as “Pending”. Once three minutes pass, an alert will begin “Firing”.
> Hello Veeru

**Steps:**</br>
* first
* second

```bash
$ ./hello so.py
$ ps -ef

```

`
ps -ef
` Please execute this




**When to perform the steps:**</br>

**Any side effects of performing above steps:**</br>


1) Determine the name of the cluster from Alert.

2) Check the actual status of prometheus-alertmanager pod from your cluster using the commands below.
    ```bash
    $ kubectl get pods --kubeconfig=<kube-config-file> -n monitoring
    ```
b) Get the name of container, from the container section. These can be used to fetch the logs

3) Check the logs of containers:
   ```bash
   $ kubectl logs <prometheus-alertmanager-pod> -c alertmanager -kubeconfig=<kube-config-file> -n monitoring
   ```

4) Check the active configmap for the running instance of alertmanager:
kubectl describe configmaps prometheus-alertmanager -kubeconfig=<kube-config-file> -n monitoring

5) The configuration files are stored on PVC (persistent volume claim) - monitoring/prometheus-server. Check if the PVC status is Bound:

`kubectl describe pvc prometheus-server -n monitoring`

6) Try to recreate prometheus-server pod:
`kubectl delete pod <prometheus-server-pod> -n monitoring`
