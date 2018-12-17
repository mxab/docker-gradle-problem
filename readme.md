# Dockerfile not created if depended on


This creates a Dockerfile
```
./gradlew clean dockerCreateDockerfile
```

The task `dockerBuildImage` depends on `dockerCreateDockerfile`.

If this `dockerCreateDockerfile` is executed it fails because there is no Dockerfile

```
./gradlew clean dockerBuildImage --console=plain

 Task :clean
> Task :compileJava
> Task :processResources NO-SOURCE
> Task :classes
> Task :jar
> Task :dockerCreateDockerfile
> Task :dockerSyncArchive

> Task :dockerBuildImage FAILED
Building image using context '/Users/bruchmann/temp/docker-gradle-demo/build/docker'.

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':dockerBuildImage'.
> Dockerfile does not exist

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

Deprecated Gradle features were used in this build, making it incompatible with Gradle 6.0.
Use '--warning-mode all' to show the individual deprecation warnings.
See https://docs.gradle.org/5.0/userguide/command_line_interface.html#sec:command_line_warnings

BUILD FAILED in 0s
6 actionable tasks: 6 executed
```