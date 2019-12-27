### [List Pods name](https://stackoverflow.com/a/51612372/2940319)

- `-o name`

    ```bash
    $ kubectl -n kube-system get pods -o name | head
    pod/coredns-c7ddbcccb-5cj5z
    pod/coredns-c7ddbcccb-lxsw6
    pod/coredns-c7ddbcccb-prjfk
    pod/etcd-node03
    pod/etcd-node04
    pod/etcd-node01
    pod/kube-apiserver-node03
    pod/kube-apiserver-node04
    pod/kube-apiserver-node01
    pod/kube-controller-manager-node03
    ```

- `--template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}'`

    ```bash
    $ kubectl -n kube-system get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}' | head
    coredns-c7ddbcccb-5cj5z
    coredns-c7ddbcccb-lxsw6
    coredns-c7ddbcccb-prjfk
    etcd-node03
    etcd-node04
    etcd-node01
    kube-apiserver-node03
    kube-apiserver-node04
    kube-apiserver-node01
    kube-controller-manager-node03

    # OR

    $ kubectl -n kube-system get pods --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}' | head
    coredns-c7ddbcccb-5cj5z
    coredns-c7ddbcccb-lxsw6
    coredns-c7ddbcccb-prjfk
    etcd-node03
    etcd-node04
    etcd-node01
    kube-apiserver-node03
    kube-apiserver-node04
    kube-apiserver-node01
    kube-controller-manager-node03
    ```
