## Trigger

### Poll SCM
```groovy
properties([
    // every 6 hours
    pipelineTriggers([
        pollSCM( ignorePostCommitHooks: true, scmpoll_spec: 'H H/6 * * *' )
    ])
])
```

```groovy
properties([
    pipelineTriggers([
        [ $class: "SCMTrigger", scmpoll_spec: 'H/5 * * * *' ],
    ])
])
```

- Dec

    ```groovy
    triggers {
        pollSCM ignorePostCommitHooks: true, scmpoll_spec: 'H H * * *'
    }
    ```
