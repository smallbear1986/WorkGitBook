### LeakCanary
>注意: 集成到低版本应用, 会报出Bug.
Error:(2) Error retrieving parent for item: No resource found that matches the given name 'android:Theme.Material'.
修改编译版本: compileSdkVersion 21 即可.


#### 接入  
In your build.gradle:
````
 dependencies {
   debugCompile 'com.squareup.leakcanary:leakcanary-android:1.5'
   releaseCompile 'com.squareup.leakcanary:leakcanary-android-no-op:1.5'
   testCompile 'com.squareup.leakcanary:leakcanary-android-no-op:1.5'
 }
 ````
In your Application class:
````
public class ExampleApplication extends Application {

  @Override public void onCreate() {
    super.onCreate();
    if (LeakCanary.isInAnalyzerProcess(this)) {
      // This process is dedicated to LeakCanary for heap analysis.
      // You should not init your app in this process.
      return;
    }
    LeakCanary.install(this);
    // Normal app init code...
  }
}
````
