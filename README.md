# ResMonitor
[![license](http://img.shields.io/badge/license-BSD3-brightgreen.svg?style=flat)](https://github.com/emile2013/ResMonitor/tree/master/LICENSE)
[![Release Version](https://jitpack.io/v/emile2013/ResMonitor.svg)](https://jitpack.io/#emile2013/ResMonitor)

A repository for android application  module to check classes in layout xml file if exist.

## Getting Started 

> Edit root project build.gradle file, append res-monitor plugin in  `buildscript`  classpath ，and do not forget add maven { url 'https://jitpack.io' } too.

```groovy
buildscript {
    ext.resmonitor_version='0.1.0'
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

>  App module build.gradle file  add res-monitor dependency

```groovy
apply plugin: 'com.android.application'
apply plugin: 'com.github.emile2013.res-monitor' // add this line
```

> Run task

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
 
> 此项目原理是拿到layout和manifest xml导出的混淆文件,再通过javassist检测类是否存在。所以依赖的项目要开启混淆配置(minifyEnabled=true)

> This program uses aapt_rule.txt and javassist to handle functions, so must set minifyEnabled=true in build.gradle file.

> 应用场景例如用于Migrate to AndroidX,无论AS自带功能或自写脚本方式均有可能对layout xml存在错误修改，本项目可以对此类问题进行检测。

## Plan
 
> 考虑到library相对功能不多，可人工或在集成到app时作较验，本项目暂时不支持library项目。

> This program do not support library module, while support later.



## License

ResMonitor is licensed under the [BSD 3-Clause License](./LICENSE).
