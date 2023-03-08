---
title: Traditional android
weight: 1
---

See [github repo](https://github.com/ApolloKwok/TracerAndroidTraditional) if you need.

## Setup
```groovy
    libraryVariants.all {
        def variantName = name
        sourceSets {
            getByName("main") {
                java.srcDir(file("$buildDir/generated/ksp/$variantName/kotlin"))
            }
        }
    }
```

如果上述方式遭遇小几率失败，需要换成以下方式，如果有其他 buildDir 则手动指定 
```groovy
kotlin {
    sourceSets.debug.kotlin.srcDirs += 'build/generated/ksp/debug/kotlin'
    sourceSets.release.kotlin.srcDirs += 'build/generated/ksp/release/kotlin'
}
```