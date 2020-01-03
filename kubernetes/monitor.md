## Grafana

### [reset password](https://grafana.com/docs/grafana/latest/administration/cli/)
```bash
$ curl -X PUT -H "Content-Type: application/json" -d '{
  "oldPassword": "admin",
  "newPassword": "newpass",
  "confirmNew": "newpass"
}' http://admin:admin@<your_grafana_host>:3000/api/user/password
```

### Environment
```bash
# for pvc
$ mkdir -p /opt/grafana/plugins
$ sudo chwon -R 472:472 $_

# https://grafana.com/docs/grafana/latest/installation/docker/#migration-from-a-previous-version-of-the-docker-container-to-5-1-or-later
# 104:104 for version < 5.1
```
- [User ID changes](https://grafana.com/docs/grafana/latest/installation/docker/#user-id-changes)

|  Version |   User  | User ID |
|:--------:|:-------:|:-------:|
|  `< 5.1` | grafana |  `104`  |
| `>= 5.1` | grafana |  `472`  |


### Setup
- ns
    ```bash
    $ cat << EOF | kubectl apply -f -
    ---
    kind: Namespace
    apiVersion: v1
    metadata:
      name: kubernetes-dashboard
      labels:
        name: kubernetes-dashboard
    EOF
    ```
- sa
    ```bash

    ```
- pv & pvc
    ```bash

    ```
- deploy
    ```bash

    ```
- svc
    ```bash

    ```
- ing
    ```bash

    ```

## Reference
- [Scaling out Grafana with Kubernetes and AWS](https://medium.com/@fcgravalos/scaling-out-grafana-with-kubernetes-and-aws-62745257df10)
- [How To Setup Grafana On Kubernetes](https://devopscube.com/setup-grafana-kubernetes/)
- [Monitoring Kubernetes Clusters with Grafana](https://medium.com/htc-research-engineering-blog/monitoring-kubernetes-clusters-with-grafana-e2a413febefd)

## Code Pool
- [kubeless/manifests/monitoring](https://github.com/kubeless/kubeless/tree/master/manifests/monitoring)
- [kube-prometheus/manifests](https://github.com/coreos/kube-prometheus/tree/master/manifests)
- [kubernetes-handbook/manifests/prometheus](https://github.com/rootsongjc/kubernetes-handbook/tree/master/manifests/prometheus)
