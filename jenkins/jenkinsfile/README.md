# jenkinsfile

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [jenkins API](./#jenkins-api)
  * [update node name](./#update-node-name)
  * [raw build](./#raw-build)
  * [manager.build.result.isBetterThan](./#managerbuildresultisbetterthan)
* [customized build](./#customized-build)
  * [display name](./#display-name)
  * [description](./#description)

{% hint style="info" %}
> reference:
>
> * [Pipeline Examples](https://www.jenkins.io/doc/pipeline/examples/)
> * [Jenkins Pipeline Syantx](https://kb.novaordis.com/index.php/Jenkins_Pipeline_Syntax)
> * [Pipeline Steps Reference](https://www.jenkins.io/doc/pipeline/steps/)
> * [Pipeline Utility Steps](https://www.jenkins.io/doc/pipeline/steps/pipeline-utility-steps/#pipeline-utility-steps)
> * [Jenkins Pipeline Cookbook](https://e.printstacktrace.blog/jenkins-pipeline-cookbook/)
{% endhint %}

## jenkins API

### update node name

* get label

  ```groovy
  @NonCPS
  def getLabel(){
    for (node in jenkins.model.Jenkins.instance.nodes) {
      if (node.getNodeName().toString().equals("${env.NODE_NAME}".toString())) {
        currentLabel = node.getLabelString()
        return currentLabel
      }
    }
  }
  ```

* set label

  ```groovy
  @NonCPS
  def updateLabel(nodeName, newLabel) {
    def node = jenkins.model.Jenkins.instance.getNode(nodeName)
    if (node) {
      node.setLabelString(newLabel)
      node.save()
    }
  }
  ```

* Jenkinsfile Example

  ```groovy
  String curLabel       = null
  String newLabel       = null
  String testNodeName   = null
  String curProject     = env.JOB_NAME
  String curBuildNumber = env.BUILD_NUMBER

  node("master") {
    try{
      stage("reserve node") {
        node("${params.tmNode}") {
          testNodeName = env.NODE_NAME
          curLabel  = getLabel()
          newLabel = "${curLabel}~running_${curProject}#${curBuildNumber}"
          echo "~~> lock ${testNodeName}. update lable: ${curLabel} ~> ${newLabel}"
          updateLabel(testNodeName, newLabel)
        } // node
      } // reserve stage
    } finally {
    if (newLabel) {
      stage("release node") {
        nodeLabels = "${newLabel}".split('~')
        orgLabel = nodeLabels[0]
        echo "~~> release ${testNodeName}. update lable ${newLabel} ~> ${orgLabel}"
        updateLabel(testNodeName, orgLabel)
      } // release stage
    } // if
  } // finally
  ```

### raw build

```groovy
Map buildResult = [:]

node("master") {
  buildResult = build job: '/marslo/artifactory-lib',
                      propagate: true,
                      wait: true
  buildResult.each { println it }

  println """
    ~~> "result" : ${buildResult.result}
    ~~> "getBuildVariables()" : ${buildResult.getBuildVariables()}
    ~~> "getBuildVariables().mytest" : ${buildResult.getBuildVariables().mytest}
    ~~> "getRawBuild().getEnvVars()" : ${buildResult.getRawBuild().getEnvVars()}
    ~~> "getRawBuild().getEnvironment()" : ${buildResult.getRawBuild.getEnvironment()}
    ~~> "rawBuild.environment.RUN_CHANGES_DISPLAY_URL" : ${buildResult.rawBuild.environment.RUN_CHANGES_DISPLAY_URL}
    ~~> "getBuildCauses()" : ${buildResult.getBuildCauses()}
    ~~> "getChangeSets()" : ${buildResult.getChangeSets()}
    ~~> "buildVariables["mytest"]" : ${buildResult.buildVariables["mytest"]}
    ~~> "buildResult.rawBuild": ${buildResult.rawBuild}
    ~~> "buildResult.rawBuild.log": ${buildResult.rawBuild.log}
  """
} // node
```

### [manager.build.result.isBetterThan](https://stackoverflow.com/a/26410694/2940319)

```groovy
if(manager.build.result.isBetterThan(hudson.model.Result.UNSTABLE)) {
  def cmd = 'ssh -p 29418 $host gerrit review --verified +1 --code --review +2 --submit $GERRIT_CHANGE_NUMBER,$GERRIT_PATCHSET_NUMBER'
  cmd = manager.build.environment.expand(cmd)
  manager.listener.logger.println("Merge review: '$cmd'")
  def p = "$cmd".execute()
  manager.listener.logger.println(p.in.text)
  manager.addShortText("M")
}
```

## customized build

### display name

```groovy
currentBuild.displayName = '#' + Integer.toString(currentBuild.number) + ' mytest'
```

![customized display name](../../.gitbook/assets/showDisplayName.png)

### description

```groovy
currentBuild.description = 'this is whitebox'
```

