# Debugging-DEVOPS
I will be debugging and recording the solutions in this repo to help you and me with saving time.


## 1-`Caused: hudson.remoting.ProxyException: java.lang.IllegalStateException: Unable to parse response from http://127.0.0.1:9000//api/ce/task?id=AYblxjKRVR_8us7BcEFR:` during sonar quality gate analysis

After examining the console output and stackoverflow, went ahead to manege jenkins--> global tool configuration-->SonarQube servers
Removed the trailing forward slash. Verified that i could get response from the api and ran the build again.

<details>
  <summary>See the log</summary>
  
```
hudson.remoting.ProxyException: net.sf.json.JSONException: Invalid JSON String
	at net.sf.json.JSONSerializer.toJSON(JSONSerializer.java:143)
	at net.sf.json.JSONSerializer.toJSON(JSONSerializer.java:103)
	at net.sf.json.JSONSerializer.toJSON(JSONSerializer.java:84)
	at hudson.plugins.sonar.client.WsClient.getCETask(WsClient.java:53)
	at org.sonarsource.scanner.jenkins.pipeline.WaitForQualityGateStep$Execution.checkTaskCompleted(WaitForQualityGateStep.java:240)
	at org.sonarsource.scanner.jenkins.pipeline.WaitForQualityGateStep$Execution.start(WaitForQualityGateStep.java:176)
	at org.jenkinsci.plugins.workflow.cps.DSL.invokeStep(DSL.java:322)
	at org.jenkinsci.plugins.workflow.cps.DSL.invokeMethod(DSL.java:196)
	at org.jenkinsci.plugins.workflow.cps.CpsScript.invokeMethod(CpsScript.java:124)
	at jdk.internal.reflect.GeneratedMethodAccessor648.invoke(Unknown Source)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:98)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:325)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1225)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1034)
	at org.codehaus.groovy.runtime.callsite.PogoMetaClassSite.call(PogoMetaClassSite.java:41)
	at org.codehaus.groovy.runtime.callsite.CallSiteArray.defaultCall(CallSiteArray.java:47)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:116)
	at org.kohsuke.groovy.sandbox.impl.Checker$1.call(Checker.java:180)
	at org.kohsuke.groovy.sandbox.GroovyInterceptor.onMethodCall(GroovyInterceptor.java:23)
	at org.jenkinsci.plugins.scriptsecurity.sandbox.groovy.SandboxInterceptor.onMethodCall(SandboxInterceptor.java:163)
	at org.kohsuke.groovy.sandbox.impl.Checker$1.call(Checker.java:178)
	at org.kohsuke.groovy.sandbox.impl.Checker.checkedCall(Checker.java:182)
	at org.kohsuke.groovy.sandbox.impl.Checker.checkedCall(Checker.java:152)
	at org.kohsuke.groovy.sandbox.impl.Checker.checkedCall(Checker.java:152)
	at com.cloudbees.groovy.cps.sandbox.SandboxInvoker.methodCall(SandboxInvoker.java:17)
Caused: hudson.remoting.ProxyException: java.lang.IllegalStateException: Unable to parse response from http://127.0.0.1:9000//api/ce/task?id=AYblxjKRVR_8us7BcEFR:

<!DOCTYPE html>
<html lang="en">

<head>
    <meta http-equiv="content-type" content="text/html; charset=UTF-8" charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <link rel="apple-touch-icon" href="/apple-touch-icon.png">
    <link rel="apple-touch-icon" sizes="57x57" href="/apple-touch-icon-57x57.png">
    <link rel="apple-touch-icon" sizes="60x60" href="/apple-touch-icon-60x60.png">
    <link rel="apple-touch-icon" sizes="72x72" href="/apple-touch-icon-72x72.png">
    <link rel="apple-touch-icon" sizes="76x76" href="/apple-touch-icon-76x76.png">
    <link rel="apple-touch-icon" sizes="114x114" href="/apple-touch-icon-114x114.png">
    <link rel="apple-touch-icon" sizes="120x120" href="/apple-touch-icon-120x120.png">
    <link rel="apple-touch-icon" sizes="144x144" href="/apple-touch-icon-144x144.png">
    <link rel="apple-touch-icon" sizes="152x152" href="/apple-touch-icon-152x152.png">
    <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon-180x180.png">
    <link rel="icon" type="image/x-icon" href="/favicon.ico">
    <meta name="application-name" content="SonarQube" />
    <meta name="msapplication-TileColor" content="#FFFFFF" />
    <meta name="msapplication-TileImage" content="/mstile-512x512.png" />
    <title>SonarQube</title>

    <link rel="stylesheet" href="/js/outV5A3AQEU.css" />
</head>

<body>
    <div id="content">
        <div class="global-loading">
            <i class="spinner global-loading-spinner"></i> 
            <span aria-live="polite" class="global-loading-text">Loading...</span>
        </div>
    </div>

    <script>
        window.baseUrl = '';
        window.serverStatus = 'UP';
        window.instance = 'SonarQube';
        window.official = true;
    </script>

    <script type="module" src="/js/outL2Z6DMVA.js"></script>
</body>

</html>

	at hudson.plugins.sonar.client.WsClient.getCETask(WsClient.java:63)
	at org.sonarsource.scanner.jenkins.pipeline.WaitForQualityGateStep$Execution.checkTaskCompleted(WaitForQualityGateStep.java:240)
	at org.sonarsource.scanner.jenkins.pipeline.WaitForQualityGateStep$Execution.start(WaitForQualityGateStep.java:176)
	at org.jenkinsci.plugins.workflow.cps.DSL.invokeStep(DSL.java:322)
	at org.jenkinsci.plugins.workflow.cps.DSL.invokeMethod(DSL.java:196)
	at org.jenkinsci.plugins.workflow.cps.CpsScript.invokeMethod(CpsScript.java:124)
	at jdk.internal.reflect.GeneratedMethodAccessor648.invoke(Unknown Source)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:98)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:325)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1225)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1034)
	at org.codehaus.groovy.runtime.callsite.PogoMetaClassSite.call(PogoMetaClassSite.java:41)
	at org.codehaus.groovy.runtime.callsite.CallSiteArray.defaultCall(CallSiteArray.java:47)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:116)
	at org.kohsuke.groovy.sandbox.impl.Checker$1.call(Checker.java:180)
	at org.kohsuke.groovy.sandbox.GroovyInterceptor.onMethodCall(GroovyInterceptor.java:23)
	at org.jenkinsci.plugins.scriptsecurity.sandbox.groovy.SandboxInterceptor.onMethodCall(SandboxInterceptor.java:163)
	at org.kohsuke.groovy.sandbox.impl.Checker$1.call(Checker.java:178)
	at org.kohsuke.groovy.sandbox.impl.Checker.checkedCall(Checker.java:182)
	at org.kohsuke.groovy.sandbox.impl.Checker.checkedCall(Checker.java:152)
	at org.kohsuke.groovy.sandbox.impl.Checker.checkedCall(Checker.java:152)
	at com.cloudbees.groovy.cps.sandbox.SandboxInvoker.methodCall(SandboxInvoker.java:17)
	at WorkflowScript.run(WorkflowScript:35)
	at ___cps.transform___(Native Method)
	at com.cloudbees.groovy.cps.impl.ContinuationGroup.methodCall(ContinuationGroup.java:90)
	at com.cloudbees.groovy.cps.impl.FunctionCallBlock$ContinuationImpl.dispatchOrArg(FunctionCallBlock.java:116)
	at com.cloudbees.groovy.cps.impl.FunctionCallBlock$ContinuationImpl.fixArg(FunctionCallBlock.java:85)
	at jdk.internal.reflect.GeneratedMethodAccessor304.invoke(Unknown Source)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at com.cloudbees.groovy.cps.impl.ContinuationPtr$ContinuationImpl.receive(ContinuationPtr.java:72)
	at com.cloudbees.groovy.cps.impl.CollectionLiteralBlock$ContinuationImpl.dispatch(CollectionLiteralBlock.java:55)
	at com.cloudbees.groovy.cps.impl.CollectionLiteralBlock$ContinuationImpl.item(CollectionLiteralBlock.java:45)
	at jdk.internal.reflect.GeneratedMethodAccessor309.invoke(Unknown Source)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at com.cloudbees.groovy.cps.impl.ContinuationPtr$ContinuationImpl.receive(ContinuationPtr.java:72)
	at com.cloudbees.groovy.cps.impl.ConstantBlock.eval(ConstantBlock.java:21)
	at com.cloudbees.groovy.cps.Next.step(Next.java:83)
	at com.cloudbees.groovy.cps.Continuable$1.call(Continuable.java:152)
	at com.cloudbees.groovy.cps.Continuable$1.call(Continuable.java:146)
	at org.codehaus.groovy.runtime.GroovyCategorySupport$ThreadCategoryInfo.use(GroovyCategorySupport.java:136)
	at org.codehaus.groovy.runtime.GroovyCategorySupport.use(GroovyCategorySupport.java:275)
	at com.cloudbees.groovy.cps.Continuable.run0(Continuable.java:146)
	at org.jenkinsci.plugins.workflow.cps.SandboxContinuable.access$001(SandboxContinuable.java:18)
	at org.jenkinsci.plugins.workflow.cps.SandboxContinuable.run0(SandboxContinuable.java:51)
	at org.jenkinsci.plugins.workflow.cps.CpsThread.runNextChunk(CpsThread.java:187)
	at org.jenkinsci.plugins.workflow.cps.CpsThreadGroup.run(CpsThreadGroup.java:420)
	at org.jenkinsci.plugins.workflow.cps.CpsThreadGroup$2.call(CpsThreadGroup.java:330)
	at org.jenkinsci.plugins.workflow.cps.CpsThreadGroup$2.call(CpsThreadGroup.java:294)
	at org.jenkinsci.plugins.workflow.cps.CpsVmExecutorService$2.call(CpsVmExecutorService.java:67)
	at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
	at hudson.remoting.SingleLaneExecutorService$1.run(SingleLaneExecutorService.java:139)
	at jenkins.util.ContextResettingExecutorService$1.run(ContextResettingExecutorService.java:28)
	at jenkins.security.ImpersonatingExecutorService$1.run(ImpersonatingExecutorService.java:68)
	at jenkins.util.ErrorLoggingExecutorService.lambda$wrap$0(ErrorLoggingExecutorService.java:51)
	at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
	at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)
Finished: FAILURE
```

</details>


![image](https://user-images.githubusercontent.com/96833570/225352229-921d4267-8ce9-446a-a006-a5f112c5e5c7.png)


## 2 `fatal: detected dubious ownership in repository at '/var/lib/jenkins/workspace/java-app-cli-pipeline'` and `WARNING: buildx: failed to read current commit information with git rev-parse --is-inside-work-tree` during docker build manual check

I encountered these errors while preparing a CI/CD project for a java maven app. I needed to test the multistage dockerfile manually before automating the build with jenkins. Solved this error running the following command:

```
 git config --global --add safe.directory '*'
```

<details>
  <summary>See the log</summary>
  
  ```
  [+] Building 180.3s (14/14) FINISHED
 => [internal] load build definition from Dockerfile                                                                                 0.0s
 => => transferring dockerfile: 373B                                                                                                 0.0s
 => [internal] load .dockerignore                                                                                                    0.0s
 => => transferring context: 2B                                                                                                      0.0s
 => [internal] load metadata for docker.io/library/openjdk:8-jre-alpine                                                              2.2s
 => [internal] load metadata for docker.io/library/maven:3.5.0-jdk-8-alpine                                                          1.5s
 => [auth] library/openjdk:pull token for registry-1.docker.io                                                                       0.0s
 => [stage-1 1/3] FROM docker.io/library/openjdk:8-jre-alpine@sha256:f362b165b870ef129cbe730f29065ff37399c0aa8bcab3e44b51c302938c  128.4s
 => => resolve docker.io/library/openjdk:8-jre-alpine@sha256:f362b165b870ef129cbe730f29065ff37399c0aa8bcab3e44b51c302938c9193        0.1s
 => => sha256:f362b165b870ef129cbe730f29065ff37399c0aa8bcab3e44b51c302938c9193 1.64kB / 1.64kB                                       0.0s
 => => sha256:b2ad93b079b1495488cc01375de799c402d45086015a120c105ea00e1be0fd52 947B / 947B                                           0.0s
 => => sha256:f7a292bbb70c4ce57f7704cc03eb09e299de9da19013b084f138154421918cb4 3.42kB / 3.42kB                                       0.0s
 => => sha256:e7c96db7181be991f19a9fb6975cdbbd73c65f4a2681348e63a141a2192a5f10 2.76MB / 2.76MB                                      16.7s
 => => extracting sha256:e7c96db7181be991f19a9fb6975cdbbd73c65f4a2681348e63a141a2192a5f10                                            0.1s
 => => sha256:f910a506b6cb1dbec766725d70356f695ae2bf2bea6224dbe8c7c6ad4f3664a2 238B / 238B                                          17.3s
 => => extracting sha256:f910a506b6cb1dbec766725d70356f695ae2bf2bea6224dbe8c7c6ad4f3664a2                                            0.0s
 => => sha256:b6abafe80f63b02535fc111df2ed6b3c728469679ab654e03e482b6f347c9639 54.94MB / 54.94MB                                   127.7s
 => => extracting sha256:b6abafe80f63b02535fc111df2ed6b3c728469679ab654e03e482b6f347c9639                                            0.3s
 => [build 1/4] FROM docker.io/library/maven:3.5.0-jdk-8-alpine@sha256:c4c0f4b442d110b344f1ff759b945be03734596f76f7b164b567edabd8  146.0s
 => => resolve docker.io/library/maven:3.5.0-jdk-8-alpine@sha256:c4c0f4b442d110b344f1ff759b945be03734596f76f7b164b567edabd8841594    0.1s
 => => sha256:c4c0f4b442d110b344f1ff759b945be03734596f76f7b164b567edabd8841594 434B / 434B                                           0.0s
 => => sha256:6e753bb2ec6763bd6c1b08b811ddca7327ded09593b37abd28e72898742f3f6b 70.05MB / 70.05MB                                   144.7s
 => => sha256:b56ae66c29370df48e7377c8f9baa744a3958058a766793f821dadcb144a4647 1.99MB / 1.99MB                                       3.3s
 => => sha256:2296e775ba08de9d41d94164ff4d14bea2c4ad0074b0e395bc6ee35ff0534a5f 237B / 237B                                           1.2s
 => => sha256:013625dbbeab94365f4b1ff9b4f76b6ed078bb6faf4b00ae3ae987d296cd9cb6 1.78kB / 1.78kB                                       0.0s
 => => sha256:67d11473f554f1f193bbf361e81847063b2759d92e9ee42cbca1b07dee7982be 6.14kB / 6.14kB                                       0.0s
 => => sha256:38ea6e0113f4e80595d678bb5449cd9165bd7b0d580fbcc4bfb1fd614fd52353 1.77MB / 1.77MB                                       7.7s
 => => extracting sha256:b56ae66c29370df48e7377c8f9baa744a3958058a766793f821dadcb144a4647                                            0.1s
 => => sha256:ace0d91c026de783b02fd57bfc47087f2421dd15871062310849ca54630f26c2 8.67MB / 8.67MB                                      38.2s
 => => extracting sha256:2296e775ba08de9d41d94164ff4d14bea2c4ad0074b0e395bc6ee35ff0534a5f                                            0.0s
 => => sha256:7a5d216d8d5d4d2865c890de23ef68854bb2928e6c04497d84882e2293ef8bd0 731B / 731B                                           8.2s
 => => sha256:1bf6b634b77415131d1faac0b332c20b0562f4c5295fdb9cc3026ffbe1dc64aa 352B / 352B                                           8.5s
 => => extracting sha256:6e753bb2ec6763bd6c1b08b811ddca7327ded09593b37abd28e72898742f3f6b                                            0.3s
 => => extracting sha256:38ea6e0113f4e80595d678bb5449cd9165bd7b0d580fbcc4bfb1fd614fd52353                                            0.1s
 => => extracting sha256:ace0d91c026de783b02fd57bfc47087f2421dd15871062310849ca54630f26c2                                            0.1s
 => => extracting sha256:7a5d216d8d5d4d2865c890de23ef68854bb2928e6c04497d84882e2293ef8bd0                                            0.0s
 => => extracting sha256:1bf6b634b77415131d1faac0b332c20b0562f4c5295fdb9cc3026ffbe1dc64aa                                            0.0s
 => [internal] load build context                                                                                                    0.1s
 => => transferring context: 14.59kB                                                                                                 0.0s
 => [stage-1 2/3] WORKDIR /app                                                                                                       0.1s
 => [build 2/4] WORKDIR /app                                                                                                         0.1s
 => [build 3/4] COPY . .                                                                                                             0.1s
 => [build 4/4] RUN mvn install                                                                                                     31.6s
 => [stage-1 3/3] COPY --from=build /app/target/techops-pr-1.0-SNAPSHOT.jar /app/techops-pr-1.0-SNAPSHOT.jar                         0.1s
 => exporting to image                                                                                                               0.1s
 => => exporting layers                                                                                                              0.1s
 => => writing image sha256:2ab0f48a2fa12077ca4229c037b67e201caf3f6ee01119d1e29aae8b99ebe154                                         0.0s
 => => naming to docker.io/library/test-app                                                                                          0.0s
WARNING: buildx: failed to read current commit information with git rev-parse --is-inside-work-tree

```

```
  fatal: detected dubious ownership in repository at '/var/lib/jenkins/workspace/java-app-cli-pipeline'
To add an exception for this directory, call:

        git config --global --add safe.directory /var/lib/jenkins/workspace/java-app-cli-pipeline
  
  
  ```
  
</details>


![image](https://user-images.githubusercontent.com/96833570/225380412-cefc6b9c-40a5-4ff8-8704-035d812d3310.png)

