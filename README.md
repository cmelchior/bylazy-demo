# Kapt and Kotlin 1.3

This project demonstrates that Kapt and Kotlin 1.3 contains bugs not present in Kotlin 1.2.71.

To reproduce, run the following command

```
./gradlew clean assemble

```

This will result in the following error:

```
=> gw clean assemble
Using gradle at '/Users/cm/RealmCustomerProjects/bylazy-demo/gradlew' to run buildfile '/Users/cm/RealmCustomerProjects/bylazy-demo/build.gradle':

e: /Users/cm/RealmCustomerProjects/bylazy-demo/app/build/tmp/kapt3/stubs/debug/com/example/hardts/myapplication/Test.java:9: error: cannot find symbol
    private final com.example.hardts.myapplication.Test$foo$2$1 getFoo() {
                                                  ^
  symbol:   class Test$foo$2$1
  location: package com.example.hardts.myapplication
> Task :app:kaptDebugKotlin FAILED
```

This will compile fine if the Kotlin version is downgraded to Kotlin 1.2.71

The offending code seems to be [here](https://github.com/cmelchior/bylazy-demo/blob/master/app/src/main/java/com/example/hardts/myapplication/Bar.kt#L9), but it is unclear why it is failing.
