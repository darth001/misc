# ReactNative


## react-native run-android

Problem:

```
michael@localhost:~/react/AwesomeProject $ react-native run-android
JS server not recognized, continuing with build...
Running adb reverse tcp:8081 tcp:8081
error: no devices/emulators found
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
Could not run adb reverse: Command failed: adb reverse tcp:8081 tcp:8081
Building and installing the app on the device (cd android && ./gradlew installDebug...
Failed to notify ProjectEvaluationListener.afterEvaluate(), but primary configuration failure takes precedence.
java.lang.RuntimeException: SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable.
	at com.android.build.gradle.internal.SdkHandler.getAndCheckSdkFolder(SdkHandler.java:102)
	at com.android.build.gradle.internal.SdkHandler.getSdkLoader(SdkHandler.java:112)
	at com.android.build.gradle.internal.SdkHandler.initTarget(SdkHandler.java:86)
	at com.android.build.gradle.BasePlugin.ensureTargetSetup(BasePlugin.groovy:507)
	at com.android.build.gradle.BasePlugin.createAndroidTasks(BasePlugin.groovy:455)
	at com.android.build.gradle.BasePlugin$_createTasks_closure13_closure17.doCall(BasePlugin.groovy:415)
	at com.android.build.gradle.BasePlugin$_createTasks_closure13_closure17.doCall(BasePlugin.groovy)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:90)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:324)
	at org.codehaus.groovy.runtime.metaclass.ClosureMetaClass.invokeMethod(ClosureMetaClass.java:292)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1015)
	at org.codehaus.groovy.runtime.callsite.PogoMetaClassSite.call(PogoMetaClassSite.java:39)
	at org.codehaus.groovy.runtime.callsite.CallSiteArray.defaultCall(CallSiteArray.java:45)
	at org.codehaus.groovy.runtime.callsite.PogoMetaClassSite.call(PogoMetaClassSite.java:54)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:112)
	at com.android.build.gradle.internal.profile.SpanRecorders$2.call(SpanRecorders.groovy:52)
	at com.android.builder.profile.ThreadRecorder$1.record(ThreadRecorder.java:48)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.codehaus.groovy.runtime.callsite.PojoMetaMethodSite$PojoCachedMethodSite.invoke(PojoMetaMethodSite.java:189)
	at org.codehaus.groovy.runtime.callsite.PojoMetaMethodSite.call(PojoMetaMethodSite.java:53)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:124)
	at com.android.build.gradle.internal.profile.SpanRecorders.record(SpanRecorders.groovy:54)
	at com.android.build.gradle.BasePlugin$_createTasks_closure13.doCall(BasePlugin.groovy:414)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:90)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:324)
	at org.codehaus.groovy.runtime.metaclass.ClosureMetaClass.invokeMethod(ClosureMetaClass.java:292)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1015)
	at groovy.lang.Closure.call(Closure.java:423)
	at org.gradle.listener.ClosureBackedMethodInvocationDispatch.dispatch(ClosureBackedMethodInvocationDispatch.java:40)
	at org.gradle.listener.ClosureBackedMethodInvocationDispatch.dispatch(ClosureBackedMethodInvocationDispatch.java:25)
	at org.gradle.internal.event.BroadcastDispatch.dispatch(BroadcastDispatch.java:87)
	at org.gradle.internal.event.BroadcastDispatch.dispatch(BroadcastDispatch.java:31)
	at org.gradle.messaging.dispatch.ProxyDispatchAdapter$DispatchingInvocationHandler.invoke(ProxyDispatchAdapter.java:93)
	at com.sun.proxy.$Proxy11.afterEvaluate(Unknown Source)
	at org.gradle.configuration.project.LifecycleProjectEvaluator.notifyAfterEvaluate(LifecycleProjectEvaluator.java:67)
	at org.gradle.configuration.project.LifecycleProjectEvaluator.evaluate(LifecycleProjectEvaluator.java:61)
	at org.gradle.api.internal.project.AbstractProject.evaluate(AbstractProject.java:487)
	at org.gradle.api.internal.project.AbstractProject.evaluate(AbstractProject.java:85)
	at org.gradle.execution.TaskPathProjectEvaluator.configureHierarchy(TaskPathProjectEvaluator.java:47)
	at org.gradle.configuration.DefaultBuildConfigurer.configure(DefaultBuildConfigurer.java:35)
	at org.gradle.initialization.DefaultGradleLauncher.doBuildStages(DefaultGradleLauncher.java:129)
	at org.gradle.initialization.DefaultGradleLauncher.doBuild(DefaultGradleLauncher.java:106)
	at org.gradle.initialization.DefaultGradleLauncher.run(DefaultGradleLauncher.java:86)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter$DefaultBuildController.run(InProcessBuildActionExecuter.java:90)
	at org.gradle.tooling.internal.provider.ExecuteBuildActionRunner.run(ExecuteBuildActionRunner.java:28)
	at org.gradle.launcher.exec.ChainingBuildActionRunner.run(ChainingBuildActionRunner.java:35)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:41)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:28)
	at org.gradle.launcher.exec.DaemonUsageSuggestingBuildActionExecuter.execute(DaemonUsageSuggestingBuildActionExecuter.java:50)
	at org.gradle.launcher.exec.DaemonUsageSuggestingBuildActionExecuter.execute(DaemonUsageSuggestingBuildActionExecuter.java:27)
	at org.gradle.launcher.cli.RunBuildAction.run(RunBuildAction.java:40)
	at org.gradle.internal.Actions$RunnableActionAdapter.execute(Actions.java:169)
	at org.gradle.launcher.cli.CommandLineActionFactory$ParseAndBuildAction.execute(CommandLineActionFactory.java:237)
	at org.gradle.launcher.cli.CommandLineActionFactory$ParseAndBuildAction.execute(CommandLineActionFactory.java:210)
	at org.gradle.launcher.cli.JavaRuntimeValidationAction.execute(JavaRuntimeValidationAction.java:35)
	at org.gradle.launcher.cli.JavaRuntimeValidationAction.execute(JavaRuntimeValidationAction.java:24)
	at org.gradle.launcher.cli.CommandLineActionFactory$WithLogging.execute(CommandLineActionFactory.java:206)
	at org.gradle.launcher.cli.CommandLineActionFactory$WithLogging.execute(CommandLineActionFactory.java:169)
	at org.gradle.launcher.cli.ExceptionReportingAction.execute(ExceptionReportingAction.java:33)
	at org.gradle.launcher.cli.ExceptionReportingAction.execute(ExceptionReportingAction.java:22)
	at org.gradle.launcher.Main.doAction(Main.java:33)
	at org.gradle.launcher.bootstrap.EntryPoint.run(EntryPoint.java:45)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.gradle.launcher.bootstrap.ProcessBootstrap.runNoExit(ProcessBootstrap.java:54)
	at org.gradle.launcher.bootstrap.ProcessBootstrap.run(ProcessBootstrap.java:35)
	at org.gradle.launcher.GradleMain.main(GradleMain.java:23)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.gradle.wrapper.BootstrapMainStarter.start(BootstrapMainStarter.java:30)
	at org.gradle.wrapper.WrapperExecutor.execute(WrapperExecutor.java:127)
	at org.gradle.wrapper.GradleWrapperMain.main(GradleWrapperMain.java:61)

FAILURE: Build failed with an exception.

* Where:
Build file '/home/michael/react/AwesomeProject/android/app/build.gradle' line: 110

* What went wrong:
A problem occurred evaluating project ':app'.
> SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

BUILD FAILED

Total time: 4.303 secs
Could not install the app on the device, read the error above for details.
Make sure you have an Android emulator running or a device connected and have
set up your Android development environment:
https://facebook.github.io/react-native/docs/android-setup.html
```

Solution:

__JS server not recognized, continuing with build...__

This is because TCP port 8081 has been taken by other service(brooklyn in my case),
```
node_modules/react-native/local-cli/runAndroid/runAndroid.js:59:      console.warn(chalk.yellow(`JS server not recognized, continuing with build...`));
node_modules/react-native/local-cli/util/isPackagerRunning.js:23:  return fetch('http://localhost:8081/status').then(
```

    $ sudo lsof -i:8081
    $ systemctl status brooklyn
    $ sudo systemctl disable brooklyn
    $ sudo systemctl stop brooklyn


## react-native run-android

Problem:

```
michael@localhost:~/react/AwesomeProject $ react-native run-android
Starting JS server...
Running adb reverse tcp:8081 tcp:8081
error: no devices/emulators found
Could not run adb reverse: Command failed: adb reverse tcp:8081 tcp:8081
Building and installing the app on the device (cd android && ./gradlew installDebug...
Failed to notify ProjectEvaluationListener.afterEvaluate(), but primary configuration failure takes precedence.
java.lang.RuntimeException: SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable.
	at com.android.build.gradle.internal.SdkHandler.getAndCheckSdkFolder(SdkHandler.java:102)
	at com.android.build.gradle.internal.SdkHandler.getSdkLoader(SdkHandler.java:112)
	at com.android.build.gradle.internal.SdkHandler.initTarget(SdkHandler.java:86)
	at com.android.build.gradle.BasePlugin.ensureTargetSetup(BasePlugin.groovy:507)
	at com.android.build.gradle.BasePlugin.createAndroidTasks(BasePlugin.groovy:455)
	at com.android.build.gradle.BasePlugin$_createTasks_closure13_closure17.doCall(BasePlugin.groovy:415)
	at com.android.build.gradle.BasePlugin$_createTasks_closure13_closure17.doCall(BasePlugin.groovy)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:90)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:324)
	at org.codehaus.groovy.runtime.metaclass.ClosureMetaClass.invokeMethod(ClosureMetaClass.java:292)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1015)
	at org.codehaus.groovy.runtime.callsite.PogoMetaClassSite.call(PogoMetaClassSite.java:39)
	at org.codehaus.groovy.runtime.callsite.CallSiteArray.defaultCall(CallSiteArray.java:45)
	at org.codehaus.groovy.runtime.callsite.PogoMetaClassSite.call(PogoMetaClassSite.java:54)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:112)
	at com.android.build.gradle.internal.profile.SpanRecorders$2.call(SpanRecorders.groovy:52)
	at com.android.builder.profile.ThreadRecorder$1.record(ThreadRecorder.java:48)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.codehaus.groovy.runtime.callsite.PojoMetaMethodSite$PojoCachedMethodSite.invoke(PojoMetaMethodSite.java:189)
	at org.codehaus.groovy.runtime.callsite.PojoMetaMethodSite.call(PojoMetaMethodSite.java:53)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:124)
	at com.android.build.gradle.internal.profile.SpanRecorders.record(SpanRecorders.groovy:54)
	at com.android.build.gradle.BasePlugin$_createTasks_closure13.doCall(BasePlugin.groovy:414)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:90)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:324)
	at org.codehaus.groovy.runtime.metaclass.ClosureMetaClass.invokeMethod(ClosureMetaClass.java:292)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1015)
	at groovy.lang.Closure.call(Closure.java:423)
	at org.gradle.listener.ClosureBackedMethodInvocationDispatch.dispatch(ClosureBackedMethodInvocationDispatch.java:40)
	at org.gradle.listener.ClosureBackedMethodInvocationDispatch.dispatch(ClosureBackedMethodInvocationDispatch.java:25)
	at org.gradle.internal.event.BroadcastDispatch.dispatch(BroadcastDispatch.java:87)
	at org.gradle.internal.event.BroadcastDispatch.dispatch(BroadcastDispatch.java:31)
	at org.gradle.messaging.dispatch.ProxyDispatchAdapter$DispatchingInvocationHandler.invoke(ProxyDispatchAdapter.java:93)
	at com.sun.proxy.$Proxy12.afterEvaluate(Unknown Source)
	at org.gradle.configuration.project.LifecycleProjectEvaluator.notifyAfterEvaluate(LifecycleProjectEvaluator.java:67)
	at org.gradle.configuration.project.LifecycleProjectEvaluator.evaluate(LifecycleProjectEvaluator.java:61)
	at org.gradle.api.internal.project.AbstractProject.evaluate(AbstractProject.java:487)
	at org.gradle.api.internal.project.AbstractProject.evaluate(AbstractProject.java:85)
	at org.gradle.execution.TaskPathProjectEvaluator.configureHierarchy(TaskPathProjectEvaluator.java:47)
	at org.gradle.configuration.DefaultBuildConfigurer.configure(DefaultBuildConfigurer.java:35)
	at org.gradle.initialization.DefaultGradleLauncher.doBuildStages(DefaultGradleLauncher.java:129)
	at org.gradle.initialization.DefaultGradleLauncher.doBuild(DefaultGradleLauncher.java:106)
	at org.gradle.initialization.DefaultGradleLauncher.run(DefaultGradleLauncher.java:86)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter$DefaultBuildController.run(InProcessBuildActionExecuter.java:90)
	at org.gradle.tooling.internal.provider.ExecuteBuildActionRunner.run(ExecuteBuildActionRunner.java:28)
	at org.gradle.launcher.exec.ChainingBuildActionRunner.run(ChainingBuildActionRunner.java:35)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:41)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:28)
	at org.gradle.launcher.exec.DaemonUsageSuggestingBuildActionExecuter.execute(DaemonUsageSuggestingBuildActionExecuter.java:50)
	at org.gradle.launcher.exec.DaemonUsageSuggestingBuildActionExecuter.execute(DaemonUsageSuggestingBuildActionExecuter.java:27)
	at org.gradle.launcher.cli.RunBuildAction.run(RunBuildAction.java:40)
	at org.gradle.internal.Actions$RunnableActionAdapter.execute(Actions.java:169)
	at org.gradle.launcher.cli.CommandLineActionFactory$ParseAndBuildAction.execute(CommandLineActionFactory.java:237)
	at org.gradle.launcher.cli.CommandLineActionFactory$ParseAndBuildAction.execute(CommandLineActionFactory.java:210)
	at org.gradle.launcher.cli.JavaRuntimeValidationAction.execute(JavaRuntimeValidationAction.java:35)
	at org.gradle.launcher.cli.JavaRuntimeValidationAction.execute(JavaRuntimeValidationAction.java:24)
	at org.gradle.launcher.cli.CommandLineActionFactory$WithLogging.execute(CommandLineActionFactory.java:206)
	at org.gradle.launcher.cli.CommandLineActionFactory$WithLogging.execute(CommandLineActionFactory.java:169)
	at org.gradle.launcher.cli.ExceptionReportingAction.execute(ExceptionReportingAction.java:33)
	at org.gradle.launcher.cli.ExceptionReportingAction.execute(ExceptionReportingAction.java:22)
	at org.gradle.launcher.Main.doAction(Main.java:33)
	at org.gradle.launcher.bootstrap.EntryPoint.run(EntryPoint.java:45)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.gradle.launcher.bootstrap.ProcessBootstrap.runNoExit(ProcessBootstrap.java:54)
	at org.gradle.launcher.bootstrap.ProcessBootstrap.run(ProcessBootstrap.java:35)
	at org.gradle.launcher.GradleMain.main(GradleMain.java:23)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.gradle.wrapper.BootstrapMainStarter.start(BootstrapMainStarter.java:30)
	at org.gradle.wrapper.WrapperExecutor.execute(WrapperExecutor.java:127)
	at org.gradle.wrapper.GradleWrapperMain.main(GradleWrapperMain.java:61)

FAILURE: Build failed with an exception.

* Where:
Build file '/home/michael/react/AwesomeProject/android/app/build.gradle' line: 110

* What went wrong:
A problem occurred evaluating project ':app'.
> SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

BUILD FAILED

Total time: 3.332 secs
Could not install the app on the device, read the error above for details.
Make sure you have an Android emulator running or a device connected and have
set up your Android development environment:
https://facebook.github.io/react-native/docs/android-setup.html

```

Solution:

__error: no devices/emulators found__

This is because emulator has not been launched yet:

    $ emulator -list-avds
    $ emulator -avd Nexus_5X_API_24


## react-native run-android

Problem:

```
michael@localhost:~/react/AwesomeProject $ react-native run-android
Starting JS server...
Running adb reverse tcp:8081 tcp:8081
Building and installing the app on the device (cd android && ./gradlew installDebug...
Failed to notify ProjectEvaluationListener.afterEvaluate(), but primary configuration failure takes precedence.
java.lang.RuntimeException: SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable.
	at com.android.build.gradle.internal.SdkHandler.getAndCheckSdkFolder(SdkHandler.java:102)
	at com.android.build.gradle.internal.SdkHandler.getSdkLoader(SdkHandler.java:112)
	at com.android.build.gradle.internal.SdkHandler.initTarget(SdkHandler.java:86)
	at com.android.build.gradle.BasePlugin.ensureTargetSetup(BasePlugin.groovy:507)
	at com.android.build.gradle.BasePlugin.createAndroidTasks(BasePlugin.groovy:455)
	at com.android.build.gradle.BasePlugin$_createTasks_closure13_closure17.doCall(BasePlugin.groovy:415)
	at com.android.build.gradle.BasePlugin$_createTasks_closure13_closure17.doCall(BasePlugin.groovy)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:90)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:324)
	at org.codehaus.groovy.runtime.metaclass.ClosureMetaClass.invokeMethod(ClosureMetaClass.java:292)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1015)
	at org.codehaus.groovy.runtime.callsite.PogoMetaClassSite.call(PogoMetaClassSite.java:39)
	at org.codehaus.groovy.runtime.callsite.CallSiteArray.defaultCall(CallSiteArray.java:45)
	at org.codehaus.groovy.runtime.callsite.PogoMetaClassSite.call(PogoMetaClassSite.java:54)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:112)
	at com.android.build.gradle.internal.profile.SpanRecorders$2.call(SpanRecorders.groovy:52)
	at com.android.builder.profile.ThreadRecorder$1.record(ThreadRecorder.java:48)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.codehaus.groovy.runtime.callsite.PojoMetaMethodSite$PojoCachedMethodSite.invoke(PojoMetaMethodSite.java:189)
	at org.codehaus.groovy.runtime.callsite.PojoMetaMethodSite.call(PojoMetaMethodSite.java:53)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:124)
	at com.android.build.gradle.internal.profile.SpanRecorders.record(SpanRecorders.groovy:54)
	at com.android.build.gradle.BasePlugin$_createTasks_closure13.doCall(BasePlugin.groovy:414)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:90)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:324)
	at org.codehaus.groovy.runtime.metaclass.ClosureMetaClass.invokeMethod(ClosureMetaClass.java:292)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:1015)
	at groovy.lang.Closure.call(Closure.java:423)
	at org.gradle.listener.ClosureBackedMethodInvocationDispatch.dispatch(ClosureBackedMethodInvocationDispatch.java:40)
	at org.gradle.listener.ClosureBackedMethodInvocationDispatch.dispatch(ClosureBackedMethodInvocationDispatch.java:25)
	at org.gradle.internal.event.BroadcastDispatch.dispatch(BroadcastDispatch.java:87)
	at org.gradle.internal.event.BroadcastDispatch.dispatch(BroadcastDispatch.java:31)
	at org.gradle.messaging.dispatch.ProxyDispatchAdapter$DispatchingInvocationHandler.invoke(ProxyDispatchAdapter.java:93)
	at com.sun.proxy.$Proxy12.afterEvaluate(Unknown Source)
	at org.gradle.configuration.project.LifecycleProjectEvaluator.notifyAfterEvaluate(LifecycleProjectEvaluator.java:67)
	at org.gradle.configuration.project.LifecycleProjectEvaluator.evaluate(LifecycleProjectEvaluator.java:61)
	at org.gradle.api.internal.project.AbstractProject.evaluate(AbstractProject.java:487)
	at org.gradle.api.internal.project.AbstractProject.evaluate(AbstractProject.java:85)
	at org.gradle.execution.TaskPathProjectEvaluator.configureHierarchy(TaskPathProjectEvaluator.java:47)
	at org.gradle.configuration.DefaultBuildConfigurer.configure(DefaultBuildConfigurer.java:35)
	at org.gradle.initialization.DefaultGradleLauncher.doBuildStages(DefaultGradleLauncher.java:129)
	at org.gradle.initialization.DefaultGradleLauncher.doBuild(DefaultGradleLauncher.java:106)
	at org.gradle.initialization.DefaultGradleLauncher.run(DefaultGradleLauncher.java:86)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter$DefaultBuildController.run(InProcessBuildActionExecuter.java:90)
	at org.gradle.tooling.internal.provider.ExecuteBuildActionRunner.run(ExecuteBuildActionRunner.java:28)
	at org.gradle.launcher.exec.ChainingBuildActionRunner.run(ChainingBuildActionRunner.java:35)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:41)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:28)
	at org.gradle.launcher.exec.DaemonUsageSuggestingBuildActionExecuter.execute(DaemonUsageSuggestingBuildActionExecuter.java:50)
	at org.gradle.launcher.exec.DaemonUsageSuggestingBuildActionExecuter.execute(DaemonUsageSuggestingBuildActionExecuter.java:27)
	at org.gradle.launcher.cli.RunBuildAction.run(RunBuildAction.java:40)
	at org.gradle.internal.Actions$RunnableActionAdapter.execute(Actions.java:169)
	at org.gradle.launcher.cli.CommandLineActionFactory$ParseAndBuildAction.execute(CommandLineActionFactory.java:237)
	at org.gradle.launcher.cli.CommandLineActionFactory$ParseAndBuildAction.execute(CommandLineActionFactory.java:210)
	at org.gradle.launcher.cli.JavaRuntimeValidationAction.execute(JavaRuntimeValidationAction.java:35)
	at org.gradle.launcher.cli.JavaRuntimeValidationAction.execute(JavaRuntimeValidationAction.java:24)
	at org.gradle.launcher.cli.CommandLineActionFactory$WithLogging.execute(CommandLineActionFactory.java:206)
	at org.gradle.launcher.cli.CommandLineActionFactory$WithLogging.execute(CommandLineActionFactory.java:169)
	at org.gradle.launcher.cli.ExceptionReportingAction.execute(ExceptionReportingAction.java:33)
	at org.gradle.launcher.cli.ExceptionReportingAction.execute(ExceptionReportingAction.java:22)
	at org.gradle.launcher.Main.doAction(Main.java:33)
	at org.gradle.launcher.bootstrap.EntryPoint.run(EntryPoint.java:45)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.gradle.launcher.bootstrap.ProcessBootstrap.runNoExit(ProcessBootstrap.java:54)
	at org.gradle.launcher.bootstrap.ProcessBootstrap.run(ProcessBootstrap.java:35)
	at org.gradle.launcher.GradleMain.main(GradleMain.java:23)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.gradle.wrapper.BootstrapMainStarter.start(BootstrapMainStarter.java:30)
	at org.gradle.wrapper.WrapperExecutor.execute(WrapperExecutor.java:127)
	at org.gradle.wrapper.GradleWrapperMain.main(GradleWrapperMain.java:61)

FAILURE: Build failed with an exception.

* Where:
Build file '/home/michael/react/AwesomeProject/android/app/build.gradle' line: 110

* What went wrong:
A problem occurred evaluating project ':app'.
> SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

BUILD FAILED

Total time: 3.915 secs
Could not install the app on the device, read the error above for details.
Make sure you have an Android emulator running or a device connected and have
set up your Android development environment:
https://facebook.github.io/react-native/docs/android-setup.html
```

Solution:

__SDK location not found__

This is because sdk.dir or ANDROID_HOME not set:

    $ echo 'sdk.dir=~/Android/Sdk' >> android/local.properties

or

    $ echo 'export ANDROID_HOME=~/Android/Sdk' >> ~/.bashrc
    $ source ~/.bashrc


## react-native run-android

Problem:

```
michael@localhost:~/react/AwesomeProject $ react-native run-android
JS server already running.
Running adb reverse tcp:8081 tcp:8081
Building and installing the app on the device (cd android && ./gradlew installDebug...
:app:preBuild UP-TO-DATE
:app:preDebugBuild UP-TO-DATE
:app:checkDebugManifest
:app:preReleaseBuild UP-TO-DATE
:app:prepareComAndroidSupportAppcompatV72301Library UP-TO-DATE
:app:prepareComAndroidSupportRecyclerviewV72301Library UP-TO-DATE
:app:prepareComAndroidSupportSupportV42321Library UP-TO-DATE
:app:prepareComFacebookFrescoDrawee0110Library UP-TO-DATE
:app:prepareComFacebookFrescoFbcore0110Library UP-TO-DATE
:app:prepareComFacebookFrescoFresco0110Library UP-TO-DATE
:app:prepareComFacebookFrescoImagepipeline0110Library UP-TO-DATE
:app:prepareComFacebookFrescoImagepipelineBase0110Library UP-TO-DATE
:app:prepareComFacebookFrescoImagepipelineOkhttp30110Library UP-TO-DATE
:app:prepareComFacebookReactReactNative0300Library UP-TO-DATE
:app:prepareOrgWebkitAndroidJscR174650Library UP-TO-DATE
:app:prepareDebugDependencies
:app:compileDebugAidl UP-TO-DATE
:app:compileDebugRenderscript UP-TO-DATE
:app:generateDebugBuildConfig UP-TO-DATE
:app:generateDebugAssets UP-TO-DATE
:app:mergeDebugAssets UP-TO-DATE
:app:generateDebugResValues UP-TO-DATE
:app:generateDebugResources UP-TO-DATE
:app:mergeDebugResources UP-TO-DATE
:app:bundleDebugJsAndAssets SKIPPED
:app:processDebugManifest UP-TO-DATE
:app:processDebugResources UP-TO-DATE
:app:generateDebugSources UP-TO-DATE
:app:processDebugJavaRes UP-TO-DATE
:app:compileDebugJavaWithJavac UP-TO-DATE
:app:compileDebugNdk UP-TO-DATE
:app:compileDebugSources UP-TO-DATE
:app:preDexDebug UP-TO-DATE
:app:dexDebug UP-TO-DATE
:app:validateDebugSigning
:app:packageDebug UP-TO-DATE
:app:zipalignDebug UP-TO-DATE
:app:assembleDebug UP-TO-DATE
:app:installDebug
Installing APK 'app-debug.apk' on 'emulator-5554 - 5.1.1'
Installed on 1 device.

BUILD SUCCESSFUL

Total time: 8.638 secs

This build could be faster, please consider using the Gradle Daemon: http://gradle.org/docs/2.4/userguide/gradle_daemon.html
Starting the app on emulator-5554 (adb -s emulator-5554 shell am start -n com.awesomeproject/.MainActivity)...
Starting: Intent { cmp=com.awesomeproject/.MainActivity }
```

Emulator,

```
Could not connect to development server

Try the following to fix the issue:
* Ensure that the package server is running
* Ensure that your device/emulator is connected to your machine and has USB debugging enabled - run `adb devices` to see a list of connected devices
* If you're on a physical device connected to the same machine, run 'adb reverse tpc:8081 tcp:8081' to forward requests from your device
* If your device is on the same Wi-Fi network, set 'Debug server host & port for device' in 'Dev settings' to your machine's IP address and the port of the local dev server - e.g. 10.0.1.1:8081

URL: http://10.0.2.2:8081/index.android.bundle?platform=android&dev=true&hot=false&minify=false
```

Solution:

__JS server already running__

__Could not connect to development server__

    $ sudo lsof -i:8081
    $ curl http://localhost:8081/status
    $ kill node-process-taking-8081


## react-native run-android

```
michael@localhost:~/react/AwesomeProject $ react-native run-android
Starting JS server...
Running adb reverse tcp:8081 tcp:8081
Building and installing the app on the device (cd android && ./gradlew installDebug...
:app:preBuild UP-TO-DATE
:app:preDebugBuild UP-TO-DATE
:app:checkDebugManifest
:app:preReleaseBuild UP-TO-DATE
:app:prepareComAndroidSupportAppcompatV72301Library UP-TO-DATE
:app:prepareComAndroidSupportRecyclerviewV72301Library UP-TO-DATE
:app:prepareComAndroidSupportSupportV42321Library UP-TO-DATE
:app:prepareComFacebookFrescoDrawee0110Library UP-TO-DATE
:app:prepareComFacebookFrescoFbcore0110Library UP-TO-DATE
:app:prepareComFacebookFrescoFresco0110Library UP-TO-DATE
:app:prepareComFacebookFrescoImagepipeline0110Library UP-TO-DATE
:app:prepareComFacebookFrescoImagepipelineBase0110Library UP-TO-DATE
:app:prepareComFacebookFrescoImagepipelineOkhttp30110Library UP-TO-DATE
:app:prepareComFacebookReactReactNative0300Library UP-TO-DATE
:app:prepareOrgWebkitAndroidJscR174650Library UP-TO-DATE
:app:prepareDebugDependencies
:app:compileDebugAidl UP-TO-DATE
:app:compileDebugRenderscript UP-TO-DATE
:app:generateDebugBuildConfig UP-TO-DATE
:app:generateDebugAssets UP-TO-DATE
:app:mergeDebugAssets UP-TO-DATE
:app:generateDebugResValues UP-TO-DATE
:app:generateDebugResources UP-TO-DATE
:app:mergeDebugResources UP-TO-DATE
:app:bundleDebugJsAndAssets SKIPPED
:app:processDebugManifest UP-TO-DATE
:app:processDebugResources UP-TO-DATE
:app:generateDebugSources UP-TO-DATE
:app:processDebugJavaRes UP-TO-DATE
:app:compileDebugJavaWithJavac UP-TO-DATE
:app:compileDebugNdk UP-TO-DATE
:app:compileDebugSources UP-TO-DATE
:app:preDexDebug UP-TO-DATE
:app:dexDebug UP-TO-DATE
:app:validateDebugSigning
:app:packageDebug UP-TO-DATE
:app:zipalignDebug UP-TO-DATE
:app:assembleDebug UP-TO-DATE
:app:installDebug
Installing APK 'app-debug.apk' on 'emulator-5554 - 5.1.1'
Installed on 1 device.

BUILD SUCCESSFUL

Total time: 10.552 secs

This build could be faster, please consider using the Gradle Daemon: http://gradle.org/docs/2.4/userguide/gradle_daemon.html
Starting the app on emulator-5554 (adb -s emulator-5554 shell am start -n com.awesomeproject/.MainActivity)...
Starting: Intent { cmp=com.awesomeproject/.MainActivity }
```


