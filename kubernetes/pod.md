### [List Pods name](https://stackoverflow.com/a/51612372/2940319)

- `-o name`

    ```bash
    $ kubectl -n kube-system get pods -o name | head
    pod/coredns-c7ddbcccb-5cj5z
    pod/coredns-c7ddbcccb-lxsw6
    pod/coredns-c7ddbcccb-prjfk
    pod/etcd-dc5-ssdfw3
    pod/etcd-dc5-ssdfw4
    pod/etcd-ir-ssdfw1
    pod/kube-apiserver-dc5-ssdfw3
    pod/kube-apiserver-dc5-ssdfw4
    pod/kube-apiserver-ir-ssdfw1
    pod/kube-controller-manager-dc5-ssdfw3
    ```

- `--template`

    ```bash
    $ kubectl -n kube-system get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}' | head
    coredns-c7ddbcccb-5cj5z
    coredns-c7ddbcccb-lxsw6
    coredns-c7ddbcccb-prjfk
    etcd-dc5-ssdfw3
    etcd-dc5-ssdfw4
    etcd-ir-ssdfw1
    kube-apiserver-dc5-ssdfw3
    kube-apiserver-dc5-ssdfw4
    kube-apiserver-ir-ssdfw1
    kube-controller-manager-dc5-ssdfw3

    # OR

    $ kubectl -n kube-system get pods --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}' | head
    coredns-c7ddbcccb-5cj5z
    coredns-c7ddbcccb-lxsw6
    coredns-c7ddbcccb-prjfk
    etcd-dc5-ssdfw3
    etcd-dc5-ssdfw4
    etcd-ir-ssdfw1
    kube-apiserver-dc5-ssdfw3
    kube-apiserver-dc5-ssdfw4
    kube-apiserver-ir-ssdfw1
    kube-controller-manager-dc5-ssdfw3
    ```
