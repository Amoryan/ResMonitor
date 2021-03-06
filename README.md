# ResMonitor
[![license](http://img.shields.io/badge/license-BSD3-brightgreen.svg?style=flat)](https://github.com/emile2013/ResMonitor/tree/master/LICENSE)
[![Release Version](https://jitpack.io/v/emile2013/ResMonitor.svg)](https://jitpack.io/#emile2013/ResMonitor)

A repository for android application module to detect if layout file contain non-existent views.

[README 中文版](README.zh-CN.md)

## Getting Started 

#### 1. Add dependencies

> Add `ResMonitor` plugin in root build.gradle,and do not forget add maven { url 'https://jitpack.io' } too.

```groovy
buildscript {
    ext.resmonitor_version='0.1.1'
    repositories {
        maven { url 'https://jitpack.io' } //add this line
        google()
        mavenCentral()
        jcenter()
    }
    dependencies {
        classpath "com.github.emile2013:ResMonitor:$resmonitor_version" //add this line
    }
}

allprojects {
    repositories {
      maven { url 'https://jitpack.io' }  //add this line
      google()
      mavenCentral()
      jcenter()
    }
}
```

>  apply `com.github.emile2013.res-monitor` plugin in module build.gradle file

```groovy
apply plugin: 'com.android.application'
apply plugin: 'com.github.emile2013.res-monitor' // add this line
```

### 2. Run task

```
./gradlew checkReleaseRes

something output on  console like:

Execution failed for task ':app:checkReleaseRes'.
> java.lang.Exception: androidx.core.view.ViewPager not exist !! but declare at:
  # Referenced at /ResMonitor/sample/app/src/main/res/layout/content_main.xml:11

```

## Samples 
- [sample](https://github.com/emile2013/ResMonitor/tree/master/sample)

## Tips
 
> This program uses aapt_rule.txt and javassist to handle functions, so must set minifyEnabled=true in build.gradle file.

## License

ResMonitor is licensed under the [BSD 3-Clause License](./LICENSE).
