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

- declarative:

    ```groovy
    triggers {
        pollSCM ignorePostCommitHooks: true, scmpoll_spec: 'H H * * *'
    }
    ```

### Triggered by

- [gitlab](https://stackoverflow.com/a/55366682/2940319)
```groovy
currentBuild.rawBuild.getCause(com.dabsquared.gitlabjenkins.cause.GitLabWebHookCause).getData()
// or
commit = currentBuild.rawBuild.getCause(com.dabsquared.gitlabjenkins.cause.GitLabWebHookCause).getData().getLastCommit()
```
