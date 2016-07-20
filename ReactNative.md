# ReactNative


## SDK location not found

Problem:

D:\Users\Michael\react\AwesomeProject>react-native run-android
JS server already running.
Building and installing the app on the device (cd android && gradlew.bat installDebug...
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
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
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
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at org.codehaus.groovy.runtime.callsite.PojoMetaMethodSite$PojoCachedMethodSite.invoke(PojoMetaMethodSite.java:189)
        at org.codehaus.groovy.runtime.callsite.PojoMetaMethodSite.call(PojoMetaMethodSite.java:53)
        at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:124)
        at com.android.build.gradle.internal.profile.SpanRecorders.record(SpanRecorders.groovy:54)
        at com.android.build.gradle.BasePlugin$_createTasks_closure13.doCall(BasePlugin.groovy:414)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
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
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at org.gradle.launcher.bootstrap.ProcessBootstrap.runNoExit(ProcessBootstrap.java:54)
        at org.gradle.launcher.bootstrap.ProcessBootstrap.run(ProcessBootstrap.java:35)
        at org.gradle.launcher.GradleMain.main(GradleMain.java:23)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at org.gradle.wrapper.BootstrapMainStarter.start(BootstrapMainStarter.java:30)
        at org.gradle.wrapper.WrapperExecutor.execute(WrapperExecutor.java:127)
        at org.gradle.wrapper.GradleWrapperMain.main(GradleWrapperMain.java:61)

FAILURE: Build failed with an exception.

* Where:
Build file 'D:\Users\Michael\react\AwesomeProject\android\app\build.gradle' line: 110

* What went wrong:
A problem occurred evaluating project ':app'.
> SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

BUILD FAILED

Total time: 19.279 secs
Could not install the app on the device, read the error above for details.
Make sure you have an Android emulator running or a device connected and have
set up your Android development environment:
https://facebook.github.io/react-native/docs/android-setup.html


Solvtion:

Add file AwesomeProject\android\local.properties with content:
sdk.dir=D:\\Users\\Michael\\AppData\\Local\\Android\\sdk

or 

export ANDROID_HOME=D:\Users\Michael\AppData\Local\Android\sdk


## No connected devices

D:\Users\Michael\react\AwesomeProject>react-native run-android
JS server already running.
Building and installing the app on the device (cd android && gradlew.bat installDebug...
Download https://jcenter.bintray.com/com/fasterxml/jackson/core/jackson-core/2.2.3/jackson-core-2.2.3.jar
Download https://jcenter.bintray.com/com/facebook/fresco/drawee/0.11.0/drawee-0.11.0.aar
Download https://jcenter.bintray.com/com/facebook/fresco/fresco/0.11.0/fresco-0.11.0.aar
Download https://jcenter.bintray.com/com/squareup/okhttp3/okhttp-ws/3.2.0/okhttp-ws-3.2.0.jar
Download https://jcenter.bintray.com/com/squareup/okhttp3/okhttp-urlconnection/3.2.0/okhttp-urlconnection-3.2.0.jar
:app:preBuild UP-TO-DATE
:app:preDebugBuild UP-TO-DATE
:app:checkDebugManifest
:app:preReleaseBuild UP-TO-DATE
:app:prepareComAndroidSupportAppcompatV72301Library
:app:prepareComAndroidSupportRecyclerviewV72301Library
:app:prepareComAndroidSupportSupportV42321Library
:app:prepareComFacebookFrescoDrawee0110Library
:app:prepareComFacebookFrescoFbcore0110Library
:app:prepareComFacebookFrescoFresco0110Library
:app:prepareComFacebookFrescoImagepipeline0110Library
:app:prepareComFacebookFrescoImagepipelineBase0110Library
:app:prepareComFacebookFrescoImagepipelineOkhttp30110Library
:app:prepareComFacebookReactReactNative0292Library
:app:prepareOrgWebkitAndroidJscR174650Library
:app:prepareDebugDependencies
:app:compileDebugAidl
:app:compileDebugRenderscript
:app:generateDebugBuildConfig
:app:generateDebugAssets UP-TO-DATE
:app:mergeDebugAssets
:app:generateDebugResValues
:app:generateDebugResources
:app:mergeDebugResources
:app:bundleDebugJsAndAssets SKIPPED
:app:processDebugManifest
:app:processDebugResources
:app:generateDebugSources
:app:processDebugJavaRes UP-TO-DATE
:app:compileDebugJavaWithJavac
:app:compileDebugNdk UP-TO-DATE
:app:compileDebugSources
:app:preDexDebug
:app:dexDebug
:app:validateDebugSigning
:app:packageDebug
:app:zipalignDebug
:app:assembleDebug
:app:installDebug FAILED

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:installDebug'.
> com.android.builder.testing.api.DeviceException: No connected devices!

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

BUILD FAILED

Total time: 1 mins 15.105 secs
Could not install the app on the device, read the error above for details.
Make sure you have an Android emulator running or a device connected and have
set up your Android development environment:
https://facebook.github.io/react-native/docs/android-setup.html


## emulator: WARNING: VM heap size set below hardware specified minimum of 228MB

Problem:

D:\Users\Michael\AppData\Local\Android\Sdk\tools\emulator.exe -netdelay none -netspeed full -avd Nexus_5X_API_23
emulator: WARNING: VM heap size set below hardware specified minimum of 228MB
emulator: WARNING: Setting VM heap size to 384MB
Hax is enabled
Hax ram_size 0x60000000
HAX is working and emulator runs in fast virt mode.
console on port 5554, ADB on port 5555


07/20 06:33:32: Launching app
$ adb push D:\Users\Michael\AndroidStudioProjects\EasyManager\app\build\outputs\apk\app-debug.apk /data/local/tmp/com.easymanager.easymanager
$ adb shell pm install -r "/data/local/tmp/com.easymanager.easymanager"
	pkg: /data/local/tmp/com.easymanager.easymanager
Success


$ adb shell am start -n "com.easymanager.easymanager/com.easymanager.easymanager.MainActivity" -a android.intent.action.MAIN -c android.intent.category.LAUNCHER
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]
Connected to process 2357 on device Nexus_5X_API_23 [emulator-5554]


Solvtion:

Set VM heap size 512MB

D:\Users\Michael\AppData\Local\Android\Sdk\tools\emulator.exe -netdelay none -netspeed full -avd Nexus_5X_API_23
Hax is enabled
Hax ram_size 0x60000000
HAX is working and emulator runs in fast virt mode.
console on port 5554, ADB on port 5555
emulator: emulator window was out of view and was recentered


## react-native run-android

D:\Users\Michael\react\AwesomeProject>react-native run-android
Starting JS server...
Building and installing the app on the device (cd android && gradlew.bat installDebug...
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
:app:prepareComFacebookReactReactNative0292Library UP-TO-DATE
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
Installing APK 'app-debug.apk' on 'emulator-5554 - 6.0'
Installed on 1 device.

BUILD SUCCESSFUL

Total time: 1 mins 16.883 secs
Starting the app on emulator-5554 (adb -s emulator-5554 shell am start -n com.awesomeproject/.MainActivity)...
Starting: Intent { cmp=com.awesomeproject/.MainActivity }


##


