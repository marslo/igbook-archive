### Get name by label
```groovy
import org.jenkins.plugins.lockableresources.LockableResourcesManager;

String l = 'my-label'
def test_beds = new LockableResourcesManager().getResourcesWithLabel(l, null)
```

### [Get all resource](https://issues.jenkins-ci.org/browse/JENKINS-46235?focusedCommentId=345401&page=com.atlassian.jira.plugin.system.issuetabpanels%3Acomment-tabpanel#comment-345401)
```groovy
def all_lockable_resources = GlobalConfiguration.all().get(org.jenkins.plugins.lockableresources.LockableResourcesManager.class).resources
```
