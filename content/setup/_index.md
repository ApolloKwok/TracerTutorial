---
title: Setup
draft: false
weight: 2
---

Configure your `build.gradle` as below.

## Add the ksp plugin
```groovy
plugins{
    // Assuming your kotlin version is `1.7.21`, here uses the latest ksp plugin version beginning 
    // with `1.7.21` ('1.7.21-1.0.8').  
    id 'com.google.devtools.ksp' version '1.7.21-1.0.8'
}
```
  
&nbsp;
## Add source sets
Skip this step if your ksp plugin version is '1.8.0-1.0.9' or higher.  
This part is different if you are using IntelliJ IDEA and KSP in a Gradle plugin. 
(See [ksp quickstart](https://kotlinlang.org/docs/ksp-quickstart.html#make-ide-aware-of-generated-code))
```groovy
// Omissible if your ksp plugin version is '1.8.0-1.0.9' or higher. 
kotlin.sourceSets {
    main.kotlin.srcDirs += "$buildDir/generated/ksp/main/kotlin"
    test.kotlin.srcDirs += "$buildDir/generated/ksp/test/kotlin"
}
```

&nbsp;
## Configure tracer
Add this part directly, rather than insert messily.
```groovy
//region tracer
// options
ksp{
//    arg("tracer.allInternal", "")
//    arg("tracer.propertiesFullName", "")
}

tasks.withType(org.jetbrains.kotlin.gradle.tasks.KotlinCompile).configureEach {
    kotlinOptions.freeCompilerArgs += '-Xcontext-receivers'
}

dependencies {
    // Keep this version latest with the prefix lower than your kotlin version(inclusive). 
    ksp 'io.github.apollokwok:tracer-common-compiler:1.7.20-1.1.0'
    // Keep this version latest but lower than the version above(inclusive). 
    implementation 'io.github.apollokwok:tracer-common-annotations:1.7.20-1.1.0'
}
//endregion 
```