# node

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [list node with label](node.md#list-node-with-label)
  * [update label of node](node.md#update-label-of-node)
* [show](node.md#show)
  * [show with labels](node.md#show-with-labels)
  * [show particular labels](node.md#show-particular-labels)
  * [show with particular columns](node.md#show-with-particular-columns)
  * [show only scheduled nodes](node.md#show-only-scheduled-nodes)
* [sort](node.md#sort)
  * [sort via kubelet version](node.md#sort-via-kubelet-version)

## list node with label

```bash
$ k get no -l <label>=<value>
```

### update label of node

```bash
$ k label no <node-name> <label>=<value> [--overwrite]
```

## show

### show with labels

```bash
$ k get no --show-labels
```

### show particular labels

* `-label-columns`

  ```bash
  $ k get no --label-columns <label-name>
  ```

  * e.g.:

    ```bash
    $ k4 get nodes --label-columns jenkins
    NAME          STATUS    ROLES    AGE     VERSION   JENKINS
    k8s-node01    Ready     worker   545d    v1.12.3
    k8s-node02    Ready     worker   597d    v1.12.3
    k8s-node03    Ready     worker   217d    v1.12.3
    k8s-node04    Ready     worker   52d     v1.12.3
    k8s-node05    Ready     worker   589d    v1.12.3
    k8s-node06    Ready     master   2y33d   v1.12.3   master
    k8s-node07    Ready     master   589d    v1.12.3
    k8s-node08    Ready     worker   535d    v1.12.3
    ```

* `-l`

  ```bash
  $ k get no --show-labels -l node-role.kubernetes.io/master
  ```

### show with particular columns

```bash
$ k get no -o custom-columns=NAME:.metadata.name,VER:.status.nodeInfo.kubeletVersion
NAME          VER
k8s-node01    v1.12.3
k8s-node02    v1.12.3
k8s-node03    v1.12.3
...
```

### show only scheduled nodes

```bash
$ k get no \
        --output 'jsonpath={range $.items[*]}{.metadata.name} {.spec.taints[*].effect}{"\n"}{end}' \
        | awk '!/NoSchedule/{print $1}'
```

## sort

### sort via kubelet version

```bash
$ k get node --sort-by={.status.nodeInfo.kubeletVersion}
```

* or

  ```bash
  $ k get nodes --sort-by={.metadata.labels."kubernetes\.io\/role"}
  ```

