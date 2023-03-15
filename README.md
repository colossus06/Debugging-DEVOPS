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

