# events

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [get info](events.md#get-info)
  * [list all warning events](events.md#list-all-warning-events)
  * [list particular events](events.md#list-particular-events)

## get info

### list all warning events

```bash
$ kubectl get events --field-selector type=Warning --all-namespaces --sort-by='{.lastTimestamp}'
```

### list particular events

```bash
$ k get event --field-selector=involvedObject.name =foo -w
```

