###Android内存泄漏分析实战

####常见android内存泄漏
>case 1. 单例造成的内存泄露

单例的静态特性导致其生命周期同应用一样长。  
解决方案：
* 将该属性的引用方式改为弱引用;
* 如果传入Context，使用ApplicationContext;

泄漏代码片段
````
private static ScrollHelper mInstance;    
private ScrollHelper() {
}    
public static ScrollHelper getInstance() {        
    if (mInstance == null) {           
       synchronized (ScrollHelper.class) {                
            if (mInstance == null) {
                mInstance = new ScrollHelper();
            }
        }
    }        

    return mInstance;
}    
/**
 * 被点击的view
 */
private View mScrolledView = null;    
public void setScrolledView(View scrolledView) {
    mScrolledView = scrolledView;
}

````
Solution：使用WeakReference
````
private static ScrollHelper mInstance;    
private ScrollHelper() {
}    
public static ScrollHelper getInstance() {        
    if (mInstance == null) {            
        synchronized (ScrollHelper.class) {                
            if (mInstance == null) {
                mInstance = new ScrollHelper();
            }
        }
    }        

    return mInstance;
}    
/**
 * 被点击的view
 */
private WeakReference<View> mScrolledViewWeakRef = null;    
public void setScrolledView(View scrolledView) {
    mScrolledViewWeakRef = new WeakReference<View>(scrolledView);
}
````

>case 2.InnerClass匿名内部类

在Java中，非静态内部类 和 匿名类 都会潜在的引用它们所属的外部类，但是，静态内部类却不会。如果这个非静态内部类实例做了一些耗时的操作，就会造成外围对象不会被回收，从而导致内存泄漏。

解决方案：

* 将内部类变成静态内部类。
* 如果有强引用Activity中的属性，则将该属性的引用方式改为弱引用。
* 在业务允许的情况下，当Activity执行onDestory时，结束这些耗时任务。

example：
````
public class LeakAct extends Activity {  
    @Override
    protected void onCreate(Bundle savedInstanceState) {    
        super.onCreate(savedInstanceState);
        setContentView(R.layout.aty_leak);
        test();
    }
    // 这儿发生泄漏    
    public void test() {    
        new Thread(new Runnable() {      
            @Override
            public void run() {        
                while (true) {          
                    try {
                        Thread.sleep(1000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }).start();
    }
}
````

Solution：
````
public class LeakAct extends Activity {  
    @Override
    protected void onCreate(Bundle savedInstanceState) {    
        super.onCreate(savedInstanceState);
        setContentView(R.layout.aty_leak);
        test();
    }  
    // 加上static，变成静态匿名内部类
    public static void test() {    
        new Thread(new Runnable() {     
            @Override
            public void run() {        
                while (true) {          
                    try {
                        Thread.sleep(1000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }).start();
    }
}
````

>case 3. Activity Context 的不正确使用
>case 4. Handler引起的内存泄漏
>case 5. 注册监听器的泄漏
>case 6. 资源未关闭造成的内存泄漏
对于使用了BraodcastReceiver，ContentObserver，File，游标 Cursor，Stream，Bitmap等资源的使用，应该在Activity销毁时及时关闭或者注销，否则这些资源将不会被回收，造成内存泄漏。
>case 7. 集合中对象没清理造成的内存泄漏
>case 8. WebView造成的泄露
>case 9. 构造Adapter时，没有使用缓存的ConvertView
>case 10. 对象没有反注册




````
在Handler中使用postDelayed需要额外的注意，为了解决问题，我们有三种方法
使用静态内部Handler/Runnable + 弱引用
在onDestory的时候，手动清除Message
使用Badoo开发的第三方的 WeakHandler
````
