# replicasets

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [list](replicaset.md#list)
  * [list redundant rs](replicaset.md#list-redundant-rs)
  * [remove useless replicasets](replicaset.md#remove-useless-replicasets)

## list

### list redundant rs

```bash
$ k -n <namespace> get rs | awk '{if ($2 + $3 + $4 == 0) print $1}'
```

### [remove useless replicasets](https://stackoverflow.com/a/65154332/2940319)

```bash
$ k -n <namespaced> delete rs $(k -n <namespace> get rs | awk '{if ($2 + $3 + $4 == 0) print $1}')
```

