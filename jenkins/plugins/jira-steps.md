# jira-steps

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [get field](jira-steps.md#get-field)
* [get issue](jira-steps.md#get-issue)

## [get field](https://jenkinsci.github.io/jira-steps-plugin/steps/issue/jira_get_fields/)

```groovy
import static groovy.json.JsonOutput.*

def fields = jiraGetFields idOrKey: 'MYJIRA-1', site: 'jira'
println prettyPrint( toJson( fields.data ))
```

## [get issue](https://jenkinsci.github.io/jira-steps-plugin/steps/issue/jira_get_issue/)

```groovy
def issue = jiraGetIssue idOrKey: 'MYJIRA-1', site: 'jira'
println issue.data
```

