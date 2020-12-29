# Gradle Help

## What?
It is a build tool.
- Follows conventions - assumptions of source files, resources, test sources location etc.
    - conventions are configurable.
- DSL based tool - Groovy / Kotlin based.
- Builds your code efficiently. Identifies only files changed and generates corresponding class files and jar files.

## How?
- Define task
- Use it through CLI / SDK
- Apply plugins - (plugin to gradle is what library to java) way to reuse group of existing tasks.

### Project
- has build file.
- build file defines the necessary tasks.


### Task:
#### Task lifecycle:
- initialization phase: 
- configuration phase
- Execution phase
    - Task methods:
      `doFirst` `doLast`
```kotlin
tasks.register("greeting") {
    doFirst {
        println("First.")
    }
    
    doLast {
        println("Last.")
    }
}
```
- Task Dependencies
```kotlin
tasks.register("dependent") {
    dependsOn("greeting")
    
    println("Without Method.")
}
```

### Plugins
Plugin is a collection of tasks and properties.
There are inbuilt plugins and community plugins. You need to specify a version for community plugins.
```kotlin
plugins { java }
```
```kotlin
plugins { 
    java
    id("org.flywaydb.flyway") version "6.3.2"
}
```
e.g.: plugin `application` has task `run` and property `mainClassName`.
```kotlin
plugins { 
    application
}

application {
    mainClassName = 'com.sample.MainClass'
}
```
- plugin can extend another plugin.
e.g. `application` plugin extends `java` plugin.
```kotlin
plugins {
    application
}

java {
    sourceCompatibility = JavaVersion.VERSION_11
    targetCompatibility = JavaVersion.VERSION_11
}
```

## Commands
- List tasks
```shell
./gradlew tasks
```  
- Check
```shell
./gradlew check
```
- Clean Build
```shell
./gradlew clean build
```
- Run
```shell
./gradlew run -q
```
- Wrapper
```shell
gradle wrapper
```
